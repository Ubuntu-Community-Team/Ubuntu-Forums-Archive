---
title: "SYSTEM DOWN - Please Help. FSTAB; user-dirs.dirs; nautilus not functioning"
date: 2014-02-01
forum: General Help
---

### Post by David_Weiner on 2014-02-01
1. I have my OS (Ubuntu 13.10) on /dev/sdc
 Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *        2048   565118975   282558464   83  Linux
/dev/sdc2       565121022   586072063    10475521    5  Extended
/dev/sdc5       565121024   586072063    10475520   82  Linux swap / Solaris

2. I have my data on /dev/sda and its backup on /dev/sdb
Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048  1953523711   976760832   83  Linux
&
Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048  1953523711   976760832   83  Linux

Question: Do I need the Extended and swap partitions on the data drives?




3. Here are the UUID's of the relevant drives:
/dev/sda1: LABEL="data" UUID="c6f3b0bc-f5f7-4ec2-88ea-a7f18e27cb2d" TYPE="ext4" 
/dev/sdb1: LABEL="backup" UUID="e1321101-627d-41ee-a7a5-6d3ba4288ff6" TYPE="ext4" 
/dev/sdc1: UUID="fd7fd8b1-2619-4aeb-bd8f-fa97707b4aff" TYPE="ext4" 
/dev/sdc5: UUID="cd7d2752-0eab-425e-9fb7-a19e616956ab" TYPE="swap" 

4. FSTAB
UUID=fd7fd8b1-2619-4aeb-bd8f-fa97707b4aff / ext4 errors=remount-ro 0 1
UUID=cd7d2752-0eab-425e-9fb7-a19e616956ab none swap sw 0 0
UUID=c6f3b0bc-f5f7-4ec2-88ea-a7f18e27cb2d /media/data ext4 defaults 0 0
UUID=e1321101-627d-41ee-a7a5-6d3ba4288ff6 /media/david/backup ext4 defaults 0 0

5. user-dirs.dirs
XDG_DESKTOP_DIR="/media/david/data/Desktop" ; this is the correct mount point

Since the "data" drive is not mounting, I get a black screen. I cannot launch open any drive with the nautilus launcher. If I "gksu nautilus," I get a blue screen and nautilus opens. When I try to access the OS, data or backup drives, no files or hidden files appear. 

My system is totally unusable and any help would be greatly appreciated.
DWLima

PS. 
ls -l /media/
total 112
drwxr-xr-x   2 root root  4096 Jan  6 15:25 bin
drwxr-xr-x   3 root root  4096 Jan 31 08:14 boot
drwxr-xr-x   2 root root  4096 Dec  5 17:10 cdrom
drwxr-xr-x   4 root root  4096 Oct 16 12:03 dev
drwxr-xr-x 152 root root 12288 Feb  1 11:53 etc
drwxr-xr-x   3 root root  4096 Dec  5 17:13 home
lrwxrwxrwx   1 root root    33 Jan  6 15:26 initrd.img -> boot/initrd.img-3.11.0-15-generic
lrwxrwxrwx   1 root root    34 Jan  6 15:25 initrd.img.old -> /boot/initrd.img-3.11.0-15-generic
drwxr-xr-x  24 root root  4096 Dec  7 21:19 lib
drwxr-xr-x   2 root root  4096 Oct 16 11:58 lib64
drwx------   2 root root 16384 Dec  5 17:08 lost+found
drwxr-xr-x   6  755 root  4096 Feb  1 08:12 media
drwxr-xr-x   2 root root  4096 Oct 13 13:41 mnt
drwxr-xr-x   3 root root  4096 Jan 25 23:05 opt
drwxr-xr-x   2 root root  4096 Oct 13 13:41 proc
drwx------   9 root root  4096 Jan 25 07:53 root
drwxr-xr-x  12 root root  4096 Oct 16 12:03 run
drwxr-xr-x   2 root root 12288 Jan 22 22:26 sbin
drwxr-xr-x   2 root root  4096 Oct 16 11:58 srv
drwxr-xr-x   2 root root  4096 Jun  4  2013 sys
drwxrwxrwt   9 root root  4096 Feb  1 11:55 tmp
drwxr-xr-x  10 root root  4096 Oct 16 11:58 usr
drwxr-xr-x  13 root root  4096 Oct 16 12:05 var
lrwxrwxrwx   1 root root    30 Jan  6 15:26 vmlinuz -> boot/vmlinuz-3.11.0-15-generic
lrwxrwxrwx   1 root root    30 Jan  6 15:25 vmlinuz.old -> boot/vmlinuz-3.11.0-15-generic

---

### Post by David_Weiner on 2014-02-01
Well, the mounting path changed and once I commented the path to the data drive out so that it points back to the OS drive, it all works. False alarm. Sorry.

---

### Post by bc.haynes on 2014-02-01
You might mark this thread as [SOLVED]   > Post # 1 > Thread Tools > "Mark this thread solved."

---

