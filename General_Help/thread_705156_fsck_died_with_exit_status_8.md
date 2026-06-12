---
title: "fsck died with exit status 8"
date: 2008-02-23
forum: General Help
---

### Post by mrhammad on 2008-02-23
fsck 1.40.2 (12-Jul-2007)
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
/dev/sda5: 296 files, 3803/1220891 clusters
Failed to open the device 'UUID=7fb43e05-a1ec-4a6b-aee2-e5b3d5e542bf': No such file or directory


fsck died with exit status 8

Sat Feb 23 13:39:11 2008

It happened after I install Ubuntu studio 7.10 on sda5 where as Ubuntu 7.10 was already installed on sda7 both are using same swap partition

it says correct the problem manually and leave me at bash root where after pressing Control+D Ubuntu opens

---

### Post by forestpixie on 2008-02-23
I believe that fstab is trying to mount a partition which doesn't exist - check by running blkid in terminal and checking the UUID against the UUID referenced in fstab - if there are differences you need to edit the file

```
blkid
cat /etc/fstab
```

to backup and edit

```
sudo cp /etc/fstab /etc/fstab.bak.2302
gksudo gedit /etc/fstab
```

---

### Post by mrhammad on 2008-02-24
Thanks forestpixie

after my installation of ubuntu studio the UUID was changed but when i boot ubuntu it happened so I changed the fstab of ubuntu today.

Now what i think is grub installed by ubuntu studio is active but i wish to activate this of ubuntu how can i make ubuntu to install its grub in action.

---

### Post by forestpixie on 2008-02-24
sorry - but not sure what you're asking

---

