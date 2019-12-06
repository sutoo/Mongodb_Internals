
配置服务器（对路由表具有权威性）将路由表信息另外存储在磁盘集合中
就是下面的3个表中：
retrieval_0.feature_meta_20的 databases
```
{ "_id" : "retrieval_0",
"primary" : "shard0",
"partitioned" : true,
"version" : { "uuid" : UUID("7df454d4-6532-454c-92cc-a829171c9eab"),
"lastMod" : 1 } }
```

retrieval_0.feature_meta_20的 collections
```
{
        "_id" : "retrieval_0.feature_meta_20",
        "lastmodEpoch" : ObjectId("5dde84db7afd011a5c5e170e"),
        "lastmod" : ISODate("1970-02-19T17:02:47.297Z"),
        "dropped" : false,
        "key" : {
                "_id" : "hashed"
        },
        "unique" : false,
        "uuid" : UUID("ccb66da8-73db-451e-a3d4-81fbea0a60d7")
}
```

retrieval_0.feature_meta_20的 chunks

```
{ "_id" : "retrieval_0.feature_meta_20-_id_MinKey",
"ns" : "retrieval_0.feature_meta_20",
"min" : { "_id" : { "$minKey" : 1 } },
"max" : { "_id" : NumberLong(0) },
"shard" : "shard0",
"lastmod" : Timestamp(1, 0),
"lastmodEpoch" : ObjectId("5dde84db7afd011a5c5e170e"),
"history" : [ { "validAfter" : Timestamp(1574864091, 21), "shard" : "shard0" } ] }   

{ "_id" : "retrieval_0.feature_meta_20-_id_0",
"ns" : "retrieval_0.feature_meta_20",
"min" : { "_id" : NumberLong(0) },
"max" : { "_id" : { "$maxKey" : 1 } },
"shard" : "shard0", "lastmod" : Timestamp(1, 1),
"lastmodEpoch" : ObjectId("5dde84db7afd011a5c5e170e"),
"history" : [ { "validAfter" : Timestamp(1574864091, 21), "shard" : "shard0" } ] }  
```
什么时候其他的角色(mongos, mongo shard)的`路由表`会过时？
* a sharded collection is dropped (and perhaps recreated with the same name)
* a collection becomes sharded or unsharded
* a chunk in the collection migrates from one shard to another
