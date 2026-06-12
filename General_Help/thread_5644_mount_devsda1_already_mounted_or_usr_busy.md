---
title: "mount: /dev/sda1 already mounted or /usr busy"
date: 2004-11-20
forum: General Help
---

### Post by Miravlix on 2004-11-20
My /usr and /var partitions refuses to mount on Hoary system.

In a recovery sessions:

mount -av
mount: proc already mounted on /proc
mount: /dev/sda1 already mounted or /usr busy
mount: /dev/sdb1 already mounted or /var busy

ls -l usr
<empty>

mount

/dev/hda1 on /
sysfs on /sys
tempfs on /tmp
usbfs on /proc/bus/usb
devpts on /dev/pts
tmpfs on /dev/shm

fdisk -l /dev/sda
disk /dev/sda1: 3240 MB, xxx bytes
24 heads, 32 sectors/track, 3090 cylinders
Units = cylinders of 2048 * 512 = 1048576 bytes
device boot start end blocks id system
/dev/sda1    1      3090 3164144 83 Linux

mount --version
mount: mount-2.12h

boot is ext3 and so is /dev/sda1 and /dev/sdb1 since I can't mount usr I'm a bit cripled in checking things any deeper. 

mount /dev/sdb1 /mnt
mount: /dev/sdb1 already mounted or /mnt busy

mkdir test
mount: /dev/sdb1 /test
mount: /dev/sdb1 already mounted or /test busy

I've used Linux for 9 years both as a hobby and profesionally, but this problem has me completely stumped. I can't for the life of me figure out why a system that has a 46 day uptime suddently dies this way on a reboot.

---

### Post by Miravlix on 2004-11-21
I found the bad guy, it was libdevmapper1.0 init script that locked the disks, a exit 0; fixed it so the system now works again after a reboot.

---

### Post by hartz on 2007-01-07
Thank you to Miravlix - this solution to your own problem over two years ago helped me with a problem with the same symptoms.

I checked out libdevmapper in synaptic and saw that it was used amongst other things by evms.

So I tried on impulse to mount /dev/evms/hda1 in stead of /dev/hda1, and it worked right away.

So now I'm investigating how to exclude a disk from evms control.

---

### Post by lmo on 2007-02-20
May also see in the logs: device-mapper: error adding target to table

This article mentions 3 solutions: [http://evms.sourceforge.net/install/kernel.html](http://evms.sourceforge.net/install/kernel.html)
The second solution was easy to do and worked for me!

Other solution which also works but is clunky, is edit /lib/modules/$(uname -r)/modules.dep and put a pound sign (#) at the beginning of each line with dm-

---

