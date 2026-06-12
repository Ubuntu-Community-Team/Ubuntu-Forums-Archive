---
title: "Trouble with fstab and ntfs partition, Help Appreciated!"
date: 2013-12-10
forum: General Help
---

### Post by dave2001 on 2013-12-10
Background: I just upgraded to 13.10 from 12.04 on my Thinkpad-T500 (a fresh installation actually). I installed a base system using the minimal iso, and then installed the kde-plasma-desktop and a few other needed packages from the official repos. This computer dual boots with a Windows 7 installation.

Problem: I attempted to edit /etc/fstab like i have with previous versions, in order to have the two windows system partitions "hidden" and left alone by ubuntu, and my ntfs data partition to be mounted so that i can then integrate it with symbolic links to my /home folders. However, when i attempt to reboot with the new fstab, i get a bsod. In order to fix the problem i had to boot on a live-cd and edit my fstab back to the way it was previously (with no entries for the ntfs partitions.)

I confirmed that ntfs-3g is installed using ```
apt-cache policy ntfs-3g
``` I also created the directories /.WinSysRes /.Windows7 and /.Data

here is the edited fstab that is not working for some reason. Is it possible I'm missing some package that is needed for mounting the partitions like this, since i did a base system install rather than  using the full kubuntu install?

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda5 during installation
UUID=952cfb84-2120-482c-aee8-528f6a686bb1 /               ext4    noatime,errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=16777e04-0555-4564-b928-313f62ced171 none            swap    sw              0       0
# Added by me for ntfs partitions
UUID=5C4861E74861BFFE /.WinSysRes ntfs-3g defaults,noauto,umask=777    0    0
UUID=241A97F71A97C468 /.Windows7 ntfs-3g defualts,noauto,umask=777    0    0
UUID=78C00125C000EAE8 /.Data ntfs-3g defualts,user,umask=000,locale=en_US.utf8,windows_names    0    0

```

---

### Post by steeldriver on 2013-12-10
def[COLOR=#ff0000]**ua**[/COLOR]lts

---

### Post by dave2001 on 2013-12-10
haha! thanks, can't believe i overlooked that.  Unfortunately fixing those two typos didn't resolve the problem.

---

### Post by drmrgd on 2013-12-10
Can you tease out an error by manually mounting them one at a time from the commandline?  Maybe you'll get something more informative than a BSOD to tell you what's not right.  I could be wrong, but I would guess that even a base install should have what you need to mount NTFS drives.

---

### Post by steeldriver on 2013-12-10
What exactly do you mean by "bsod"? I'm only familiar with that term in the context of Microsoft - for *buntu, you should at least get a 'drive missing' message with options to skip / manually mount

Do you see anything in dmesg after the failures? Since 2 of the 3 are 'noauto' it shouldn't even be trying to mount them at boot time, so I'd suspect the 3rd (Data) partition first.

---

### Post by dave2001 on 2013-12-11
> **steeldriver said:**
> What exactly do you mean by "bsod"? I'm only familiar with that term in the context of Microsoft - for *buntu, you should at least get a 'drive missing' message with options to skip / manually mount 

Thanks for the reply!
Sorry for being vague, you're right it's not a total "black screen of death".. but it is close. I get a black screen with a cursor.. no tty promt or anything.. JUST a cursor. However it won't accept any input, typing on the keyboard only produces non-sense characters like "[^]&

> **steeldriver said:**
> 
Do you see anything in dmesg after the failures? Since 2 of the 3 are 'noauto' it shouldn't even be trying to mount them at boot time, so I'd suspect the 3rd (Data) partition first.

I have not looked in dmesg yet, but i will, and post if there's anything unusual (or that I'm not sure about).

---

### Post by dave2001 on 2014-01-19
So I found a workaround for the problem, and will post it for anyone else with the same problem.

Instead of identifying the partition by the newly "preferred" UUID method, use the old descriptor method instead; /dev/sdXY  (where X is the letter of the drive and Y the number identifying the partition, eg. /dev/sda1). 

Changing my fstab entry to this worked perfectly:
```
dev/sda3 /.Data ntfs-3g defaults,user,umask=000,locale=en_US.utf8,windows_names 0 0 
```

It IS the manual entries in fstab causing the "black screen of death" on boot.. even using only the first manually entered line (which has a noauto option!) as the ONLY changing variable will reproduce the behavior every time.

So, this problem is related to UUID and fstab implementation during boot, the issue is also something new to 13.10 (at least in comparison to 12.04, I haven't tried the intermediates).

Does anyone think this is a bug? Should I see about posting on launchpad?

---

### Post by bab1 on 2014-01-19
> **dave2001 said:**
> So I found a workaround for the problem, and will post it for anyone else with the same problem.

Instead of identifying the partition by the newly "preferred" UUID method, use the old descriptor method instead; /dev/sdXY  (where X is the letter of the drive and Y the number identifying the partition, eg. /dev/sda1). 

Changing my fstab entry to this worked perfectly:
```
dev/sda3 /.Data ntfs-3g defaults,user,umask=000,locale=en_US.utf8,windows_names 0 0 
```

It IS the manual entries in fstab causing the "black screen of death" on boot.. even using only the first manually entered line (which has a noauto option!) as the ONLY changing variable will reproduce the behavior every time.

So, this problem is related to UUID and fstab implementation during boot, the issue is also something new to 13.10 (at least in comparison to 12.04, I haven't tried the intermediates).

Does anyone think this is a bug? Should I see about posting on launchpad?

I doubt this is a UUID bug.  Post the output of ```
sudo blkid -c /dev/null -o list
```

---

### Post by dave2001 on 2014-01-21
This is the output of requested command 

```
/dev/sda1      ntfs    System Reserved (not mounted) 5C4861E74861BFFE
/dev/sda2      ntfs             (not mounted)      241A97F71A97C468
/dev/sda3      ntfs    Data     /.Data             78C00125C000EAE8
/dev/sda5      ext4    SaucySal /                  b6e86e27-5720-435b-978e-6ccfbb212cba
/dev/mapper/cryptswap1
               swap             <swap>             13b8bf86-0ac1-4113-9e00-aff842845f12

```

If it's not a UUID bug, I think it's a bug in something. If it's not a bug in anything, then I'd have to say that imho it's poorly implemented functionality.

---

