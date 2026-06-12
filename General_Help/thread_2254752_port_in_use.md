---
title: "port in use"
date: 2014-11-29
forum: General Help
---

### Post by ELMIT on 2014-11-29
I get:
An error occured while setting up the RPC port 12128 for listening: bind: Address already in use ...

Howerver, when I try to 
sudo netstat -ltnp |grep '12128'

I get nothing back.

???

---

### Post by steeldriver on 2014-11-29
What do you get if you remove the netstat -t flag or replace it with -u ? it may be using UDP not TCP

---

### Post by ELMIT on 2014-11-29
I get the same, ... nothing

---

