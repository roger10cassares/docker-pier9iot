FROM node:16.14.0-alpine3.15

LABEL username <roger10cassares@gmail.com>

RUN apk update \
    && apk add tzdata \
    && apk add git

ENV TZ=America/Sao_Paulo

# Create app directory
WORKDIR /usr/src/app

RUN npm install bower -g

RUN echo '{ "allow_root": true }' > /root/.bowerrc

# Install app dependencies
COPY ./nodejs_smartcampus_pier9iot/*.json ./
COPY ./nodejs_smartcampus_pier9iot/.bowerrc ./

# RUN yarn
# If you are building your code for production
RUN rm -rf node_modules && yarn --frozen-lockfile

# Bundle app source
COPY ./nodejs_smartcampus_pier9iot ./

EXPOSE 7300
CMD [ "node", "start.js" ]
