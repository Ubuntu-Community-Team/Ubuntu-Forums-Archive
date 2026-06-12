---
title: "disk space confusion"
date: 2007-10-06
forum: General Help
---

### Post by ozzzzysh on 2007-10-06
ok i have feisty and when i go to my home directory it says i have 2.2 GB space remaining in the bottom corner of file browser but when I goto /var or anywhere else besides anything in my /home directory it says I have 10.1 GB remaining? Ive been learning linux for about 2 months now but ive never figured out why it does this?is something wrong or is it normal? BTW feisty was installed with wubi in a 20GB "virtual" drive.

---

### Post by atlfalcons866 on 2007-10-06
if your file system is ext3 you lost 5% of it. Ext3 reserves 5% of the space for the inodes

---

### Post by taurus on 2007-10-07
Do you have a separate /home partition?  What's the output of this command from a terminal?

```
df -h
```

---

### Post by atlfalcons866 on 2007-10-07
does his problem have anything to do with ext3?

---

### Post by taurus on 2007-10-07
> **atlfalcons866 said:**
> does his problem have anything to do with ext3?

I bet he has a separate /home partition.

---

### Post by ozzzzysh on 2007-10-07
> **taurus said:**
> Do you have a separate /home partition?  What's the output of this command from a terminal?

```
df -h
```

This is what i got

Filesystem            Size  Used Avail Use% Mounted on
/media/host/wubi/disks/system.virtual.disk
                       14G  3.0G   11G  23% /
varrun                982M  100K  982M   1% /var/run
varlock               982M     0  982M   0% /var/lock
procbususb            982M  104K  982M   1% /proc/bus/usb
udev                  982M  104K  982M   1% /dev
devshm                982M     0  982M   0% /dev/shm
lrm                   982M   15M  967M   2% /lib/modules/2.6.20-15-lowlatency/volatile
/dev/sda1             128G  124G  4.8G  97% /media/LOL
/dev/sda2              22G  4.5G   17G  22% /media/LOL2
/media/host/wubi/disks/home.virtual.disk
                      2.8G  394M  2.3G  15% /home

BTW LOL and LOL2 are my hdds lol

---

### Post by taurus on 2007-10-07
> **ozzzzysh said:**
> This is what i got

Filesystem            Size  Used Avail Use% Mounted on
/media/host/wubi/disks/system.virtual.disk
                       14G  3.0G   11G  23% /
varrun                982M  100K  982M   1% /var/run
varlock               982M     0  982M   0% /var/lock
procbususb            982M  104K  982M   1% /proc/bus/usb
udev                  982M  104K  982M   1% /dev
devshm                982M     0  982M   0% /dev/shm
lrm                   982M   15M  967M   2% /lib/modules/2.6.20-15-lowlatency/volatile
/dev/sda1             128G  124G  4.8G  97% /media/LOL
/dev/sda2              22G  4.5G   17G  22% /media/LOL2
**[COLOR="Blue"]/media/host/wubi/disks/home.virtual.disk   2.8G  394M  2.3G  15% /home[/COLOR]**

There you go.  You only have 2.8GB for /home.

---

### Post by ozzzzysh on 2007-10-07
can i change that? i used wubi and it kinda automates everything so...

---

### Post by taurus on 2007-10-07
Maybe you want to browse these, [http://ubuntuforums.org/forumdisplay.php?f=234](http://ubuntuforums.org/forumdisplay.php?f=234).

---

