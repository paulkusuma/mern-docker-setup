# Dockerfile Frontend
FROM node:18 as build

WORKDIR /app

# Copy package.json dan install dependencies
COPY package*.json ./
RUN npm install

# Copy semua source code frontend
COPY . .

# Build aplikasi React
RUN npm run build

# Gunakan nginx untuk serve hasil build
FROM nginx:alpine
COPY --from=build /app/build /usr/share/nginx/html

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]