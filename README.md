# jzsystemd
##1
4s: scenario, service, storage, scale

QPS
150m*60(average request time)/86400 = 100k
peak user*3
max=peak*2


QPS= 1k (single point failure)
QPS=1m(1000 servers)
SQL 1kqps (if lots of join and index query, will be smaller)
NOSQL , cassandra 10k
NOSQL, memcached 1M

#### pull model
```
getNewsFeed(request):
  followings = DB.getFollowings(user=request.user)
  news_feed = empty
  for followr in followings:
    tweets = DB.getTweets(following.to)user,100)
    news_feed.merge(tweets)
  sort(news_feed)
  return news_feed


postTweet(request,tweet)
  DB.insert(request,tweet)
  return success

