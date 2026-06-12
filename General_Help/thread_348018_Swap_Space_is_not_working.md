---
title: "Swap Space is not working"
date: 2007-01-28
forum: General Help
---

### Post by nike984 on 2007-01-28
Yesterday, I've modified the size of my Swap partition by using Gparted.
After resizing the / & swap partition for ubuntu Edgy,the  swap space is not recognized.
But, Ubuntu partition and Window partition is working fine.
I think that if I can correctly modify the /etc/fstab file, the Swap partition will work,
but I'm a newbie, so I desperately need your help.:confused:  

 The result for "free -m" is
```
             total       used       free     shared    buffers     cached
Mem:           470        450         20          0          9        166
-/+ buffers/cache:        273        197
Swap:            0          0          0
```

The result for "sudo fdisk -l" is 
```
Disk /dev/hda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        6020    48355618+   7  HPFS/NTFS
/dev/hda2            6021        6149     1036192+  82  Linux swap / Solaris
/dev/hda3            6150        7296     9213277+  83  Linux

```

Also, my /etc/fstab file (I'm using Edgy) is 
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3
UUID=ef9e9486-85d8-4018-b42f-dd26562aa8bd /               ext3    defaults,error
s=remount-ro 0       1
# /dev/hda1
UUID=4250671F506718C5 /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46
 0       1
# /dev/hda2
UUID=9a418641-0362-473f-828f-80a16a577788 none            swap    sw            
  0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
```

---

### Post by cd-r80 on 2007-01-28
Are some of your lines commented out "#" or not in fstab?  Or is your cut & paste only mess...?

---

### Post by nike984 on 2007-01-28
shown on the post is same as the result on my terminal.
I've hearld that the Syntax for fstab used in Edgy is different.

---

### Post by nike984 on 2007-01-28
I've manually edit the /etc/fstab file as shown below.

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc            /proc   proc    defaults        0       0
/dev/hda3       /       ext3    defaults,errors=remount-ro      0       1
/dev/hda1       /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hda2       none    swap    sw      0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

After then, the swap partition is correctly recognized at the system monitor, but
still the 'used swap' measures to be stuck at 0.
Free -m result shown that 
```
             total       used       free     shared    buffers     cached
Mem:           470        459         11          0         11        234
-/+ buffers/cache:        213        257
Swap:         1011          0       1011
```

I can't figure out why the swap partition is still not working.
Please give me any help.

---

### Post by jimbob on 2007-01-28
So what makes you think you should be using swap all the time?

Is your machine heavily loaded with memory-intensive processes?

How much memory do you have?

There have been many posts about this subject but I don't remember the solution so do some forum searches for 'swap'.
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by olejorgen on 2007-01-28
[http://ubuntuforums.org/showthread.php?t=287962](http://ubuntuforums.org/showthread.php?t=287962)

try that

---

### Post by nike984 on 2007-01-28
Thanks for the reply.

Before I've extend the swap space to 1GB, I was using only 8M for swap,
and system monitor always shows that swap is used by 100%.
I've show some post at the forum that [it is normal to have 0% Swap usage]("http://ubuntuforums.org/showthread.php?t=344404&highlight=swap"), but if the swap was fully using 8M before,
isn't it logical that to still use at least 6~8M even though the swap partition has been
grown to 1GB?  :confused:

p.s. My RAM capacity is 512M and 32M is shared by graphic card.
       Currently only 255M/ 470M (~50%) is used.

---

