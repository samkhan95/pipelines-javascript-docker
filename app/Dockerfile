# syntax=docker/dockerfile:1

FROM node:12.18.1
ENV NODE_ENV=production

WORKDIR /app

# Install setcap package
RUN apt install libcap2-bin
# ...
# Give access to the ports below 1024 to non-root users
RUN setcap 'cap_net_bind_service=+ep' $(readlink -f $(which node))

COPY ["package.json", "package-lock.json*", "./"]

RUN npm install --production

COPY . .

EXPOSE 8080
CMD [ "node", "server.js" ]
