---
title: "Error while mounting ntfs drive."
date: 2013-06-12
forum: General Help
---

### Post by Crypdos on 2013-06-12
Today I started getting this error on boot

"Error while mounting /media/hdd1"   (or /media/mediahdd. mediahdd is the label of the harddrive, hdd1 is the mountpoint I created myself)

I can press S to skip or press M to go into manual recovery
When I press S it just boots up normally, and I see that the hdd is mounted, but I can't write to it or anything. So it didn't boot using my fstab settings. The hdd is a ntfs drive I use for some data and stuff I added on windows.

**The weird thing: when I unmount the device and remount it again (after booting), it's working as it should!** So when I
 ```
sudo umount /media/hdd1
sudo mount /dev/sdb1
```
It works how I want it to, it uses the fstab settings and mounts correctly on /media/hdd1 with write access. (not under /media/mediahdd - which is the label)

It was working perfectly until today. I was messing with lightdm and added a custom session under /././xsessions when this error started happening.

I don't know why it doesn't just mount as specified in fstab while booting, because when manually remounting it does work.

/etc/fstab
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc    /proc    proc    nodev,noexec,nosuid    0    0
tmpfs    /tmp    tmpfs    defaults,noatime,mode=1777    0    0
#Entry for /dev/sda2 :
UUID=5a1e8c36-abdd-496a-8421-e6486df36fc7    /    ext4    noatime,discard,errors=remount-ro    0    1
#Entry for /dev/sda3 :
UUID=088cb6f0-84f9-4246-98ae-5d3662d2d8ec    /home    ext4    noatime,discard,defaults    0    2
#Entry for /dev/sda1 :
UUID=15dad974-4171-4753-bd9c-f6610589368f    none    swap    sw    0    0
#mediahdd on mountpoint hdd1
UUID=3AB87D34B87CF02D /media/hdd1 ntfs defaults,nls=utf8,umask=000,uid=1000,windows_names 0 0


```

/var/log/boot.log 

```

fsck from util-linux 2.20.1 
fsck from util-linux 2.20.1 
lircd-0.9.0[860]: lircd(default) ready, using /var/run/lirc/lircd  
/dev/sda2: clean, 230248/2444624 files, 1417549/9765632 blocks 
/dev/sda3: clean, 9139/6840320 files, 621950/27353856 blocks 
Mount is denied because the NTFS volume is already exclusively opened. 
The volume may be already mounted, or another software may use it which 
could be identified for example by the help of the 'fuser' command. 
mountall: mount /media/hdd1 [897] terminated with status 16 
mountall: Filesystem could not be mounted: /media/hdd1 
Skipping /media/hdd1 at user request

```

---

### Post by SeijiSensei on 2013-06-12
If the machine has Windows installed, or you can access the drive in some other manner from Windows. I *strongly* suggest running chkdsk on the NTFS filesystem and see whether it reports any errors.

---

### Post by Crypdos on 2013-06-13
I will try that when I'm home. But I really doubt it, the HDD is barely 1 month old. It's a western digital 1,5TB one.

Meanwhile, any other suggestions?

---

### Post by Mark Phelps on 2013-06-13
I had three WD drives fail me last year, one of which was only a few months old.  So, run the CHKDSK to confirm there are no filesystem errors.  New WD drives fail, too.

---

### Post by Crypdos on 2013-06-13
Ok, I ran chkdsk for a ridiculous amount of hours and it found no problems + 0kb in bad sectors.

It must be something else.

---

### Post by Crypdos on 2013-06-14
Sorry, afraid I must bump :)

---

### Post by carboi82 on 2013-06-14
I remember two or three years ago there being issues with mount rejecting nls=XXXX statements.  Have you tried it without that option? Or alternatively just add a bash script to mount the drive for you after login...

---

### Post by Crypdos on 2013-06-14
I tried running it with just "defaults,windows_names" as options. Same error.
If possible, I would like to get it working with fstab.
Thanks for the help though!

---

### Post by carboi82 on 2013-06-14
Have you tried reinstalling ntfs-3g?

```
[COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get --reinstall install ntfs-3g[/FONT][/COLOR]
```

---

### Post by oldfred on 2013-06-15
Part of the reason I do not like very large NTFS data partitions is how long chkdsk can take. And you cannot use fsck on NTFS formatted partitions.

Only if mounted by Nautilus and  not already mounted, would it mount in /media using the label.

Is UUID correct?

Ubuntu changed to use sdXY for all drives, but before hdXY was for some drives. Since your mount point is close to an old standard reserved mount, I wonder if that could be part of the issue. I might just try something different. And/or mount in /mnt not /media.

---

### Post by Crypdos on 2013-06-15
After deleting the old mountpoint and specifying a new one, and reinstalling ntfs-3g it now works again. Weird.

Maybe the old mountpoint was instead conflicting with hdXY, or maybe it was ntfs-3g? Haha, anyways I'm glad it works now.

Thanks for the help.

---

### Post by Crypdos on 2013-06-15
Too soon to cheer ...

After 3 reboots it is now happening again, error: error while mounting /media/mediadrive.
This is the new mountpoint I made...

---

### Post by oldfred on 2013-06-15
Gparted will often have a yelllow or red icon on a partition with issues. Clicking (right click?) on icon may tell why it has issues. Often with NTFS it just suggests chkdsk.

From Disk Utility or Disks click on drive and on right side is Smart Data info on drive. Is it showing any issues. New drive should not but even new drives sometimes have issues.

---

### Post by Crypdos on 2013-06-15
Gparted is showing a green icon. Smart-Data says "drive is healthy". And chkdsk yesterday reported no errors too.
I don't think the drive or the filesystem is faulty. I think the problem lies purely in the booting process. When I mount the drive in a gnome terminal, there are no problems at all - it uses the specified fstab mountpoint and works correctly.

**Could it be that the drive gets accessed by something before fstab can mount it? **
from the boot.log:

```
Mount is denied because the NTFS volume is already exclusively opened.  The volume may be already mounted, or another software may use it which  could be identified for example by the help of the 'fuser' command.  
mountall: mount /media/hdd1 [897] terminated with status 16  
mountall: Filesystem could not be mounted: /media/hdd1 
```

I pressed M at the errorscreen (manual recovery) and ran "fuser -vm /dev/sdb1" and "mount" and recorded the output:

```

root@Media-PC:~# fuser -vm /dev/sdb1
                     USER        PID ACCESS COMMAND
/dev/sdb1:           root     kernel swap  /dev/sda1
                     root     kernel mount /dev
                     root          1 F.... init
                     root        396 F.... upstart-udev-br
                     root        398 F.... udevd
                     root        575 F.... udevd
                     root        580 F.... udevd
                     root        806 F.... upstart-socket-
                     root        878 F.... lircd
                     root        916 F.... mount.ntfs
                     root        924 F.... sh
                     root        925 F.... initctl
                     root        933 F.... sh
                     root        934 F.... bash
                     root        944 F.... script
                     root        945 F.... script
root@Media-PC:~# mount
/dev/sda2 on / type ext4 (rw,noatime,discard,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /tmp type tmpfs (rw,noatime,mode=1777)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
/dev/sda3 on /home type ext4 (rw,noatime,discard)
/dev/sdb1 on /media/mediahdd type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
root@Media-PC:~# exit
exit

```

---

### Post by oldfred on 2013-06-15
Your error message is from your old mount, where is that from?

I thought this was not now used:
 mountall: Filesystem could not be mounted: /media/hdd1

What is mounted:

   /dev/sdb1 on /media/mediahdd type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)

---

### Post by Crypdos on 2013-06-15
Yes, this was the old mountpoint. Sorry I copied the error message from my opening post.

The fuser and mount output are recent. It seems that the HDD is already mounted at that point (during manual recovery - which is before gnome)?

---

### Post by Crypdos on 2013-06-16
bump

---

### Post by oldfred on 2013-06-16
Were you not mounting hdd1 with fstab but with something else like a script or udisks? 
Or is entry in fstab still there for the hdd1?

It seems like you are still trying to mount the same drive twice which is not allowed.

---

### Post by Crypdos on 2013-06-16
Yes, that's exactly what I'm saying. Something accesses the drive before fstab does. At least that's what I'm thinking right now.

I didn't manually make a script to do this, maybe it is a program I installed that I forgot about. I removed all entries from fstab now.

---

### Post by Crypdos on 2013-06-17
When I remove the line from fstab completely, it still gets mounted during boot. It is then mounted with the label's name under /media/mediahdd. The label is mediahdd. When mounted this way I do not have write access. 

So something other than fstab mounts the drive during boot. Even _before_ fstab, because fstab reports the error "Mount is denied because the NTFS volume is already exclusively opened. The volume may be already mounted, or another software may use it which could be identified for example by the help of the 'fuser' command."

WHAT MOUNTS MY PROGRAM BEFORE FSTAB DOES?

---

### Post by oldfred on 2013-06-17
If you click on a partition that is not mounted with Nautilus then it will auto mount it with defaults and will use the label if you have one. 
So it may not be mounted before fstab?

As soon as you boot run this:
mount
 cat /etc/mtab



And that should show what is mounted before you manually mount anything with Nautilus.

---

### Post by Crypdos on 2013-06-17
Yes, I'm aware of that. I don't mount the drive by clicking on it in nautilus - it is already mounted.

mount
cat /etc/mtab
```

tom@Media-PC:~$ mount
/dev/sda2 on / type ext4 (rw,noatime,discard,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /tmp type tmpfs (rw,noatime,mode=1777)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
/dev/sda3 on /home type ext4 (rw,noatime,discard)
/dev/sdb1 on /media/mediahdd type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
gvfs-fuse-daemon on /home/tom/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=tom)
tom@Media-PC:~$ cat /etc/mtab
/dev/sda2 / ext4 rw,noatime,discard,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
none /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
udev /dev devtmpfs rw,mode=0755 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
tmpfs /tmp tmpfs rw,noatime,mode=1777 0 0
tmpfs /run tmpfs rw,noexec,nosuid,size=10%,mode=0755 0 0
none /run/lock tmpfs rw,noexec,nosuid,nodev,size=5242880 0 0
none /run/shm tmpfs rw,nosuid,nodev 0 0
/dev/sda3 /home ext4 rw,noatime,discard 0 0
/dev/sdb1 /media/mediahdd fuseblk rw,nosuid,nodev,allow_other,default_permissions,blksize=4096 0 0
gvfs-fuse-daemon /home/tom/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=tom 0 0
tom@Media-PC:~$ 

```

This is after boot, with no fstab entry!

---

### Post by Morbius1 on 2013-06-17
Anything listed here that might automount the partition:
```
ls -l $HOME/.config/autostart
```
Is this an external usb "drive" ?

---

### Post by Crypdos on 2013-06-17
```

tom@Media-PC:~$ ls -l $HOME/.config/autostart
total 8
-rw-rw-r-- 1 tom tom 212 Jun 17 12:03 qbittorrent.desktop
-rw-rw-r-- 1 tom tom 165 Jun  7 18:34 xbmc.desktop

```
These are my 2 startup applications, xbmc is disabled though.

The drive is a SATA drive.

---

### Post by oldfred on 2013-06-17
Repost fstab

       cat /etc/fstab

---

### Post by Crypdos on 2013-06-17
```

tom@Media-PC:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc    /proc    proc    nodev,noexec,nosuid    0    0
tmpfs    /tmp    tmpfs    defaults,noatime,mode=1777    0    0
#Entry for /dev/sda2 :
UUID=5a1e8c36-abdd-496a-8421-e6486df36fc7    /    ext4    noatime,discard,errors=remount-ro    0    1
#Entry for /dev/sda3 :
UUID=088cb6f0-84f9-4246-98ae-5d3662d2d8ec    /home    ext4    noatime,discard,defaults    0    2
#Entry for /dev/sda1 :
UUID=15dad974-4171-4753-bd9c-f6610589368f    none    swap    sw    0    0




```

---

### Post by oldfred on 2013-06-17
What you have happening is not possible.  Or perhaps Morbius1 has some other ideas.

---

### Post by Crypdos on 2013-06-18
Not possible? But it's really happening. I'm not pulling a show here ... this is actually really frustrating because I want to move on with this and complete this project.

Tell me if I need to post logs or anything.

---

### Post by Morbius1 on 2013-06-18
> **oldfred said:**
> What you have happening is not possible.  Or perhaps Morbius1 has some other ideas.
The only possibilities I can think of have pretty much been covered already:

(1) A udisks mount in startup applications.
(2) I don't think Ubuntu is capable of this anymore but if you could save your session at shutdown I suppose it would come back mounted at login.
(3) User created his own udev rule but that would have been such an arduous endeavor a person would remember doing it.

Having said that I have come across this phenomenon once before: [http://ubuntuforums.org/showthread.php?t=2143849](http://ubuntuforums.org/showthread.php?t=2143849)

That user insisted there was an option somewhere in System Settings in 12.10:
> I've noticed that System Settings has an entry which sets this partition  as "Automount on Login", but it appears there is no way to set the  default permissions.
Maybe someone else can find it but there is no "Automount on Login" on my system. He stated he's using KDE installed on top of Ububntu so maybe it's a KDE thing. In any event as you can see from the link I couldn't answer that one either.

---

### Post by Crypdos on 2013-06-18
[COLOR=#000000](2) I don't think Ubuntu is capable of this anymore but if you could save your session at shutdown I suppose it would come back mounted at login.[/COLOR][COLOR=#000000]
I unmount the drive before rebooting (or poweroff), and on the next boot it is mounted again. (with no fstab entry)
[/COLOR][COLOR=#000000](3) User created his own udev rule but that would have been such an arduous endeavor a person would remember doing it.[/COLOR][COLOR=#000000]
I don't even know what that is :).

My system settings doesn't have the "Automount on Login" option. I'm running only 12.04 Ubuntu, no second OS.

So ... what do we do? Surely there must be a way to find out how it gets mounted via logs or so? Keep in mind that I'm not the most experienced user, I dont have too much experience yet with linux. That being said I also didn't change too much in my installation. So my system shouldn't be too far from standard.




[/COLOR]

---

### Post by oldfred on 2013-06-18
I have no idea what log file to review, there are many. And your issue may be somewhere we would not normally look anyway.
I normally look at dmesg which is the same as what your see when booting if you do not use quiet splash and it is more driver related.
I might just start reviewing all recent logs and look for something related.

What gui are you using, I use fallback or gnome-panel so may not see same info.

---

### Post by Crypdos on 2013-06-18
I'm using the default 12.04 gui, which I think is ubuntu-desktop? I'm not sure. Havent really messed with gui's yet.
I might install gnome-panel, it looks nice from what I can see.
Should I check dmesg? I don't see a lot while booting.

---

### Post by oldfred on 2013-06-18
The default is the Unity with the icons on the left side. My monitor is 4:3 so I have more space on top & bottom so the old layout works better, plus oldfred is getting to the point where change is more difficult.

I might look at dmesg but that may be before whatever is mounting your partition. Then just look for any log files with time stamps for most recent boot and see if anything applies?

---

### Post by Crypdos on 2013-06-20
Do I need to post dmesg? Is this a logfile?

Meanwhile I've been looking for another solution, since we are obviously not getting any further with this problem.
I modified my /etc/rc.local file to include sudo umount and sudo mount. Is this a good way of going about it? Or is there a better way?
```

sudo umount /dev/sdb1
sudo mount -U 3AB87D34B87CF02D /media/mediadrive
exit 0

```

Is there any way I can add boot options like in fstab via sudo mount? Options like default,windows_names etc etc?

---

