---
title: "&quot;cloudflare warp daemon&quot; error when register the client"
date: 2021-06-29
forum: General Help
---

### Post by hiepvs on 2021-06-29
[COLOR=black][FONT=Arial]Hi, I use xubuntu 18.04. I installed warp client for ubuntu 16.04, I have an error when register the warp client:
```

pc@pc:~/Desktop$ warp-cli register

```[/FONT][/COLOR]```
Unable to connect to CloudflareWARP daemon. Maybe the daemon is not running, or is connected to another process?
```
[COLOR=black][FONT=Arial]How to solve it? Thanks
[/FONT][/COLOR]

---

### Post by hiepvs on 2021-06-30
sudo systemctl start warp-svc.service

---

