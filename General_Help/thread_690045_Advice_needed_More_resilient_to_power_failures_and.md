---
title: "Advice needed: More resilient to power failures and general CF drive optimisation"
date: 2008-02-07
forum: General Help
---

### Post by SergeiFranco on 2008-02-07
Here is the story: I have built a Carpc (aka Carputer), based on VIA EPIA EN, Automotive PSU, and 4Gb CF card working as main drive (through SATA adapter). Right now the system is not very resilient: if I have power failure (say when Automotive PSU does not give enough time to system to power off) it would fsck it reboot it (or sometimes fail and will require keyboard input) and sometimes loose some files (once I lost xorg.conf, that was "fun"). Also I would like to minimize the writes (if not eliminate them entirely) like logs, swap and other stuff that liveCD seems to get away with.
I basically understand that I need to create some sort of RAM drive and mount /var/log to there as well as make it swapless somehow, I already have noatime optimisation there.
I have 512Mb of ram to play with, I will be running basic KDE + Amarok + my own kommander script as front end.

1) How to create ramdrive file system and mount all the places that can be mounted
2) I was thinking mounting most of the OS stuff read-only - how to do that (if it is possible)?
3) Which places can be mounted to ramdrive?
4) How to make system swapless without dramatic consequences?
5)I assume 512Mb of ram is enough?

I do not want to reinstall everything as it took me awhile to setup touchscreen, audio and other stuff, so I would preffer to do it on "live" system.

Thanks.

Sergei.

---

### Post by Rhubarb on 2008-02-07
To turn off your swap:
```
sudo swapoff
```

This is an easy way to get a ram disk working in ubuntu:
[http://www.vanemery.com/Linux/Ramdisk/ramdisk.html](http://www.vanemery.com/Linux/Ramdisk/ramdisk.html)
When I tried this out, ubuntu gave 16MB ram disks by default.
RAM disk size can be changed by editing your /boot/grub/menu.lst

RAM disks can be mounted anywhere.
Just make sure you've got a script that starts at startup to create + mount + change the permissions of the RAM disk accordingly.

It should be possible to turn off logs aswell, but I haven't tried this out for myself yet.

---

### Post by SergeiFranco on 2008-02-08
righto, thanks for the hint, although I used tmpfs, and added following entries to fstab:

```
tmpfs /var/run  tmpfs defaults 0 0
tmpfs /var/lock tmpfs defaults 0 0
tmpfs /var/log  tmpfs defaults 0 0
tmpfs /tmp      tmpfs defaults 0 0
```

I have removed swap partition entirely, and resized the root partition, as swap is not really needed for my application (free shows that more than 50% of memory free even with tmpfs).

also I modified powerbtn.sh scrip gutting it out of most junk and leaving the first part and last (it shuts down quicker)..

On every boot it complains about /var/log stuff that it cannot find something and that it cannot chown something, is there anyway to stop it? Also where is the log file for the stuff that is displayed on the screen (that you see when usplash is off), I was going through /var/log and could not find it....

Where do I control the level of system logging?

---

### Post by SergeiFranco on 2008-02-08
found it, syslog.conf -> commented all of it as those logs are useless to me. Got rid of missing files messages on the boot, and it seems it shaved couple of second off the boot time as well.

---

