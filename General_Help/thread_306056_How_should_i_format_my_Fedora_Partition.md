---
title: "How should i format my Fedora Partition"
date: 2006-11-24
forum: General Help
---

### Post by tomcheng76 on 2006-11-24
Currently i have windows XP, Fedora and Ubuntu Edgy and having a grub in fedora, with a triboot menu

I found that Ubuntu is great , so i desided to delete those partitions of fedora
first i boot into ubuntu , cd / and then grub-install /dev/hda
everything is fine. now i have a boot menu with ubuntu and xp

the problem is that fedora's partitions is LVM and i dunno how to deal with them.
hda9 is my edgy and i think hda3,hda4 and hda5 is fedora?

Here is my fdisk -l

Disk /dev/hda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = &#12471;&#12522;&#12531;&#12480;&#25968; of 16065 * 512 = 8225280 bytes

&#12487;&#12496;&#12452;&#12473; Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1         653     5245191    7  HPFS/NTFS
/dev/hda2             654        4569    31455270    7  HPFS/NTFS
/dev/hda3            4570        4582      104422+  83  Linux
/dev/hda4            4583       30401   207391117+   f  W95 Ext'd (LBA)
/dev/hda5            4583        6279    13631121   8e  Linux LVM
/dev/hda6            6280       16853    84935623+   7  HPFS/NTFS
/dev/hda7           16854       17375     4192933+   b  W95 FAT32
/dev/hda8           17376       18680    10482381    7  HPFS/NTFS
/dev/hda9           18681       20638    15727603+  83  Linux
/dev/hda10          20639       24555    31463271    7  HPFS/NTFS
/dev/hda11          24556       30401    46957963+   7  HPFS/NTFS

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = &#12471;&#12522;&#12531;&#12480;&#25968; of 16065 * 512 = 8225280 bytes

&#12487;&#12496;&#12452;&#12473; Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        9729    78148161    7  HPFS/NTFS

and here is my fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda9 -- converted during upgrade to edgy
UUID=e7db6e08-4d90-4dc3-87cb-498e425e02bb / ext3 defaults,errors=remount-ro 0 1
/dev/hda1       /media/hda1     ntfs    defaults,nls=utf8,ro,umask=222,noauto,gid=46 0       1
/dev/hda2       /media/hda2     ntfs    defaults,nls=utf8,ro,umask=222,noauto,gid=46 0       1
# /dev/hda3 -- converted during upgrade to edgy
UUID=9b643074-0359-4cc9-92ab-fb7cab2d9dee /media/hda3 ext3 defaults 0 2
# /dev/hda6 -- converted during upgrade to edgy
UUID=ACC02009C01FD902 /media/hda6 ntfs defaults,nls=utf8,ro,umask=222,gid=46 0 1
# /dev/hda7 -- converted during upgrade to edgy
UUID=185D-2502 /media/hda7 vfat defaults,utf8,umask=007,gid=46 0 1
# /dev/hda8 -- converted during upgrade to edgy
UUID=98FC471CFC46F452 /media/hda8 ntfs defaults,nls=utf8,ro,umask=222,gid=46 0 1
# /dev/hdb1 -- converted during upgrade to edgy
UUID=3E78D44878D40097 /media/hdb1 ntfs defaults,nls=utf8,ro,umask=222,gid=46 0 1
/dev/mapper/VolGroup00-LogVol00 /media/mapper_VolGroup00-LogVol00 ext3    defaults        0       2
/dev/mapper/VolGroup00-LogVol01 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda10      /media/hda10 ntfs defaults,nls=utf8,ro,umask=222,gid=46 0 1
/dev/hda11      /media/hda11 ntfs defaults,nls=utf8,ro,umask=222,gid=46 0 1

any help will be appreciate ](*,)

---

### Post by tomcheng76 on 2006-11-24
Here is the Gparted snap
[IMG]http://img511.imageshack.us/img511/6180/gparteddz1.png[/IMG]
I cannot umount hda3. It said "Most likely other partitions are also mounted on these mountpoints. You are advised to umount them manually.
I thought that combining them (hda3,4 and 5) together without umount is dangerous. So, i stopped here. Any idea?

---

### Post by timcredible on 2006-11-24
the logical partitions create issues with some partition managers.  if you want to keep the logical partition, use qtparted to work on the drive (it handles it ok).  however, you might want to just backup all your data (grsync is good for this if you have a large usb external drive), and then delete all partitions and re-partition with primary partitions only.

---

### Post by tomcheng76 on 2006-11-24
Thanks timcredible
It seems that gparted is still not yet supported LVM
Any idea ? i just affraid to delete the logical partition and make other partition die
i cant even format hda5, that is currently most wanted
Any help will be appreciate

---

### Post by tomcheng76 on 2006-11-25
Anyone ? ](*,)

---

### Post by louieb on 2006-11-25
Just a thought. Why reformat it? If you want to empty it of its current contents and replace it with some other data. 
Check out the rm command.  Just be carefull.

---

### Post by tomcheng76 on 2006-11-25
It is a good idea, louieb
i just wonder if i could merge the 3 into 1 , that would be nicer
however, if it is too troublesome, i just rm, thanks !

---

