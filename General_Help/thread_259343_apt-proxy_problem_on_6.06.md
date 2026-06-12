---
title: "apt-proxy problem on 6.06"
date: 2006-09-17
forum: General Help
---

### Post by GSMD on 2006-09-17
I've installed apt-proxy according to [Wiki Entry]("https://help.ubuntu.com/community/AptProxy?action=show&redirect=AptProxyHowTo") but what I get in the log when a client tries to **apt-get** is```
2006/09/17 16:12 EEST [-] apt_proxy.apt_proxy.Factory starting on 9999
2006/09/17 16:12 EEST [-] Starting factory <apt_proxy.apt_proxy.Factory instance at 0xb795c3ec>
2006/09/17 16:12 EEST [-] set uid/gid 107/65534
2006/09/17 16:13 EEST [Channel,0,10.1.1.100] Unhandled error in Deferred:
2006/09/17 16:13 EEST [Channel,0,10.1.1.100] Traceback (most recent call last):
          File "/usr/lib/python2.4/site-packages/twisted/web/http.py", line 557, in requestReceived
            self.process()
          File "/usr/lib/python2.4/site-packages/apt_proxy/apt_proxy.py", line 1400, in process
            self.fetch()
          File "/usr/lib/python2.4/site-packages/apt_proxy/apt_proxy.py", line 1482, in fetch
            (dummyFetcher, 0, running,), None)
          File "/usr/lib/python2.4/site-packages/twisted/internet/defer.py", line 182, in addCallbacks
            self._runCallbacks()
        --- <exception caught here> ---
          File "/usr/lib/python2.4/site-packages/twisted/internet/defer.py", line 307, in _runCallbacks
            self.result = callback(self.result, *args, **kw)
          File "/usr/lib/python2.4/site-packages/apt_proxy/apt_proxy.py", line 1451, in fetch_real
            fetcher = dummyFetcher.apEndTransfer(fetcher_class)
          File "/usr/lib/python2.4/site-packages/apt_proxy/apt_proxy.py", line 463, in apEndTransfer
            fetcher = fetcher_class(req)
          File "/usr/lib/python2.4/site-packages/apt_proxy/apt_proxy.py", line 317, in __init__
            self.activate(request)
          File "/usr/lib/python2.4/site-packages/apt_proxy/apt_proxy.py", line 616, in activate
            ClientFactory(self), request.backend.config.timeout)
          File "/usr/lib/python2.4/site-packages/twisted/internet/posixbase.py", line 392, in connectTCP
            c = tcp.Connector(host, port, factory, timeout, bindAddress, self)
          File "/usr/lib/python2.4/site-packages/twisted/internet/tcp.py", line 840, in __init__
            raise error.ServiceNameUnknownError(string="%s (%r)" % (e, port))
        twisted.internet.error.ServiceNameUnknownError: Service name given as port is unknown: service/proto not found ('').
```
Is there anything to do with that?

---

