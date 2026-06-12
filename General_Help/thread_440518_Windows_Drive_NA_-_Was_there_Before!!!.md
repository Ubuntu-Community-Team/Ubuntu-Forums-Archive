---
title: "Windows Drive N/A - Was there Before!??!!"
date: 2007-05-11
forum: General Help
---

### Post by tosimran on 2007-05-11
I've installed ubuntu and on my second or third restart (after installing ntfs-config, which allowed me the ability to access and modify all my other drives), my windows partition is missing in places>Computer. It was present before ntfs-config was installed, but doesn't show up now. Any help would be appreciated.

- Super-green Linux user

---

### Post by wtruong on 2007-05-11
If you hibernate in windows, you can't access your ntfs partitions.  So just go in windows and shut down properly and then start up ubuntu

---

### Post by tosimran on 2007-05-15
sorry for the late reply. Did that several times, but no luck. It still doesn't show up. And now i've got some issues with my external HDD, but i've got some links thats i'm following for that one.

---

### Post by wataboutbob on 2007-05-16
Hi, can you try turning off NTFS-config by going to Applications > System Tools > NTFS and see if they are mounted then.

You might also want to check if the volume_id for the HDDs listed in your fstab are correct. You can check this by running the following commands in a terminal

```
sudo fdisk -l
```

this gives details of all your HDD's (external and internal) connected to your system.

```
sudo vol_id /dev/sdaX
```

where X is the correct sda number. This will give volume label and id that can be compared to your fstab

---

