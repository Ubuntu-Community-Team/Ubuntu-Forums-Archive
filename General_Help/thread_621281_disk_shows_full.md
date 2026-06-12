---
title: "disk shows full"
date: 2007-11-23
forum: General Help
---

### Post by zdwc01 on 2007-11-23
GG 7.10 Kubuntu  diskusage shows / 142G  9% on /dev/sda3 Gparted and others show 144.31GB with 142.04GB used. How can I recover/or correct for the 120GB difference?

---

### Post by john_spiral on 2007-11-23
are you sure your maths is correct?

---

### Post by mellowd on 2007-11-23
Looks like 2GB difference

---

### Post by jpkotta on 2007-11-23
Your question is hard to understand.  I think you're saying that one tool says your disk is 9% full, and gparted says it's 98% full.  If that's the case, gparted and a filesystem usage tool measure different things.  gparted is saying that 98% of the disk is being used by the filesystem, and the filesystem usage tool is saying that filesystem is 9% full.

---

### Post by taurus on 2007-11-23
Just post the output of this command from a terminal.

```
df -h
```

---

### Post by iiviip3 on 2007-11-23
I am having a similar issue. I've browsed the forum looking for why gparted merely finds my hard disk as one gigantic unallocated 93 gig drive, but no help thus far. When I entered your df -h command it spit back...

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda8             7.6G  7.2G   11M 100% /
varrun                506M   88K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
udev                  506M   76K  506M   1% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M   34M  472M   7% /lib/modules/2.6.22-14-generic/volatile
/dev/sda7              46M   22M   22M  51% /boot
/dev/sda1              17G   15G  2.0G  89% /media/sda1
/dev/sda5              69G   58G   11G  85% /media/sda5
overflow              1.0M  208K  816K  21% /tmp

I have a dual-boot system with XP. I've just started using ubuntu 2 weeks ago and love it. Now I would like to resize my partitions to give Ubuntu more space but I am running into problems. Partition Magic comes up with an error when I tried in Windows. Any help would be much appreciated. These forums have been fantastic; very helpful. Thanks!

---

### Post by solidus126 on 2007-12-13
I too am having issues with full disk errors.  I know for a fact that my Western Digital My Book 160GB external USB hard drive (/dev/sdb1 in the output) has about 35GB of free space (checked it with Windows on two separate comuters), but as you see from the output of "df -h", it for some reason is thinking that there is only about 1.4MB free.  Read/Write work perfect under windows, and it is a single FAT32 partition on the external drive.

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3              52G   36G   14G  72% /
varrun                506M  112K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
procbususb            506M  112K  506M   1% /proc/bus/usb
udev                  506M  112K  506M   1% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M   33M  474M   7% /lib/modules/2.6.20-16-generic/volatile
/dev/sda1              47M  389K   46M   1% /media/sda1
/dev/sda2              20G   19G  1.3G  94% /media/sda2
/dev/sdb1             150G  150G  1.4M 100% /media/My Book

Has anyone come up with a solution to this problem?  I have tried to boot into safe mode to see if I could find anything but no cigar.  I am in the midst of upgrading to Kubuntu 7.10 and my progress has been stopped due to this problem.  Thank you for your time!

-Luke

---

