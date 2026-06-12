---
title: "ssh doesn't work with corkcrew to connect via proxy"
date: 2013-08-30
forum: General Help
---

### Post by cthlhu1987 on 2013-08-30
Since I only connect to the net via proxy, I have to use corkscrew, but it won't work ;( Here's my ~/.ssh/config file:

```
Host *
  ProxyCommand corkscrew <redacted>:<redacted>@<redacted> 8080 %h %p
```

but ssh gives me the following error:

```
Couldn't establish connection to proxy: Network is unreachable
ssh_exchange_identification: Connection closed by remote host
```

I did successfully make a ssh session via firessh, so the proxy apparently doesn't filter ssh connections. You know, what to do?

---

