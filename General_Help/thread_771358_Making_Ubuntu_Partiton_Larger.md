---
title: "Making Ubuntu Partiton Larger"
date: 2008-04-27
forum: General Help
---

### Post by RATM_Owns on 2008-04-27
I really have no idea whatsoever how to do this.

I'll kinda need step by step instructions. xP

---

### Post by ibuclaw on 2008-04-27
1) If you have multiple partitions, open up a terminal and type in:
```
df -h
```
And take note of the Filesystem location of the partition mounted to **/**:
ie: My Output...
```

Filesystem            Size  Used Avail Use% Mounted on
**/dev/sdb1**              27G  6.8G   19G  27% /

```

2) Insert the Ubuntu LiveCD

3) Reboot your Computer

4) Enter LiveCD, wait for the Ubuntu Environment to load.

5) Open up GParted. Go into "**System>Administration>Partition Editor**"

6) Find the filesystem location of your root partition (the one you identified earlier) and right-click on it within GParted and select "Resize/Move"

7) Resize at will.

Regards
Iain

---

### Post by Gregory_NZL on 2008-04-28
Why is the partition editor not available in the installed version of 8.04? At least not on my system.

---

### Post by jespdj on 2008-04-28
I don't know why it's not present by default on an installed system, but it's easy to add:
```
sudo apt-get install gparted
```

---

### Post by ryanhaigh on 2008-04-28
This is not as simple as that, when you mess with a partitions size you are going to change its UUID, when that filesystem is the root partition you are going to be left with an unbootable system. There are many posts on here regarding resizing and ubuntu not booting. After you resize you are going to need to fix grubs menu.lst, /etc/fstab and if you use hibernate initramfs. If you have a freshly installed system and have your home folder on a separate partition it may be easier just to reinstall. (I can't believe I am forced to say that about a Linux system, why oh why are we not using labels instead of uuid).

---

### Post by Gregory_NZL on 2008-04-28
Thanks for your answer ryanhaigh. So I guess its safe/preferable to do it from the Live CD.

---

