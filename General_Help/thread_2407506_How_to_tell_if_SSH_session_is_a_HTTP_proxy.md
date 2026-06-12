---
title: "How to tell if SSH session is a HTTP proxy"
date: 2018-12-05
forum: General Help
---

### Post by achmonth on 2018-12-05
Hi,

I use several servers as different HTTP proxies over SSH.
Often I open up new non-proxy SSH sessions into these same servers to do other work, and to avoid confusion I have until now opened the proxy SSH sessions in their own workspace.
But sometimes I am still in doubt.

Are there some easy way to see if my current SSH session also works as a HTTP proxy?

---

### Post by TheFu on 2018-12-05
Check the ssh options.  This is how I startup an SSH-based SOCKS proxy.
```
$ ssh -f -C -D 64000 123.1.2.3 -NT
```

And I have the web browser specify to use port 64000 for the proxy ... 
```
$ chromium-browser --proxy-server="socks5://localhost:64000" &
```

Unfortunately, Firefox doesn't allow a simple command line option to force a proxy be used. To use FF with a proxy, we have to setup a  new profile and use that.  Meh.

---

