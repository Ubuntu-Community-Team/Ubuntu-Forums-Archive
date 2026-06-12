---
title: "hda1 no space"
date: 2006-12-23
forum: General Help
---

### Post by arthursc on 2006-12-23
How can I free space on hda1??

gdm will not bot sa
pace all space all used??

---

### Post by taurus on 2006-12-23
Boot with the LiveCD, mount your /dev/hda1, and do some house cleaning...

Applications -> Accessories -> Terminal
```
sudo mkdir /mnt/ubuntu
sudo mount -t ext3 /dev/hda1 /mnt/ubuntu
cd /mnt/ubuntu/var/cache/apt/archives
sudo rm -rf *
cd
sudo umount /dev/hda1
```
Reboot and see if you can log in now!!!

---

### Post by arthursc on 2006-12-23
df still says 100% Used.

can I gui and browse the mounted hda1 to free space?

---

### Post by taurus on 2006-12-23
Look in the trash for your user and root as well!!!

```
sudo rm /mnt/ubuntu/root/.Trash/*
sudo rm /mnt/ubuntu/home/**arthursc**/.Trash/*
(assuming **arthursc** is your login name on the system...)
```

---

### Post by arthursc on 2006-12-23
sorted thanks

---

### Post by taurus on 2006-12-23
If you have a small harddrive, should keep an eye on the free space...  ;) 

```
df -h
```

---

