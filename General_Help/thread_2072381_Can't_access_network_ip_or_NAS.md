---
title: "Can't access network ip or NAS"
date: 2012-10-17
forum: General Help
---

### Post by hippytyre on 2012-10-17
Hello,
I have a Qnap NAS connected to my network and it's working perfectly from my Windows laptop. When I try to access it from my ubuntu desktop I cant connect to it at all.

I've tried

'Connect to server', didn't work

Try to access the NAS ip 192.168.1.24 from Chrome, no luck

Browsing to the share via file manager, nothing. Yet it sees my router and windows laptop.

ping 192.168.1.24, no response.


any ideas on what might be wrong? I reinstalled samba, and did an update/upgrade apt-get.



Thanks.

---

### Post by steeldriver on 2012-10-17
Have you tried

```
sudo smbtree
```

to make sure the share(s) are visible? also I think the client side package is 'smbclient' ('samba' is the server side iirc)

---

