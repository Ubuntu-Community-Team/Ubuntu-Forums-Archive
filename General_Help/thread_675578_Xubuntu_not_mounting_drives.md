---
title: "Xubuntu not mounting drives"
date: 2008-01-22
forum: General Help
---

### Post by winston84 on 2008-01-22
Hello I have Xubuntu 7.10 installed on a PATA drive I also have 2 SATA drives 250GB with Xp on it 
and a 500GB drive now i boot just fine on Xubuntu and XP but in Xubuntu my SATA drives don't
auto-mount but my USB 500GB (NTFS) mounts just fine so it not NTFS. One other thing this is new
when I first installed Xubuntu there was no problem. The drive do mount if I do it my self

### mount root/windowsXP
sudo mkdir /media/root
sudo mount -t ntfs-3g /dev/sdb1 /root


### partion 2 on 250GB
sudo mkdir /media/aux
sudo mount -t ntfs-3g /dev/sdb2 /media/aux

#### 500gb drive
sudo mkdir /media/500gb
sudo mount -t ntfs-3g /dev/sdc3 /media/500gb

Thanks Winston84

---

### Post by jken146 on 2008-01-24
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by winston84 on 2008-01-24
I fixed the problem I had to add  add some line to my fstab file it wasn't a ntfs problem as my 
USB drive is ntfs For some reason the drives were not mounting at boot like they did when I 
first installed Xubuntu. :)

---

