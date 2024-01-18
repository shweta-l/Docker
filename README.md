Dockerfile 
- It must starts with a Dockerfile.

File content:

FROM <image>	      - Defines a base for your image.
RUN <command>	      - Executes any commands in a new layer on top of the current image and commits the result. RUN also has a shell form for running commands.
WORKDIR <directory>	- Sets the working directory for any RUN, CMD, ENTRYPOINT, COPY, and ADD instructions that follow it in the Dockerfile.
COPY <src> <dest>	  - Copies new files or directories from <src> and adds them to the filesystem of the container at the path <dest>.
CMD <command>	      - Lets you define the default program that is run once you start the container based on this image. Each Dockerfile only has one CMD, and only the last CMD instance is respected when multiple exist.

Example - Dockerfile

FROM python:3.8-alpine
COPY . /app
WORKDIR /app
RUN pip install -r requirements.txt
CMD python app.py

**Build Docker**

docker build -t shweta51193/welcome-app:latest .

docker run -p 127.0.0.1:8000:8000 shweta51193/welcome-app:latest

**Get docker images**
docker images

**Get Container details**
docker ps

**Docker compose**
create compose file with name - compose.yml 

compose.yml
services:
  web:
    build: .
    ports:
      - "8000:5000"
  redis:
    image: "redis:alpine"

**Build and run your app with Compose**
docker compose up

