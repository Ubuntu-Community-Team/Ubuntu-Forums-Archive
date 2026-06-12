---
title: "two /home partitions sda1,sda5 sda1-no space remaining"
date: 2012-12-20
forum: General Help
---

### Post by kpholmes on 2012-12-20
in setup my home directory be on a seperate partition then root. but on the / partition i see a /home

also on sda5, the intended /home folder, is a complete copy. i think theres some link to both partitions, how do i go about closing or deleting the /home partition on sda 1 without breaking the computer??

thanks in adavance

---

### Post by fdrake on 2012-12-20
> **kpholmes said:**
> in setup my home directory be on a seperate partition then root. but on the / partition i see a /home

also on sda5, the intended /home folder, is a complete copy. i think theres some link to both partitions, how do i go about closing or deleting the /home partition on sda 1 without breaking the computer??

thanks in adavance
 are you sure that the home in sda5 is not just mounted on the home of sda1?

post the output of "mount"

---

### Post by kpholmes on 2012-12-20
```
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
/dev/sda5 on /home type ext4 (rw)
gvfsd-fuse on /run/user/saturn/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=saturn)
/dev/sdb1 on /media/saturn/HD2 type ext3 (rw,nosuid,nodev,uhelper=udisks2)
/dev/sda5 on /mnt/newhome type ext4 (rw)

```

---

### Post by fdrake on 2012-12-20
as i suspected it is mounted on the /home folder . everything is the way it is supposed to be :
> [COLOR="Red"]**/dev/sda5 on /home type ext4 (rw**[/COLOR])
no reason to worry about it.. as you can check the size of the sda1 partition is intact because nothing it is coppied in /home. All the files that you see are mounted fro  the sda5 partition . if you boot with a live cd and check  the /home directory in sda1 it will be empty

---

### Post by kpholmes on 2012-12-20
thanks!

---

### Post by fdrake on 2012-12-20
> **kpholmes said:**
> thanks! didnt know i had to mount it. was getting errors! so ill have to set this up to mount on boot also? you have to change your /etc/fstab.

---

### Post by kpholmes on 2012-12-20
looking at fstab its setup the way i would like it to be. let me upload a pic of the disc analyzer.

```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=b7cb9bb6-906f-447a-80c3-60ed71f01610 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda5 during installation
UUID=38a7f4ab-d195-4c67-a6cd-c24f0b55d15d /home           ext4    defaults        0       2
# swap was on /dev/sda2 during installation
UUID=b50f19b7-f58e-458e-9f62-93fdfb5dbcf5 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

```

---

### Post by kpholmes on 2012-12-20
http://    lookpic.com/O/i2/127/hFaeNmKC.png

[IMG]http://lookpic.com/O/i2/127/hFaeNmKC.png[/IMG]

trying to get the pic up, 1 min

---

### Post by fdrake on 2012-12-20
the fstab looks good... but i don't understand the issue? you cannot boot or something? or cannot login? i am missing the point...

---

### Post by kpholmes on 2012-12-20
just got the pic up, this is all on a 1tb hard drive so i know im not out of space, but that ive somehow didnt partition right. 

the /mnt/nowhome is what i mounted earlier before making the thread.

---

### Post by fdrake on 2012-12-20
> **kpholmes said:**
> just got the pic up, this is all on a 1tb hard drive so i know im not out of space, but that ive somehow didnt partition right. 

the /mnt/nowhome is what i mounted earlier before making the thread.

i have to go to bed(3:26am).. i'll check the thread in the morning. Change the thread to "Unsolved" so other ppl will help you. Also the full hdd is a recurring isssue in the forum ,I would goolgr around I am sure it's nothing serious ...

---

### Post by kpholmes on 2012-12-20
thanks for the help!

---

### Post by kpholmes on 2012-12-20
rsync: write failed on "/media/saturn/foxcon-backup/ ": No space left on device (28)
rsync error: error in file IO (code 11) at receiver.c(322) [receiver=3.0.9]
rsync: connection unexpectedly closed (272 bytes received so far) [generator]
rsync error: error in rsync protocol data stream (code 12) at io.c(605) [generator=3.0.9]
saturn@MK:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1        28G   24G  3.1G  89% /
udev            1.5G  4.0K  1.5G   1% /dev
tmpfs           602M  1.3M  601M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            1.5G   76K  1.5G   1% /run/shm
none            100M   24K  100M   1% /run/user
/dev/sda5       888G  170G  674G  21% /home

---

### Post by kpholmes on 2012-12-20
i figured it out, i was not loading the proper locations with rsync

thanks for the help :p

---

