---
title: "Transfering files over network"
date: 2008-01-16
forum: General Help
---

### Post by Heinrisch on 2008-01-16
[SOLVED] Check my last post..

I need a fast way to transfer files between my linux server and my windows laptop (server to laptop).
So far I have tried samba and get around 4 MB/s right now. FTP is about the same. HTTP goes around 2 MB/s, and ssh is the same as HTTP.
Is there any other way I can transfer my files? Is there some way to speed up the transfer speed (in terms of configuring samba, network props or similar).
My current samba config can be viewed here: [http://wihoo.no-ip.org/smb.conf]("http://wihoo.no-ip.org/smb.conf")

Thanks for any help!

---

### Post by amo-ej1 on 2008-01-16
Are you on a wireless link ?

---

### Post by Heinrisch on 2008-01-16
> **amo-ej1 said:**
> Are you on a wireless link ?

No, its a cable.. both server and laptop. Linksys router.

---

### Post by Heinrisch on 2008-01-17
anyone?

---

### Post by notwen on 2008-01-17
Other than trying SSH, the Ubuntu to Windows barrier might limit you to SMB.  I personally use NFS for transfers from my Debian Etch file server to my Ubuntu PC and Ubuntu laptop.  If you eventually lose your windows PC check out this [guide]("http://ubuntuguide.org/wiki/Ubuntu:Gutsy#NFS_Server") to NFS, it's pretty easy to get up & running on both ends. =]  Good luck w/ your issue, maybe this will come in handy in the future.

---

### Post by Heinrisch on 2008-01-18
Solved it myself. Wrote a simple java program that sends the file over the network.
I get around 10 MB/s with it.

If anyone wants the program, just PM me.

---

