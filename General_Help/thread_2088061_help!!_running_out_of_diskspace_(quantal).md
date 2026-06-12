---
title: "help!! running out of diskspace (quantal)"
date: 2012-11-25
forum: General Help
---

### Post by ray field on 2012-11-25
Last week I started getting messages that my root filesystem was running out of free space. I thought it was some sort of weird glitch, until a day or two later when I was unable to get past the bad graphics popup on boot. When I rebooted into a 12.4 partition I saw that the 30GB 12.10 root partition was indeed out of room.  It didn't make sense to me, but since I had some unallocated disk space, I added 10GB to the root partition after which things seemed fine.

Today I was trying to copy a friend's DVD when k3b told me there wasn't enough room left in /tmp to proceed. Sure enough according to Midnight Commander, all I have is 1012M free of 42 GB. 

I thought maybe something was going crazy with log files, but right now /var/log only has 15.2 MB.

Searching around I found someone suggested running sudo du --max-length=1, which gives 

```
12M	/opt
4.0K	/srv
128K	/tmp
188G	/usr
1.1M	/run
16K	/lost+found
1.2M	/root
1.6G	/var
57M	/boot
295M	/lib
4.0K	/selinux
15M	/sbin
9.5G	/home
12K	/mnt
8.8M	/bin
12K	/dev
0	/proc
0	/sys
3.2T	/media
71M	/etc
4.0K	/cdrom
3.4T	/
```


Note 3.4T in / !

Have I somehow screwed up mounting? I have 

* three external HDs that automount in /media, along with my old Precise /home

* two windows drives automount in /mnt

I thought it was maybe a root cron process but I've cleared out the crontab and still seem to be running out of filespace. I can't really think of anything I've installed that would have caused this. help!!

---

### Post by ray field on 2012-11-25
fixed it. had a bunch of rsnapshot bash scripts in my root crontab, which I thought would simply fail if the external drive was disconnected, but I guess I was wrong.

---

