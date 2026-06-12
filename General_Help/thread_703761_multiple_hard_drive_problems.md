---
title: "multiple hard drive problems"
date: 2008-02-21
forum: General Help
---

### Post by svtfmook on 2008-02-21
ok, i have 3 hard drives
SDA
SDB
SDC

now, SDA1 has my windows partition
SDB1,2&3 are my gutsy partitions
SDC is currently unallocated

now, what i'd like to do is create a partition on SDC so i can backup important data.

i tried creating the partition using gparted, but when i try to write anything to it, i don't have priveledges (owner is root).

i'd also like to rename the volumes, because it's going to be difficult to distinguish which is which since they both show up as "238GB volume" in nautilus.

i also have a mobile rack coming that i will use for the drive SDC.

how do i go about setting this up properly?

---

### Post by Shazaam on 2008-02-21
The drive is probably mounted. To be safe try this....
Set your pc to boot from cd, pop the Ubuntu livecd in the drive and boot. Run gparted from the livecd to set up your third drive.

---

### Post by svtfmook on 2008-02-21
ok, i created the partitions with a live gparted cd, but i still cannot write to the drive due to lack of permissions.

---

### Post by Shazaam on 2008-02-21
Can you post the terminal output of this?
```
mount
```

---

### Post by svtfmook on 2008-02-22
/dev/sdb1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
/dev/sdb3 on /home type ext3 (rw)
none on /proc/bus/usb type usbfs (rw,devgid=46,devmode=664)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/sdc1 on /media/disk type ext3 (rw,nosuid,nodev)

the sdc1 is one of the partitions in question.  the other partition is not mounted right now

---

### Post by svtfmook on 2008-02-22
ok, i'm an idiot.  i just had to change ownership.

now how do i rename the partitions?

---

### Post by LuisGMarine on 2008-02-22
Try this guide here:

[https://help.ubuntu.com/community/RenameUSBDrive]("https://help.ubuntu.com/community/RenameUSBDrive")

I think that is what you are looking for.  If you are talking about the name when you see the HDD icon on your desktop then that depends on what the mount folder is.  e.i

I have a hard drive, /dev/sdb , that is mounted to /media/extradrive.  When the HDD is mounted, it shows up as the name " extradrive . "  now if you want to change the actual names of the partitions like you would have / for root or /home, that guide should point you in the right direction.

---

### Post by svtfmook on 2008-02-22
perfect!  thanks!

---

