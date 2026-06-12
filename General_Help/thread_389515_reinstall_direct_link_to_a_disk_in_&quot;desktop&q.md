---
title: "reinstall direct link to a disk in &quot;desktop&quot; and &quot;places&quot;"
date: 2007-03-20
forum: General Help
---

### Post by lucho115 on 2007-03-20
i install ubuntu 6.10 and it add my windows partions to "places" and "desktop", so i erase one partions with Gparted, and then i created again but with less space, i do this changes from the livecd, then i reboot normaly but my link to that partition in desktop and in places wasnt there, i can mount it from command line but the link dont appear instead. So i open devices manager and go to that partition, and i see that have i flag like this: "volume.ignore true" and then see the other partirion thats work ok and they have the same flag but with the value "false", i have try to change the value to falso but i cant.
anybody knows how to solve this issue??
thks

---

### Post by chewearn on 2007-03-21
You probably have to edit /etc/fstab

Post the output from the following:
```
sudo fdisk -l
```
```
cat /etc/fstab
```

---

### Post by lucho115 on 2007-04-28
OK, the problem is with the hal devices, exist any gui aplication to mod this configuration? like hal-device on console?
thks

---

