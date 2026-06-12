---
title: "disk full problems"
date: 2007-09-17
forum: General Help
---

### Post by Screaming Monkey on 2007-09-17
I recently repartitioned my harddrive so that my linux partition is the bigger of the two (I also have windows XP).  However, after I did that, I noticed that instead of freeing up space, I now have a 98% disk full error.  And no matter what I delete as root (mainly my extra music files) it still reads as 98% full.

I have checked out the following threads and none of them have helped
[http://ubuntuforums.org/showthread.php?t=219022&highlight=full+disk+error&page=2]("http://ubuntuforums.org/showthread.php?t=219022&highlight=full+disk+error&page=2")
[http://ubuntuforums.org/showthread.php?t=523707&highlight=full+disk+error&page=2]("http://ubuntuforums.org/showthread.php?t=523707&highlight=full+disk+error&page=2")
[http://ubuntuforums.org/showthread.php?t=401761]("http://ubuntuforums.org/showthread.php?t=401761")
[http://ubuntuforums.org/showthread.php?t=108882]("http://ubuntuforums.org/showthread.php?t=108882")
[http://ubuntuforums.org/showthread.php?t=491660]("http://ubuntuforums.org/showthread.php?t=491660")

I am using Ubuntu Dapper Drake  and my df -h reads thusly:
```
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda2              24G   22G  677M  98% /
varrun                252M   92K  252M   1% /var/run
varlock               252M  4.0K  252M   1% /var/lock
udev                  252M  108K  252M   1% /dev
devshm                252M     0  252M   0% /dev/shm
lrm                   252M   18M  234M   8% /lib/modules/2.6.15-29-686/volatile
192.168.2.199:/home/dougj
                       17G  8.3G  7.4G  53% /home/dougj
```

There are some figures that I don't understand on there at all, like the last entry.  Also, when I look at the properties in nautilus of the whole filesystem I get this:
> Contents: 193012 items, totalling 12.0 GB (some contents unreadable)

Any ideas?  I've cleaned the cache, checked my logs and stuff.  The one thing that may be of use, I don't know, is that my computer backs up every night to our network backup computer.  I found recently on there a backup directory.  Have deleted that, which was over 5 GB in size and it only gave me about 400mb of room.  Any help would be greatly appreciated.

---

### Post by Screaming Monkey on 2007-09-17
re-mounted my harddrives and reconfigured my ntfs drives and so now my df -h looks like this:
```

Filesystem            Size  Used Avail Use% Mounted on
/dev/hda2              24G   22G  592M  98% /
varrun                252M   92K  252M   1% /var/run
varlock               252M  4.0K  252M   1% /var/lock
udev                  252M  108K  252M   1% /dev
devshm                252M     0  252M   0% /dev/shm
lrm                   252M   18M  234M   8% /lib/modules/2.6.15-29-686/volatile
/dev/hda1              13G   12G  1.2G  91% /media/windowbox
192.168.2.199:/home/dougj
                       17G  8.3G  7.4G  53% /home/dougj


```

---

### Post by Screaming Monkey on 2007-10-20
Apparently, for anyone who looks at this thread, Dapper has a bug in it where it empties the trash but not really.  You have to open nautilus with root priveleges and empty the .trash file there.  That's how I solved my problems.  The best way to open nautilus with root is

```
gksudo nautilus
```

---

### Post by xc3RnbFO8P on 2007-10-20
> **Screaming Monkey said:**
> Apparently, for anyone who looks at this thread, Dapper has a bug in it where it empties the trash but not really.  You have to open nautilus with root priveleges and empty the .trash file there.  That's how I solved my problems.  The best way to open nautilus with root is

```
gksudo nautilus
```

I was hoping that someone will comment on this, there has been a thread about lack of disk full warnings, but never about trash. 

anybody?

---

### Post by xc3RnbFO8P on 2007-10-20
rig@rig-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2             162G   88G   66G  57% /
varrun               1014M  116K 1014M   1% /var/run
varlock              1014M     0 1014M   0% /var/lock
procbususb           1014M  188K 1014M   1% /proc/bus/usb
udev                 1014M  188K 1014M   1% /dev
devshm               1014M     0 1014M   0% /dev/shm
lrm                  1014M   16M  998M   2% /lib/modules/2.6.20-16-386/volatile
/dev/disk/by-uuid/7AEC8F82EC8F3781
                       70G   42G   28G  61% /media/sda1
rig@rig-desktop:~$ 

I got 18.1 gb in trash.

When I empty the trash:

rig@rig-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2             162G   70G   84G  46% /
varrun               1014M  116K 1014M   1% /var/run
varlock              1014M     0 1014M   0% /var/lock
procbususb           1014M  188K 1014M   1% /proc/bus/usb
udev                 1014M  188K 1014M   1% /dev
devshm               1014M     0 1014M   0% /dev/shm
lrm                  1014M   16M  998M   2% /lib/modules/2.6.20-16-386/volatile
/dev/disk/by-uuid/7AEC8F82EC8F3781
                       70G   42G   28G  61% /media/sda1
rig@rig-desktop:~$

---

