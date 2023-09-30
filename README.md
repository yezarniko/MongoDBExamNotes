## One-Minute Test Setup

`$ mongo --nodb`  
`> cluster = new ShardingTest({"shards": 3, "chunksize": 1})`

## Sh

##### Sharding status
`> sh.status()`

##### Shard a particular collection
`> sh.enableSharding("test")` or `db.enableSharding("test")`   
`> db.users.ensureIndex({"username": 1})`  
`> sh.shardCollection("test.users", {"username": 1})`

##### Shard a particular collection with hash shard key
`db.users.ensureIndex({"username": "hashed})`   
`sh.shardCollection("app.users",{"username": "hashed})`

#### Shutdown all of the servers
`> cluster.stop()`


#### Adding a shard from a replica set
`> sh.addShard("spock/server-1:27017,server-2:20717,server-4:27017)`

#### Adding shard Tag
`> sh.addShardTag("shard0000", "USPS")`   
`> sh.addShardTag("shard0000", "Apple")`  
`> sh.addShardTag("shard0002", "Apple")`

#### Adding shard Tag Range
`sh.addTagRange("test.ips", {"ip": "056.000.000.000"},{"ip": "057.000.000.000"}, "USPS")`  
`sh.addTagRange("test.ips", {"ip": "017.000.000.000"},{"ip": "018.000.000.000"}, "Apple")`


#### Turning off the balancer
`> sh.setBalancerState(false)`