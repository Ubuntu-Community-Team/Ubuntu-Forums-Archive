---
title: "rsync and compression"
date: 2016-05-02
forum: General Help
---

### Post by alain.roger on 2016-05-02
Hi,

Can you explain me what is the compression parameter purpose on rsync ?
because whatever level i use the source and destination are only files/directories synchronization and no compression (like in zip, tar, etc) is used are it is only synchronization.

so i would be glad to understand the parameter purpose.

thx

---

### Post by HermanAB on 2016-05-02
It does exactly what it says on the tin:
-z, --compress              compress file data during the transfer

So it reduces the bandwidth used when you use rsync across a network.
After the transfer, the two files (source and destination) will be identical.

---

### Post by alain.roger on 2016-05-02
Ok so i understood it correctly.. it does not compress destination files, just it compress during transfer to reduce time and bandwidth.
thx for confirmation

---

