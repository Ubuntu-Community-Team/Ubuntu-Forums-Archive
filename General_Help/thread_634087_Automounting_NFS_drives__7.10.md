---
title: "Automounting NFS drives : 7.10"
date: 2007-12-07
forum: General Help
---

### Post by xSauronx on 2007-12-07
Ok Ive got a debian box I use as a fileserver with samba/nfs

presently, i DO have the following in /etc/fstab

192.168.1.5:/home/xsauronx 	/home/xsauronx/actium	nfs	rsize=1024,wsize=1024,noauto 	0 	0
192.168.1.5:/multimedia	/var/multimedia		nfs	rsize=1024,wsize=1024,noauto	0	0

but it does NOT work :(
i have to manually mount my drives when i reboot or when the server reboots

id like, at the least, the NFS drives to mount with the rest of my local filesystem when my Ubuntu system boots, but ideally, id like to automount the NFS drives anytime the laptop OR the server reboots (that is, i want them treated almost like a flash drive: mounted whenever its available)

how can i go about this? and is my fstab syntax wrong for what i was trying to do?
thanks :)

---

### Post by Borbus on 2008-01-15
Well removing the noauto option would be the obvious way...

---

