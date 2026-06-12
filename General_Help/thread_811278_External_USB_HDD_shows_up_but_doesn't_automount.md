---
title: "External USB HDD shows up but doesn't automount"
date: 2008-05-29
forum: General Help
---

### Post by jonno on 2008-05-29
I'm running a Mythbuntu 8.04 install and have my recordings stored on an external HDD permanently turned on and connected via USB.

The drive shows at boot as an icon on the desktop as "750G Volume". Also the drive shows up as sdb when I do sudo fdisk -l. However as far as I can tell it is not actually mounted anywhere. If try to cd /media/disk there is no such directory.
I can get it to mount easily by double-clicking on the icon or by browsing with Thunar to the 750G Volume. The contents then show up and I can cd to /media/disk.

If I turn off the USB external drive and restart it while the system is booted then it does mount the drive.

Any ideas how to get the drive to mount on boot? The problem is at the moment I have to restart the drive and then restart the Mythbackend every time I reboot the system (like when there's a powercut).

Also as you can tell I'm pretty green. What command will tell me where all the drives are mounted? fdisk -l didn't seem to contain this. Do I need to look at /etc/fdisk? Will this contain information about automounted drives?

Thanks in advance.

---

### Post by VMC on 2008-05-29
'cat /etc/fstab' will show you what shold be mounted. Typing mount inside a terminal window will tell what is mounted. show us the output of 'fstab' for starters.

---

### Post by jonno on 2008-05-29
Thanks for the quick reply.

> jonno@jonno-mythbuntu:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=8a66f906-8ce0-494f-822e-2aff1b61e501 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=80c58744-4142-48c4-b723-230599ae7618 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

> jonno@jonno-mythbuntu:~$ mount
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-16-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)

However if I restart the drive while the system is booted I get:
> jonno@jonno-mythbuntu:~$ mount
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-16-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
[COLOR="Red"]/dev/sdb1 on /media/disk type xfs (rw,nosuid,nodev,uhelper=hal)[/COLOR]


---

### Post by jonno on 2008-05-29
FYI I have "Mount Removable Drives When Hot-Plugged" checked in the Thunar Removable Drives and Media manager.

---

### Post by jonno on 2008-05-29
Also I just checked on my Ubuntu 8.04 desktop system which has 3 external USB drives plugged into it and they all mount on boot. So my guess is that there is some difference when Thunar is in control of removable drives instead of Nautilus.
I will try plugging the drive into my dektop later this evening to see if it automounts on boot in a different system.

I suppose I could try to manually alter /ect/fstab but I know that can be dangerous and frankly I'd rather have it be done automatically.

---

### Post by jonno on 2008-05-29
Well I did some messing around and chose to try editing /etc/fstab. Seems to be working with this:
/dev/sdb1       /media/disk xfs auto,rw,nosuid,nodev
Not sure about the options. I basically copied them from what the Thunar's Removable Drive tool did. Please let me know if you think I should modify this.

---

