---
title: "Mount ftp?"
date: 2007-10-07
forum: General Help
---

### Post by Martje_001 on 2007-10-07
Hi,
I added this line to my fstab:
```
curlftpfs#myuser:mypass@192.168.1.65 /mnt/music fuse rw,uid=500,user,noauto 0 0
```
But it doesn't get mounted :(. If I do
```
sudo curlftpfs -o allow_other ftp://myuser:mypass@192.168.1.65 /mnt/music
```
it all works fine :(.

---

