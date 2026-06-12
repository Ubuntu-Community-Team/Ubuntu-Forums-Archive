---
title: "[SOLVED] Windows hates me or something..."
date: 2008-02-28
forum: General Help
---

### Post by Zeotronic on 2008-02-28
The other day I had to get onto Windows... eww... to instruct my friend how to use Nero to burn the Ubuntu ISO to a disk so that he could install Ubuntu onto his computer. (take that Windows!) However, shortly after I was done doing that, but before I could retreat back to Xubuntu, Windows decided to have a seizure. After getting back to Xubuntu I noticed that I could no longer access my Windows partition from the folder I made to it... its contents appeared blank, however Windows is still alive and well (I checked). Can someone please present to me a way to create another folder to Windows (I don't recall how I did it the first time) and possibly some sort of an explanation of what may have happened? Thanks.

---

### Post by taurus on 2008-02-28
I just went through this with another poster.  If you didn't shutdown your windows cleanly, you won't be able to mount it in Ubuntu without using the force option.  

Post the outputs of these commands from a terminal.

```
sudo fdisk -l
cat /etc/fstab
df -h
```

---

### Post by Zeotronic on 2008-02-28
> If you didn't shutdown your windows cleanly, you won't be able to mount it in Ubuntu without using the force option. 
That makes sense... I'm going to go try to get Windows to do it *right* now...
> dusk@zeomatrix:~$ sudo fdisk -l
[sudo] password for dusk:

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4864    39070048+   7  HPFS/NTFS

Disk /dev/sdb: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x89d27200

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         255     2048256    5  Extended
/dev/sdb2             256        4863    37013760   83  Linux
/dev/sdb5               1         255     2048224+  82  Linux swap / Solaris
dusk@zeomatrix:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb2
UUID=c2a6d4db-0d1d-41ea-a51e-288c3333d803 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=4EC05CB2C05CA24F /WindowsXP      ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sdb5
UUID=5aa13677-b479-4009-a5a3-a8901f08a033 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
dusk@zeomatrix:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb2              35G   22G   12G  66% /
varrun                252M  120K  252M   1% /var/run
varlock               252M  4.0K  252M   1% /var/lock
udev                  252M   64K  252M   1% /dev
devshm                252M     0  252M   0% /dev/shm
lrm                   252M   17M  236M   7% /lib/modules/2.6.22-14-generic/volatile
dusk@zeomatrix:~$ 


---

### Post by Neodynamics on 2008-03-02
I'm having a similar issue. I also have noticed my windows folder is empty, and I have made sure windows was properly shut down. My Windows side did have some viruses on it however, would this have anything to do with this? If so, can I still transfer my windows data to Ubuntu?

If not, I'll just have to do it the 2 GB Jumpdrive way. : (

---

