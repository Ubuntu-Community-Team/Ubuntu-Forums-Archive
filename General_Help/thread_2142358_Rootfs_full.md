---
title: "Rootfs full?"
date: 2013-05-05
forum: General Help
---

### Post by Jeff142 on 2013-05-05
On one of my servers i use for minecraft, i login and seen

rootfs          20906992 20906992         0 100% /
/dev/root       20906992 20906992         0 100% /
none             6600848      280   6600568   1% /run
none                5120        0      5120   0% /run/lock
none            33004228        0  33004228   0% /run/shm
/dev/md2        95568208 17032188  73750104  19% /home


After googleing around and spending hours trying all kinds of things all i can see is that a folder called "." is takeing up 17gb

Any help would be appreciated

---

### Post by Cheesemill on 2013-05-05
There isn't a folder called .

The . is a shortcut that means the current folder.
Can you post the output of the following commands please, it will let us know what's using all of your drive.
```
df -h
sudo du -h --max-depth=1 / | sort -hr
```

---

### Post by Jeff142 on 2013-05-05
```
Filesystem      Size  Used Avail Use% Mounted on
rootfs           20G   20G     0 100% /
/dev/root        20G   20G     0 100% /
none            6.3G  280K  6.3G   1% /run
none            5.0M     0  5.0M   0% /run/lock
none             32G     0   32G   0% /run/shm
/dev/md2         92G   17G   71G  19% /home

```


and

[http://pastebin.com/raw.php?i=gLTgBdYN](http://pastebin.com/raw.php?i=gLTgBdYN)

---

### Post by schragge on 2013-05-05
Hmm, I wonder what ```
ls -ahl /
``` and ```
sudo du -hxd1 / | sort -hr
``` would show?

---

### Post by Jeff142 on 2013-05-05
> **schragge said:**
> Hmm, I wonder what ```
ls -ahl /
``` and ```
sudo du -hxd1 /
``` would show?
```

total 104K
drwxr-xr-x  24 root root 4.0K May  4 11:24 .
drwxr-xr-x  24 root root 4.0K May  4 11:24 ..
drwxr-xr-x   2 root root 4.0K Mar 29 22:55 bin
drwxr-xr-x   3 root root 4.0K Mar 29 22:48 boot
drwxr-xr-x   3 root root 4.0K Mar 29 23:15 build
drwxr-xr-x   8 root root 4.0K May  2 16:02 dev
-rw-r--r--   1 root root    0 May  4 11:24 directorySizesInMegabytes
drwxr-xr-x  95 root root 4.0K Apr 21 18:06 etc
drwxr-xr-x   5 root root 4.0K May  4 11:10 home
drwxr-xr-x  16 root root 4.0K Mar 29 23:15 lib
drwxr-xr-x   2 root root 4.0K Mar 29 22:54 lib64
drwx------   2 root root  16K Mar 29 22:48 lost+found
drwsrwsrwt   3 root root 4.0K Apr 24  2012 media
drwxr-xr-x   2 root root 4.0K Jan 27  2012 mnt
drwxr-xr-x   2 root root 4.0K Apr 24  2012 opt
dr-xr-xr-x 209 root root    0 May  2 16:02 proc
drwx------   6 root root 4.0K May  4 11:08 root
drwxr-xr-x  15 root root  560 May  4 10:35 run
drwxr-xr-x   2 root root  12K Mar 29 22:55 sbin
drwxr-xr-x   2 root root 4.0K Mar  5  2012 selinux
drwxr-xr-x   2 root root 4.0K Apr 24  2012 srv
drwxr-xr-x  12 root root    0 May  2 16:02 sys
drwxrwxrwt   6 root root 4.0K May  5 13:25 tmp
drwxr-xr-x  10 root root 4.0K Apr 24  2012 usr
drwxr-xr-x  13 root root 4.0K May  2 16:03 var
```

---

### Post by schragge on 2013-05-05
It almost looks like your home partition was not mounted at some point, and your wrote big data to  /home on the root partition, then mounted /home over it.

---

### Post by Jeff142 on 2013-05-05
Didnt see the 2nt command

```

0    /sys
16K    /lost+found
0    /run
84K    /build
59M    /lib
4.0K    /lib64
668K    /tmp
13M    /boot
0    /proc
6.4M    /etc
56K    /dev
4.0K    /home
504M    /var
947M    /usr
4.0K    /selinux
4.0K    /opt
16M    /sbin
8.0K    /media
8.7M    /bin
27M    /root
4.0K    /mnt
4.0K    /srv
1.6G    /
```

Any idea how i could fix this?

---

### Post by matt_symes on 2013-05-05
Hi

@[**[COLOR=#000000]Jeff142[/COLOR]**]("http://ubuntuforums.org/member.php?u=1313333")

Please use code tags when copying and pasting code from a terminal into your posts. It makes it much easier to read. I have edited your two posts above and added code tags for you.

You can add code tags by highlighting the text in your post and hitting the # button above where you type the text.

I also had a disk full issue that i fixed today in saucy but you're in good hands with the existing posters so i'll let them guide you through the fix.

Kind regards

---

### Post by schragge on 2013-05-05
Reboot into recovery console, unmount /home ```
umount /home
``` and look what you have in /home:
```
du -hx /home
```
Also, have a look at [thread=2122739]this thread[/thread]. There's also a possibility of big open unlinked files. You can check for them with
```
sudo find /proc/*/fd -type f -links 0 \! -empty -ls
``` and
```
sudo lsof -K|awk -vd="$(lsblk -nro maj:min $(findmnt -no source /)|tr : ,)" '$7==d{print $8,$1,$10}'|sort -nr|head -20
```

---

### Post by Jeff142 on 2013-05-06
Oddly i reinstalled 12.04 64 bit on a soft raid 1, installed java 7 orical and lamp as i was un taring backups instantly rootfs was full.
Going to try on 13.04 and see if the same thing happens

(Sever is a OVH.com E5 with ssd's)

---

### Post by schragge on 2013-05-06
> **Jeff142 said:**
> as i was un taring backups instantly rootfs was full.As I previously said, it looks like */home* was not mounted, and you were untarring backups into the root partition. Have you tried to unmount */home* in recovery mode (see [uwiki]RecoveryMode[/uwiki])? Also, please post the output of ```
sudo mdadm -D /dev/md2
```

---

### Post by Jeff142 on 2013-05-06
My backups wear of software, not the os.

Installed 13.04 and every thing seams to be working smoothly Thanks for the time and help.

---

