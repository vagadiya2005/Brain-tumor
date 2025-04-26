# Stage 1: Build with devDependencies (since you're running dev server)
FROM node:19-alpine AS builder

WORKDIR /app

COPY package*.json ./

# Install ALL dependencies, including dev
RUN npm ci

COPY . .

# No build step, you're using `react-scripts start`

# Final Stage (can be same as builder if for dev)
FROM node:19-alpine

WORKDIR /app

COPY --from=builder /app .

EXPOSE 3000

CMD ["npm", "start"]
