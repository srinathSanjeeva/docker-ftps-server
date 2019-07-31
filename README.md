In your docker-compose.yml :

ftps_server:
  image: mikatux/ftps-server
  volumes:
    - ./data:/home/username
  environment:
    USER: username
  ports:
    - "4567:21"
    - "3000-3010:3000-3010"
or: docker run -d -v $(pwd)/data:/home/username -e USER=username -p 4567:21 -p 3000-3010:3000-3010 mikatux/ftps-server

The password is automatically generated see your docker logs or use PASSWORD env variable: docker logs {your_container_id}

docker run -d -v $(pwd)/data:/home/username -e USER=username -e PASSWORD=password -p 4567:21 -p 3000-3010:3000-3010 mikatux/ftps-server
