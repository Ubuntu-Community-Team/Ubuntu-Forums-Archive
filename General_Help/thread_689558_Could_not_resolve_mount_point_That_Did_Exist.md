---
title: "Could not resolve mount point That Did Exist"
date: 2008-02-06
forum: General Help
---

### Post by ssechaud on 2008-02-06
Hi,

I am having trouble with my mount points for some windows shares I have. I had set them up and they were working, but after rebooting they have "disappeared", when running "moint -a" they cannot be resolved. However when running "mkdir" they are said to already exist. I've even tried to change the permissions of "/mnt" in case I couldn't see or modify it. Here are some of the logs:

root@user02:/home/user# sudo mount -a
Could not resolve mount point /mnt/user00c

root@user02:/home/user# sudo mkdir /mnt/user00c
mkdir: cannot create directory `/mnt/user00c': File exists

root@user02:/home/user# sudo chmod -R 755 /mnt
chmod: cannot access `/mnt/user00c': Input/output error

I am probably missing something obvious or a fundamental rule somewhere. I am using my linux box as a webserver to host a music streaming service for me and my friends and my music is stored on a windows machine that I use for myself in the home. This setup has worked alright before in the past but I am now having this problem.

I am not well versed in the art of using linux and maybe something in the way I have set things up may be the cause, I will try to explain what I have done to the box.

I installed [Mythbuntu]("http://www.mythbuntu.org/") cause I like how it automatically setup a vnc server for me, then installed the [Xubuntu]("http://www.xubuntu.org/") desktop components from within the Mythbuntu Control Panel. I used [Xampp]("http://www.apachefriends.org/en/xampp-linux.html") as my webserver package and [JInzora]("http://en.jinzora.com/") as my streaming software. I setup the mount points in "/etc/fstab" and it worked alright. Now I am having the problem described above.

Any help or advice would be greatly appreciated and thanks for taking the time to read this post. Also apologies if this should be on another forum and not here.

---

### Post by taurus on 2008-02-06
Can you post

```
sudo fdisk -l
cat /etc/fstab
df -h
```

---

### Post by osos on 2008-02-06
what is in your /mnt folder?
also could you paste the contents of /etc/fstab here

---

### Post by ssechaud on 2008-02-06
Thanks for the fast replies:

Taurus:

root@user02:/home/user# sudo fdisk -l

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00045c38

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4660    37431418+  83  Linux
/dev/sda2            4661        4865     1646662+   5  Extended
/dev/sda5            4661        4865     1646631   82  Linux swap / Solaris

root@user02:/home/user# cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=4f9c95c2-4c10-4d71-8fca-d0cd74dd55cd /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=a57ac4b6-719b-4f1a-bb8a-0e910eb40e93 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
//user00/user00-c   /mnt/user00c      smbfs   credentials=/etc/.smbpasswd,uid=1000 0 0

root@user02:/home/user# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              36G  2.7G   31G   8% /
varrun                378M  204K  378M   1% /var/run
varlock               378M     0  378M   0% /var/lock
udev                  378M   72K  378M   1% /dev
devshm                378M   12K  378M   1% /dev/shm
lrm                   378M   34M  345M   9% /lib/modules/2.6.22-14-generic/volatile

osos:

I have basically mounted the shared drive on my windows machine that holds my music.

fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=4f9c95c2-4c10-4d71-8fca-d0cd74dd55cd /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=a57ac4b6-719b-4f1a-bb8a-0e910eb40e93 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
//user00/user00-c	/mnt/user00c	smbfs	credentials=/etc/.smbpasswd,uid=1000 0 0

---

### Post by ssechaud on 2008-02-13
Still having trouble with this, can anyone cast some light on what may be wrong?

---

### Post by ssechaud on 2008-04-18
I've reinstalled the OS and set it up again and its working but I still have no idea why this happened. I will see if it happens again and post back with any info.

---

