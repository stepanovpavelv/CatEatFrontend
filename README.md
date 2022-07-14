# CatEatFrontend
Application for visual monitoring of previously entered indications.

## Deploy to Github Pages
Main information is on official page: <a>https://angular.io/guide/deployment#deploy-to-github-pages</a>

## Deploy to Docker
1. First you have to create Dockerfile with some instructions;
    * setup current directory for app;
	* copy package.json & package-lock.json and install libraries;
	* copy other files;
	* build & run production;
	* copy nginx to default linux nginx path;
	* copy sources;
	* more details on: https://habr.com/ru/post/566210/
	
2. Then add .dockerignore
    * node_modules
	* dist
	
3. Create nginx.conf file
    * Note: if you want to send requests to remote API, then you may allow these actions with `location`-instruction as it has been done in this repository.
	* Note 2: it would be better if router paths won't be equals to remote api urls.
	
4. Build with Docker (on the example of my app). 
    * Be careful with the dot at the end in the next command - this is the current directory;
    * docker build -t cat-monitoring .
	* docker run -d -p 8080:80 cat-monitoring:latest
	* You may check current image with the command: `docker image ls`

5. Publication to Dockerhub
    * docker login
	* docker tag cat-monitoring DOCKER_HUB_NAME/cat-monitoring
	* docker push DOCKER_HUB_NAME/cat-monitoring