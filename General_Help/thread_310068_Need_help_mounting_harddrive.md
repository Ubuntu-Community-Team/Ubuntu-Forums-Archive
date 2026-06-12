---
title: "Need help mounting harddrive"
date: 2006-11-30
forum: General Help
---

### Post by Castigate on 2006-11-30
I formatted an additional hardrive to ext3.  It shows up in my file system but I cannot do anything with it.  I cant create folder or save anything in it.  When I right click on it there is no option to mount or unmount.  Can someone help me out.  

Here is sudo fdisk -l output

Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2422    19454683+   7  HPFS/NTFS
/dev/hda2            2423        2613     1534207+  82  Linux swap / Solaris
/dev/hda3            2614        4865    18089190   83  Linux

Disk /dev/hdb: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        2434    19551073+  83  Linux

Disk /dev/hdc: 20.4 GB, 20490559488 bytes
255 heads, 63 sectors/track, 2491 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1               1        2491    20008926   83  Linux


hdc1 is the harddrive I would like to use as and extra drive in linux
Thanks

---

### Post by taurus on 2006-11-30
Where do you mount /dev/hdc1 because you can change permissions so you can read and write to it with the chmod command...

```
sudo chmod 777 <mount point>
```

---

### Post by Castigate on 2006-11-30
Im not really sure where I mount it.  Sorry I'm still very new to this.  Maybe you can explain it easier for me.

---

### Post by taurus on 2006-11-30
Can you paste the output of these two commands from a terminal?

Applications -> Accessories -> Terminal
```
cat /etc/fstab
df -h
```

---

### Post by Castigate on 2006-11-30
castigate666@homedesktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3
UUID=934386c8-78fc-4db1-afde-a04bb4f7db78 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb1
UUID=a3fbcba1-0148-45c4-9129-d568eeecb110 /home           ext3    defaults        0       2
# /dev/hda1
UUID=F6B8EF73B8EF30B3 /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hdc1
UUID=12CA7A92924BACE9 /media/hdc1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda2
UUID=89352d6f-af48-450a-ae76-a497fd5b1c39 none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

castigate666@homedesktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda3              17G  4.6G   12G  29% /
varrun                379M   88K  379M   1% /var/run
varlock               379M     0  379M   0% /var/lock
procbususb             10M  136K  9.9M   2% /proc/bus/usb
udev                   10M  136K  9.9M   2% /dev
devshm                379M     0  379M   0% /dev/shm
lrm                   379M   18M  362M   5% /lib/modules/2.6.17-10-generic/volatile
/dev/hdb1              19G  9.6G  7.9G  55% /home
/dev/hda1              19G   12G  7.5G  61% /media/hda1
castigate666@homedesktop:~$

---

### Post by taurus on 2006-11-30
What other ext3 partition are you talking about because I only see two:  / & /home?

You said that you formatted /dev/hdc1 as ext3 but how come you mount it as ntfs!  Is that an old entry before you reformatted it from ntfs to ext3?

---

### Post by Castigate on 2006-11-30
I guess Thats the problem I formatted hdc1 in ext3.  It probably is an old entry because that use to be the extra hardrive for windows xp.  It was NTFS and I used QTPARTED to format it to ext3 because I coudln't use it before.  I could only read.  I'm trying to convert to linux little by little:-D So what should I do to fix it?

---

### Post by Castigate on 2006-11-30
Can anybody out there help me.  I'm really stuck](*,)

---

### Post by taurus on 2006-11-30
If you formatted /dev/hdc1 to ext3, then you need to modify your /etc/fstab.  

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/fstab
```
Remove the old entry for /etc/hdac1 and add this line in there.

```
/dev/hdc1   /media/hdc1   ext3   defaults   0   1
```
Reboot and enjoy...

---

### Post by Castigate on 2006-12-01
It didn't work, after changing old entry to  
/dev/hdc1   /media/hdc1   ext3   defaults   0   1
I was unable to reboot into KDE.  I didn't know how to go back to old setting through comand line so I reinstalled kubuntu]:mad:    I'm still having the same problems with hdc1.  I need more help](*,)

---

### Post by Castigate on 2006-12-01
Drive hdc1 is mounted but I can only read from it.  Does anyone know how I can enable writing as well?

---

### Post by Castigate on 2006-12-01
Anyone?

---

### Post by taurus on 2006-12-01
Since /dev/hdc1 is ext3 and if you want to write to it, you just have to change the permissions of it then!!!

```
sudo chmod -R 777 /media/hdc1
```

---

### Post by Castigate on 2006-12-01
Thank you!  That worked:-D   Can I do that with hda1 wich is my windows xp partition?  This way I can write to it as well?

---

