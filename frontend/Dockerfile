# ===== STAGE 1 : Build Angular avec Node =====
FROM node:22-alpine AS build
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
RUN npm run build -- --configuration production

# ===== STAGE 2 : Servir avec Nginx Alpine =====
FROM nginx:alpine
# Angular 22 met les fichiers dans dist/frontend/browser/
COPY --from=build /app/dist/frontend/browser /usr/share/nginx/html
EXPOSE 80
