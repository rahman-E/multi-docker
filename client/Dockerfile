FROM node:alpine as builder
WORKDIR '/app'
COPY ./package.json ./
RUN npm install
RUN npm install axios
RUN npm install react-router-dom
COPY . .
RUN npm run build

FROM nginx
EXPOSE 3000
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
COPY --from=builder /app/build /usr/share/nginx/html
