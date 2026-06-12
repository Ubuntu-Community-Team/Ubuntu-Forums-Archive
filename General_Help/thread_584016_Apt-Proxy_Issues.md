---
title: "Apt-Proxy Issues"
date: 2007-10-20
forum: General Help
---

### Post by MobiusNZ on 2007-10-20
Hey guys,

I run 2 ubuntu servers and 3 desktop/laptops on my home network, so I've decided to have apt-proxy on one of my servers. This is kind of working ok, as the clients are updating as they should - sometimes. Often when I "sudo apt-get update" on my clients, it seems to hang at 99% [Waiting for headers]. When I jump on the my server, I see this in my /var/log/apt-proxy.log
```
2007/10/22 00:35 +1300 [Channel,0,192.168.1.1] [CacheEntry] start download:dists/gutsy-security/Release
2007/10/22 00:35 +1300 [FetcherHttpClient,client] [fetcher] (dists/gutsy/Release) up_to_date
2007/10/22 00:35 +1300 [FetcherHttpClient,client] [CacheEntry] sending file from cache:/files/cache/apt-proxy/ubuntu/dists/gutsy/Release
2007/10/22 00:35 +1300 [FetcherHttpClient,client] [CacheEntry] transfer_file:/files/cache/apt-proxy/ubuntu/dists/gutsy/Release
2007/10/22 00:35 +1300 [FetcherHttpClient,client] Starting factory <apt_proxy.fetchers.HttpFetcher instance at 0x84c360c>
2007/10/22 00:35 +1300 [FetcherHttpClient,client] Stopping factory <apt_proxy.fetchers.HttpFetcher instance at 0x84b9e2c>
2007/10/22 00:35 +1300 [FetcherHttpClient,client] [fetcher] (dists/gutsy-updates/Release) up_to_date
2007/10/22 00:35 +1300 [FetcherHttpClient,client] [CacheEntry] sending file from cache:/files/cache/apt-proxy/ubuntu/dists/gutsy-updates/Release
2007/10/22 00:35 +1300 [FetcherHttpClient,client] [CacheEntry] transfer_file:/files/cache/apt-proxy/ubuntu/dists/gutsy-updates/Release
2007/10/22 00:35 +1300 [FetcherHttpClient,client] Starting factory <apt_proxy.fetchers.HttpFetcher instance at 0xb78e03ec>
2007/10/22 00:35 +1300 [FetcherHttpClient,client] Stopping factory <apt_proxy.fetchers.HttpFetcher instance at 0x84c360c>
2007/10/22 00:35 +1300 [FetcherHttpClient,client] [fetcher] (dists/gutsy-security/Release) up_to_date
2007/10/22 00:35 +1300 [FetcherHttpClient,client] [CacheEntry] sending file from cache:/files/cache/apt-proxy/ubuntu/dists/gutsy-security/Release
2007/10/22 00:35 +1300 [FetcherHttpClient,client] [CacheEntry] transfer_file:/files/cache/apt-proxy/ubuntu/dists/gutsy-security/Release
2007/10/22 00:35 +1300 [FetcherHttpClient,client] Stopping factory <apt_proxy.fetchers.HttpFetcher instance at 0xb78e03ec>
2007/10/22 00:35 +1300 [Channel,0,192.168.1.1] Unhandled error in Deferred:
2007/10/22 00:35 +1300 [Channel,0,192.168.1.1] Unhandled Error
        Traceback (most recent call last):
          File "/usr/lib/python2.5/site-packages/twisted/internet/abstract.py", line 132, in doWrite
            self.producer.resumeProducing()
          File "/usr/lib/python2.5/site-packages/twisted/protocols/basic.py", line 442, in resumeProducing
            self.deferred.callback(self.lastSent)
          File "/usr/lib/python2.5/site-packages/twisted/internet/defer.py", line 239, in callback
            self._startRunCallbacks(result)
          File "/usr/lib/python2.5/site-packages/twisted/internet/defer.py", line 304, in _startRunCallbacks
            self._runCallbacks()
        --- <exception caught here> ---
          File "/usr/lib/python2.5/site-packages/twisted/internet/defer.py", line 317, in _runCallbacks
            self.result = callback(self.result, *args, **kw)
          File "/usr/lib/python2.5/site-packages/apt_proxy/cache.py", line 267, in file_transfer_complete
            request.finish()
          File "/usr/lib/python2.5/site-packages/apt_proxy/apt_proxy.py", line 324, in finish
            http.Request.finish(self)
          File "/usr/lib/python2.5/site-packages/twisted/web/http.py", line 671, in finish
            self._cleanup()
          File "/usr/lib/python2.5/site-packages/twisted/web/http.py", line 483, in _cleanup
            self.channel.requestDone(self)
          File "/usr/lib/python2.5/site-packages/twisted/web/http.py", line 1098, in requestDone
            self.requests[0].noLongerQueued()
          File "/usr/lib/python2.5/site-packages/twisted/web/http.py", line 518, in noLongerQueued
            self._cleanup()
          File "/usr/lib/python2.5/site-packages/twisted/web/http.py", line 483, in _cleanup
            self.channel.requestDone(self)
        exceptions.AttributeError: Request instance has no attribute 'channel'


```

Any ideas on this one?

---

### Post by MobiusNZ on 2007-11-02
Hmmm, seems to be some sort of problem with the whitespacing or something -- I copied my sources.list from another computer and it worked fine!!

---

