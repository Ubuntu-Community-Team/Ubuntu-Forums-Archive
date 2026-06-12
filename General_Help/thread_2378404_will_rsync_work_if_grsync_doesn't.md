---
title: "will rsync work if grsync doesn't?"
date: 2017-11-23
forum: General Help
---

### Post by sterator on 2017-11-23
I've been using grsync for about a month with little or no issue.

last night, grsync threw an error that it couldn't find the destination volume. I can see this volume in a window at the OS level..plain as day.

if I try to do another backup using rsync, will it be able to resolve the path to the backup (provided I correctly type it)?

or, does a fail in grsync indicate something which rsync couldn't overcome..IOW, is it beyond just the GUI front end and something more serious?

thank you!

---

### Post by ajgreeny on 2017-11-23
It sounds more like a permissions problem to me for the destination folder.

Give us more info about the details of pathways to the folders and we might be able to help, and show us the rsync command that's used with Alt+R

You can also see the rsync command used in the grsync window printout if you have chosen to "show rsync output" in grsync preferences.

---

### Post by sterator on 2017-11-23
I don't understand the part about "Alt-R" ... when /where do I type that and what result ought I look for?

My path, in regular language is "Back up the documents folder onto another internal drive."  At some point, grsync ceased to "see" the other drive. It was after I'd run some terminal commands given by others here to try to figure out how much hard drive space I had remaining..there was a mismatch between what I'd seen in the computer window and an error ubuntu was throwing, "not enough space..free some space."

I'm fairly new to linux, but I have 30 years with Mac OS

---

### Post by Bashing-om on 2017-11-23
sterator; Hello;

There are several conditions to be met to perform a backup.
1) is the destination file system mounted to be available ?
```

mount

```
2) is there space available on that "mounted" volume ?
```

df -h
df -i

```
3) are both paths set correctly ?
some examples of my use case:
Mounted internal drive:
> 
rsync -av work/ /mnt/bups/work/ ; rsync -av system/ /mnt/bups/system/

backup of the /home directory to an external USB drive - where I have authorization to access the file system(s):
> 
rsync -av --exclude=".*" /home/sysop/ /media/sysop/8023-774F/storage/

where sysop is my username on this system and 8023-774F is the UUID of MY USB drive as known from the outputs of either
```

ls -al /media/<username>/
sudo blkid

```

As it works in my use case -
[INDENT][INDENT]make it work in your use case
[/INDENT][/INDENT]

---

### Post by ajgreeny on 2017-11-23
>  It was after I'd run some terminal commands given by others here to try to figure out how much hard drive space I had remaining.And what was that command? You can find previous commands used by typing the command history in terminal and scrolling up and down; if you know part of the command try ```
history | grep **word**
``` where **word** is what you remember.

It may explain why you can no longer access that destination.

---

### Post by sterator on 2017-11-23
Thank you..below are the commands I've run, immediately prior to experiencing failure with grsync:


```
df -h


sudo fdisk -l


sudo apt autoremove


du -sh /var/log
```

---

### Post by sterator on 2017-11-23
Below are the results of the first 3 terminal commands. The others, I'd not sure what to do with. I think I can make the system show me what the source and destination paths are. the last command didn't work for me (I substituted in my own actual username)


maker@bento:~$ mount
sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
udev on /dev type devtmpfs (rw,nosuid,relatime,size=8186468k,nr_inodes=2046617,mode=755)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
tmpfs on /run type tmpfs (rw,nosuid,noexec,relatime,size=1641968k,mode=755)
/dev/mapper/ubuntu--vg-root on / type ext4 (rw,relatime,errors=remount-ro,data=ordered)
securityfs on /sys/kernel/security type securityfs (rw,nosuid,nodev,noexec,relatime)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /run/lock type tmpfs (rw,nosuid,nodev,noexec,relatime,size=5120k)
tmpfs on /sys/fs/cgroup type tmpfs (ro,nosuid,nodev,noexec,mode=755)
cgroup on /sys/fs/cgroup/systemd type cgroup (rw,nosuid,nodev,noexec,relatime,xattr,release_agent=/lib/systemd/systemd-cgroups-agent,name=systemd)
pstore on /sys/fs/pstore type pstore (rw,nosuid,nodev,noexec,relatime)
efivarfs on /sys/firmware/efi/efivars type efivarfs (rw,nosuid,nodev,noexec,relatime)
cgroup on /sys/fs/cgroup/pids type cgroup (rw,nosuid,nodev,noexec,relatime,pids)
cgroup on /sys/fs/cgroup/cpu,cpuacct type cgroup (rw,nosuid,nodev,noexec,relatime,cpu,cpuacct)
cgroup on /sys/fs/cgroup/freezer type cgroup (rw,nosuid,nodev,noexec,relatime,freezer)
cgroup on /sys/fs/cgroup/net_cls,net_prio type cgroup (rw,nosuid,nodev,noexec,relatime,net_cls,net_prio)
cgroup on /sys/fs/cgroup/devices type cgroup (rw,nosuid,nodev,noexec,relatime,devices)
cgroup on /sys/fs/cgroup/memory type cgroup (rw,nosuid,nodev,noexec,relatime,memory)
cgroup on /sys/fs/cgroup/cpuset type cgroup (rw,nosuid,nodev,noexec,relatime,cpuset)
cgroup on /sys/fs/cgroup/perf_event type cgroup (rw,nosuid,nodev,noexec,relatime,perf_event)
cgroup on /sys/fs/cgroup/hugetlb type cgroup (rw,nosuid,nodev,noexec,relatime,hugetlb)
cgroup on /sys/fs/cgroup/blkio type cgroup (rw,nosuid,nodev,noexec,relatime,blkio)
systemd-1 on /proc/sys/fs/binfmt_misc type autofs (rw,relatime,fd=27,pgrp=1,timeout=0,minproto=5,maxproto=5,direct,pipe_ino=26824)
debugfs on /sys/kernel/debug type debugfs (rw,relatime)
hugetlbfs on /dev/hugepages type hugetlbfs (rw,relatime)
mqueue on /dev/mqueue type mqueue (rw,relatime)
tracefs on /sys/kernel/debug/tracing type tracefs (rw,relatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw,relatime)
/dev/sda1 on /boot/efi type vfat (rw,relatime,fmask=0077,dmask=0077,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
tmpfs on /run/user/1000 type tmpfs (rw,nosuid,nodev,relatime,size=1641964k,mode=700,uid=1000,gid=1000)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,relatime,user_id=1000,group_id=1000)
/dev/sdb on /media/maker/Bento_Backup type ext4 (rw,nosuid,nodev,relatime,data=ordered,uhelper=udisks2)

====================================================================
maker@bento:~$ df -h
Filesystem                   Size  Used Avail Use% Mounted on
udev                         7.9G     0  7.9G   0% /dev
tmpfs                        1.6G  9.9M  1.6G   1% /run
/dev/mapper/ubuntu--vg-root  442G  353G   67G  85% /
tmpfs                        7.9G   28M  7.9G   1% /dev/shm
tmpfs                        5.0M  4.0K  5.0M   1% /run/lock
tmpfs                        7.9G     0  7.9G   0% /sys/fs/cgroup
/dev/sda1                    511M  3.4M  508M   1% /boot/efi
tmpfs                        1.6G  120K  1.6G   1% /run/user/1000
/dev/sdb                     458G  234G  201G  54% /media/maker/Bento_Backup



maker@bento:~$ df -i
Filesystem                    Inodes  IUsed    IFree IUse% Mounted on
udev                         2046617    632  2045985    1% /dev
tmpfs                        2052455    941  2051514    1% /run
/dev/mapper/ubuntu--vg-root 29450240 887452 28562788    4% /
tmpfs                        2052455     30  2052425    1% /dev/shm
tmpfs                        2052455      6  2052449    1% /run/lock
tmpfs                        2052455     16  2052439    1% /sys/fs/cgroup
/dev/sda1                          0      0        0     - /boot/efi
tmpfs                        2052455     50  2052405    1% /run/user/1000
/dev/sdb                    30531584 486511 30045073    2% /media/maker/Bento_Backup

---

### Post by Bashing-om on 2017-11-23
sterator; Hey ...

Paths my friend .. paths ..
Is this the target to backup too ?
> 
/dev/sdb on /media/maker/Bento_Backup


And what is it that you want to backup ? And we determine the path for the source .
Be aware I have no experience with encryption . This may well be a learning experience for me also .

[INDENT][INDENT]together we can
[/INDENT][/INDENT]

---

### Post by sterator on 2017-11-23
> **Bashing-om said:**
> sterator; Hey ...

Paths my friend .. paths ..
Is this the target to backup too ?


And what is it that you want to backup ? And we determine the path for the source .
Be aware I have no experience with encryption . This may well be a learning experience for me also .[INDENT][INDENT]together we can
[/INDENT]
[/INDENT]


No.."Bento_Backup" is my destination..it's an SSD whose sole purpose is to be the backup volume. It's the same make and size as the boot volume.

I get that this: 
/dev/sdb on /media/maker/Bento_Backup

...is a path, but I don't know my beans about paths well enough to say, yep, that's it. I'd need to rely on an OS Tool which, when right-clicked would "Copy path" or "Reveal path" or some such.

"maker" is me, and "maker's" password is what unlocks the magical kingdom whenever I'm asked for admin credentials.

"Bento" is the name of my machine, so in my nomenclature it's a backup of the stuff that's on that machine. "Bento" as in "Bento Box"...one of my faves! ;-)

like, I'm confused that that path doesn't begin with "home" but that "maker" is in there makes sense to me..

thank you

---

### Post by Bashing-om on 2017-11-23
sterator; K -


File system: have a read.
[https://www.freedesktop.org/software/systemd/man/file-hierarchy.html](https://www.freedesktop.org/software/systemd/man/file-hierarchy.html)

so, don your learning cap, and I see if I have a dunce cap on :)
so - you want to copy what to where - as a backup ?

all ya got to do is tell the system what to do .
then again .. there is :
> 
sysop@x1604:~$ sudo apt update
[sudo] password for sysop: 
You can't come in. Our tiger has got flu
[sudo] password for sysop:


[INDENT][/INDENT]-all in the care and feeding of your 'buntu-

---

### Post by sterator on 2017-11-23
is that stuff an actual terminal command?

I think I'm the one with the dunce cap..

---

### Post by Bashing-om on 2017-11-23
sterator;; nooooo ...

Just my feeble attempt at some humor to lend a bit of levity to a serious consideration.

one has to have sme understanding, in order to make progress - know the file system.

-it is doable-

---

### Post by JKyleOKC on 2017-11-23
Just jumping in here, but I see a couple of references to "/dev/sdb" with NO partition number on it -- which would mean the entire drive, which by definition could not be backed up. Only the partitions on it can be mounted or accessed. I suspect that missing partition number, most likely a "1", is a typo causing the problem.

---

### Post by sterator on 2017-11-23
'k..thot so.

I have used rsync on OS X with great success...I kept a text document with the path structure so that I didn't have to memorize it.

---

### Post by sterator on 2017-11-23
> **JKyleOKC said:**
> Just jumping in here, but I see a couple of references to "/dev/sdb" with NO partition number on it -- which would mean the entire drive, which by definition could not be backed up. Only the partitions on it can be mounted or accessed. I suspect that missing partition number, most likely a "1", is a typo causing the problem.

The way I set up grsync was "back up Documents on boot drive to the other volume"

"other volume" being reserved entirely for backing up. Are you saying that that is improper practice?

---

