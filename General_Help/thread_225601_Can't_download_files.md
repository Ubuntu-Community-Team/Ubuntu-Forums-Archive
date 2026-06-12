---
title: "Can't download files"
date: 2006-07-30
forum: General Help
---

### Post by mempf on 2006-07-30
I have a laptop with Ubuntu 6.06 Dapper Drake. When I try and download any kind of largish file, Edgy daily build, fedora core, or random videos my connection keeps timing out.

I have a broadcom 4318 wireless card using ndiswrapper however I have also tried over a wired network with the same results.

It is important I am able to download these files.

I have tried downloading with firefox, wget, d4x, freeloader and others all resulting with the connection timing out.

How can I resolve this problem?

Thanks

---

### Post by mempf on 2006-07-30
After some investigation it turns out the problem is that my router is blocking the packets because of the SPI filtering. 

The router thinks that ubuntu is sending malicious packets so it stopes them which in turn causes the download to cut out.

How can I fix ubuntu so it won't send these crappy packets?

---

### Post by jpkotta on 2006-07-30
I don't know what SPI filtering is or why Ubuntu is sending bad packets.  I can suggest ```
wget -c
```

Also, maybe you can use netstat to figure out what is sending the bad packets.

---

