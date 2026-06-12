---
title: "ext3 Partition Keeps Mounting As Read-only"
date: 2006-12-01
forum: General Help
---

### Post by hxx4 on 2006-12-01
I have two internal hard drives (excluding the hard drive ubuntu is installed on). Both are 200gb ext3 partitions. Here are the relevant parts of my /etc/fstab file:```
# /dev/hdc1
UUID=f8481eb6-866c-4fd6-a2a6-8fa207ba18a2 /home/user/Desktop/hdc1 ext3 defaults

# /dev/hdd1
UUID=0721b9d2-9d7a-478b-8c78-032d6550db30 /home/user/Desktop/hdd1 ext3 defaults
```The problem is that hdc1 mounts as read-only. I tried unmounting both of them, deleting the mountpoints, recreating the mount points, and then remounting them. They both ended up read-write after that. However, when I rebooted, I ran into the same problem where hdc1 was read-only again. Here is the fdisk info on them:```
Disk /dev/hdc: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1               1       24321   195358401   83  Linux

Disk /dev/hdd: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1               1       24321   195358401   83  Linux

```I believe the problem is happening because of the ownership and permissions of the mountpoints. I cannot figure out why the ownership and permissions are different for the two partitions when they are seemingly identical. I have attached screenshots of the permissions for hdc1 (problematic) and hdd1 (functional). For the record, hdc1 is completely empty at the moment as it is brand-new, and hdd1 has just over 10gb free.

---

### Post by LLRNR on 2006-12-01
Seems strange... ```
mount
```?

Another thing you might want to try is to **cd ~/Desktop** and then use **ls -al** to check the owner / permissions on both *hdc1* and *hdd1* to see what's wrong.

LLRNR

---

### Post by hxx4 on 2006-12-01
mount returns ```
/dev/hdc1 on /home/user/Desktop/hdc1 type ext3 (rw)
/dev/hdd1 on /home/user/Desktop/hdd1 type ext3 (rw)

```
ls -al returns```
drwxr-xr-x  2 root  root   4096 2006-11-29 21:06 hdc1
drwxrwxrwx 10   999 root   4096 2006-11-30 18:41 hdd1

```Obviously the ownership and permissions are different, but why? The permissions were fine and I was the owner of the mountpoints when I first created them, but after rebooting, the ownership and permissions changed.

---

### Post by LLRNR on 2006-12-01
"mount" says it's ok, since they're both **rw**, that's alright.

But what about that *hdc1* which appears without write permissions? One thing I'd do would be ```
sudo chmod a+w -vR hdc1
``` (you'll still have to be in ~/Desktop)

See if that has any effect.

LLRNR

---

### Post by hxx4 on 2006-12-01
Thank you very much LLRNR! Changing the permissions as you suggested worked. I rebooted to ensure that the permissions would not change on their own again, and they appear to be fine now.

---

### Post by LLRNR on 2006-12-01
I'm glad it worked :D (Usually I **chmod a-rwx** my personal folder on the PC from my University... and so far my colleagues - since there's only a generic *student* account - didn't think of checking the permissions *heh heh*)

LLRNR

---

### Post by wgscott on 2006-12-02
I had a very similar problem.


Using the old /dev/foo syntax in /etc/fstab rather than the newer edgy
UUID syntax appears to fix the problem (leaving all original permissions intact -- global write permissions on every file on the device is a little too scary for me.

---

### Post by odin1965 on 2006-12-03
Could mounting previously formatted drives in /home/Desktop create some odd behavior with the permissions? Since the permissions on /home are different than /mnt or /media? Were both drives formatted by the owner of /home?

I tens to stick with mounting in /mnt or /media if I have to manullly mount a whole partition.

---

