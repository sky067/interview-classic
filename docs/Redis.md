# Redis

## 如何保持redis与mysql数据一致性：

双删策略

1. 先删缓存
2. 再写入mysql
3. 等待时间（500ms），再删除缓存。

    - 此时删除的是写入mysql数据时，读行为在redis中产生的脏数据。产生的原因：第一次删除后，缓存中读不到数据，线程从mysql中将数据写入缓存，此时新数据还未写入mysql。

## 