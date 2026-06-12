---
title: "[SOLVED] Running out of disk space"
date: 2008-03-27
forum: General Help
---

### Post by stevoo on 2008-03-27
Well it seems i runned out of disk space

I used to have 14 gb and run on those out of 27 that i have available.

But for some time they end up getting less and less.

Today i unzipped something directly from my hard disk into an external disk and all my hard disk runned up. 
Either that or i was downloading a large file into another partition ( win partition ) and dried up all my space.

I am search of some missing Gb, so please some help here

sudo du -ks /* | sort -n
0       /cdrom
0       /initrd.img
0       /initrd.img.old
0       /proc
0       /sys
0       /vmlinuz
0       /vmlinuz.old
4       /EULA.txt
4       /initrd
4       /mnt
4       /srv
16      /GPL.txt
16      /lost+found
108     /dev
2660    /tmp
4776    /bin
6200    /sbin
6432    /root
12976   /etc
34536   /boot
197004  /opt
273488  /lib
603944  /var
4442636 /usr


df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6              28G   27G  476M  99% /
varrun               1010M   96K 1010M   1% /var/run
varlock              1010M     0 1010M   0% /var/lock
udev                 1010M   92K 1010M   1% /dev
devshm               1010M     0 1010M   0% /dev/shm
lrm                  1010M   34M  976M   4% /lib/modules/2.6.22-14-generic/volatile
/dev/sda5             2.1G  4.0K  2.1G   1% /media/sda1
/dev/sda2              44G   36G  7.5G  83% /media/sda2
/dev/sda5             2.1G  4.0K  2.1G   1% /media/sda5


I am interested in my sda6. 

Anyone has any idea where Ubuntu has hidden those extra gb  ?

------------------

It seems that wine kind of kept some hiden data from me. After some poking i delete 8 gb of video files and freed a lot of space

---

### Post by Rocket2DMn on 2008-03-27
You can try clearing out your apt cache with
```
sudo apt-get clean
```
Make sure your trash is empty, too.  Those are always the best starts.  Do that and we'll see where we are.

EDIT: Oh, you solved it, sorry.  Well, good advice anyway.

---

### Post by dcstar on 2008-03-27
> **stevoo said:**
> Well it seems i runned out of disk space

I used to have 14 gb and run on those out of 27 that i have available.

But for some time they end up getting less and less.

Today i unzipped something directly from my hard disk into an external disk and all my hard disk runned up. 
.........
It seems that wine kind of kept some hiden data from me. After some poking i delete 8 gb of video files and freed a lot of space

That's what happens when you don't have a separate /home partition - user downloads stuff up your root filesystem.

---

### Post by dcstar on 2008-03-27
> **Rocket2DMn said:**
> 
..........
EDIT: Oh, you solved it, sorry.  Well, good advice anyway.

Pity he didn't use the forum tools to mark the thread as solved.

---

### Post by Rocket2DMn on 2008-03-27
> **dcstar said:**
> Pity he didn't use the forum tools to mark the thread as solved.

+1
See my sig, too :)

---

