### Step 1: Download & install docker

### Step 2: Install postgreSQL
```docker pull postgres```

Run postgreSQL container
```docker run --name mattermost_postgres -e POSTGRES_USER=mmuser -e POSTGRES_PASSWORD=mmuser_password -e POSTGRES_DB=mattermost -d postgres```

### Step 3: Install mattermost server

Clone mattermost
```git clone https://github.com/mattermost/docker```
```cd docker```

Copy .env file and config it
```cp env.example .env```

<img width="601" alt="image" src="https://github.com/user-attachments/assets/c040c351-1ba6-4d0c-844e-2e2fb05ee32f">

```mkdir -p ./volumes/app/mattermost/{config,data,logs,plugins,client/plugins,bleve-indexes}```

```sudo chown -R 2000:2000 ./volumes/app/mattermost```

Run docker mattermost server
```docker compose -f docker-compose.yml -f docker-compose.without-nginx.yml up -d```

