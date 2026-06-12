---
title: "Re: Mounting Linux hard drive [Resolved]"
date: 2006-12-15
forum: General Help
---

### Post by jtfolden on 2006-12-15
> **aysiu said:**
> To make sure you have proper access to it, change ownership on the partition: ```
sudo chown -R ptah:ptah /media/extrastuff
```

I just happen to be setting up a 2nd drive myself and I've successfully done everything up to this part. HOWEVER, the volume is still listed as being owned by root and I can not make any changes to it (can't create folders, add files, etc)....

---

### Post by aysiu on 2006-12-15
If you don't mind, I'm actually going to move you to your own thread. Your problem is entirely different, as the other person didn't even have a valid partition table.

Can you post the output of these commands? ```
sudo fdisk -l
df -h
cat /etc/fstab
```

---

### Post by jtfolden on 2006-12-15
> **aysiu said:**
> If you don't mind, I'm actually going to move you to your own thread. Your problem is entirely different, as the other person didn't even have a valid partition table. 

No problem... i just didn't want to litter the forum with too many similar threads so was at least *trying* to do the right thing. :lol:

sudo fdisk -l
```

Disk /dev/hda: 7510 MB, 7510164480 bytes
255 heads, 63 sectors/track, 913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1         871     6996276   83  Linux
/dev/hda2             872         913      337365    5  Extended
/dev/hda5             872         913      337333+  82  Linux swap / Solaris

Disk /dev/hdb: 8455 MB, 8455200768 bytes
255 heads, 63 sectors/track, 1027 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        1027     8249346   83  Linux

```

df -h
```

Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1             6.6G  2.6G  3.7G  41% /
varrun                125M  140K  125M   1% /var/run
varlock               125M     0  125M   0% /var/lock
procbususb             10M  100K   10M   1% /proc/bus/usb
udev                   10M  100K   10M   1% /dev
devshm                125M     0  125M   0% /dev/shm
lrm                   125M   18M  108M  14% /lib/modules/2.6.17-10-generic/volatile
/dev/hdb1             7.8G  146M  7.3G   2% /media/uStorage
//192.168.1.100/Movies_HD
                      280G  274G  5.9G  98% /media/Movies HD
//192.168.1.100/Storage_HD
                      280G  270G  9.9G  97% /media/Storage HD

```

cat /etc/fstab
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=a35be0ff-f810-4ca4-8f4e-ea4c53ff25ed /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=f97ed499-76f7-4b84-aa4f-549cc37036fe none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
# /dev/           /media/floppy0  auto    rw,user,noauto  0       0
/dev/hdb1 /media/uStorage ext3 defaults 0 0
//192.168.1.100/Movies\040HD /media/Movies\040HD smbfs username=xxx,password=xxx,umask=022 0 0
//192.168.1.100/Storage\040HD /media/Storage\040HD smbfs username=xxx,password=xxx,umask=022 0 0





```[/QUOTE]

---

### Post by aysiu on 2006-12-15
Everything looks kosher to me.

And you've already done ```
sudo chown -R jtfolden:jtfolden /media/uStorage
``` huh?

I know this may seem out there, but can you try a reboot? Theoretically, you shouldn't have to, but I think it's worth a shot.

---

### Post by jtfolden on 2006-12-15
> **aysiu said:**
> I know this may seem out there, but can you try a reboot? Theoretically, you shouldn't have to, but I think it's worth a shot.

Well, that was too simple... a reboot worked. ](*,)  

Also, I notice that while the volume is labeled properly on the Desktop and in the sidebar, in the Computer window of Nautilus it is listed as "7.9 GB Volume: uStorage" rather than just the name. Is there a fix for this oddity?

As a side question, under OS X there is an option to "Ignore Ownership On This Volume" for secondary and external volumes so pretty much anyone and everyone can read/write/move/create/delete any and all files and folders for collaborative projects. Is there anything similar for this situation?


Thanks,
John

---

### Post by aysiu on 2006-12-15
If you chmod it to 777, anyone can read/write/execute.

---

### Post by jtfolden on 2006-12-15
> **aysiu said:**
> If you chmod it to 777, anyone can read/write/execute.

Including any files made in the future? So if at some point "user A" makes a file "a.txt" and then "user B" later comes along he can then modify "a.txt" as he pleases?

---

### Post by aysiu on 2006-12-15
> **jtfolden said:**
> Including any files made in the future? So if at some point "user A" makes a file "a.txt" and then "user B" later comes along he can then modify "a.txt" as he pleases?
Good point.

[This post](http://ubuntuforums.org/showpost.php?p=1509894&postcount=3) may help you out.

---

### Post by jtfolden on 2006-12-15
> **aysiu said:**
> Good point.

[This post](http://ubuntuforums.org/showpost.php?p=1509894&postcount=3) may help you out.


Thanks!

---

