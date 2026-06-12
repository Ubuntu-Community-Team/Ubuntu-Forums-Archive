---
title: "Timed out waiting for dev-disk-by-id for encrypted RAID volume"
date: 2015-06-16
forum: General Help
---

### Post by tyteen4a03 on 2015-06-16
I just got a "Timed out waiting for dev-disk-by-id 5baf3c76-ad4f-4888-a792-5859aba6c7cf to load" when booting up. It is a encrypted RAID10 drive and all cables are connected correctly; I don't know what the problem is. The RAID array is mounted as /home, therefore I can't boot.

---

### Post by raja.genupula on 2015-06-16
Before going to do anything I suggest you to take a backup of > /etc/fstab file. We need the content in your /etc/fstab file. and output of > sudo blkid command.

If possible provide us RAID info.

---

### Post by raja.genupula on 2015-06-16
Hi , If in case I dont respond intime , go through below links and try . but dont forget backup /etc/fstab

[https://bbs.archlinux.org/viewtopic.php?id=154633](https://bbs.archlinux.org/viewtopic.php?id=154633)
[http://forums.fedoraforum.org/showthread.php?t=282602](http://forums.fedoraforum.org/showthread.php?t=282602)

---

### Post by tyteen4a03 on 2015-06-16
For some reason, after I mounted the RAID partition in Parted Magic, everything worked again. No idea what happened.

Thanks for trying to help anyway.

---

### Post by raja.genupula on 2015-06-16
We are glad to know your issue got solved, Please mark the thread as solved. 

And may be systemd unable to find the given RAID partition at booting , but with UUID it can. May be parted magic used its UUID to mount it. 

Think that way if you get same issue again.

Good day. : )

---

