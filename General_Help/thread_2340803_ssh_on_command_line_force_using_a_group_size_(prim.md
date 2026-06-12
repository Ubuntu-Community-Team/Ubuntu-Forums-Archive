---
title: "ssh on command line: force using a group size (prime size) of 1024 (and not 2048)"
date: 2016-10-22
forum: General Help
---

### Post by veraee on 2016-10-22
Hi

Is there a way to make ssh use prime size of 1024, i.e. 
Not sending 

SSH2_MSG_KEX_DH_GEX_REQUEST(1024<2048<8192) sent

to the server, but

SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<1024) sent

instead
(just to ckeck if the server refuses too small prime size)

Thanks in advance

---

