# Start local mongodb

### When `docker-compose.yml` is in the root folder

```bash
docker-compose up
```

### When `docker-compose.yml` is in the nested folders

```bash
docker-compose -f ./mongodb/docker-compose.yml up
```

# Connection string

```bash
mongodb://root:example@localhost:27017/dbName?retryWrites=true&w=majority&authSource=admin
```

# Connect using MongoDB Compass GUI client

- Download [MongoDB Compass](https://www.mongodb.com/products/tools/compass)
- Enter the above connection string with correct `username` and `password` and hit connect
- That's it you are good to go now!

# Access mongo shell with permissions

```bash
docker-compose -f compose.yml run mongo mongosh -u root -p example --host mongo
```

- `-u root` this is the username that we have provided in the compose file with `MONGO_INITDB_ROOT_USERNAME: root` env var
- `-p example` this is the password that we have provided in the compose file with `MONGO_INITDB_ROOT_PASSWORD: example` env var

After running this you will see the following output:

```bash
Current Mongosh Log ID: 65916c87334d0c4c484182d6
Connecting to:          mongodb://<credentials>@mongo:27017/?directConnection=true&appName=mongosh+1.10.1
Using MongoDB:          6.0.8
Using Mongosh:          1.10.1

For mongosh info see: https://docs.mongodb.com/mongodb-shell/

------
   The server generated these startup warnings when booting
   2023-12-31T13:14:21.738+00:00: vm.max_map_count is too low
------

test>
```

Now, run `show dbs` and you will get the list of dbs as follows:

```bash
test> show dbs
admin   100.00 KiB
config  108.00 KiB
local    72.00 KiB
```

Now, you can run mongodb related commands here
