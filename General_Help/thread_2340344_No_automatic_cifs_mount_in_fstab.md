---
title: "No automatic cifs mount in fstab"
date: 2016-10-17
forum: General Help
---

### Post by piotergmoter on 2016-10-17
Hi
I have just installed kubuntu 16.04 and the problem is with automounting (during boot) my NAS (using cifs) shares. fstab looks like this:
//bimba/domek /mnt/domek        cifs    credentials=/root/.smbcredentials,iocharset=utf8,rw,nounix,_netdev,file_mode=0777,dir_mode=0777 0 0
It worked fine in kubuntu 14.04 even without _netdev option.
Now when I login to my desktop the shares are not mounted. But the sudo mount -a works without any problems. I guess it is the network problem (ie. no network) during boot time (I have wifi access to NAS). But I thought that _netdev should solve this and why kubuntu 14 had no problem with this?
So now I have no idea what to do.

Regards
Piotr

---

### Post by bashiergui on 2016-10-18
Maybe set a cron job to mount it after it has connected to wifi.

---

### Post by piotergmoter on 2016-10-19
> **bashiergui said:**
> Maybe set a cron job to mount it after it has connected to wifi.

Well, cron is for cyclic jobs. Much better solution would be to mount it just after the network is connected. And it looks like in 16.04 it is not possible what worked fine in older 14.04. Sad.


P.

---

