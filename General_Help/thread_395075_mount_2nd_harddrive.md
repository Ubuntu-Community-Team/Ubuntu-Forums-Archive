---
title: "mount 2nd harddrive"
date: 2007-03-27
forum: General Help
---

### Post by Digitallysick on 2007-03-27
I have formatted my second hd to ext3, i can click the icon, enter my password, and then access my drive, how i can mount it at startup without a password? and give my network read/write permission?

---

### Post by paparucino on 2007-03-28
> **Digitallysick said:**
> I have formatted my second hd to ext3, i can click the icon, enter my password, and then access my drive, how i can mount it at startup without a password? and give my network read/write permission?

```

su gedit /etc/fstab

```

add following line
```

/dev/hdbx /media/hdbx  ext3 defaults 0 2


```

where hdbx is the name of the device you use when mout manually

---

### Post by Digitallysick on 2007-03-30
i still cant get it to work, my 2nd HD is an 80 gig sata

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=f6d1b956-3f42-4ff1-b1f8-125226735a56 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb1 /media/disk  ext3 defaults 0 2
# /dev/sda5
UUID=8aad1a94-725c-48b0-a5ec-2581a4ccf95d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

i put in 

# /dev/sdb1 /media/disk  ext3 defaults 0 2


but it does nothing at boot up i still have to mount my 2nd hardrive manually

---

### Post by Motoxrdude on 2007-03-30
> **Digitallysick said:**
> i still cant get it to work, my 2nd HD is an 80 gig sata

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=f6d1b956-3f42-4ff1-b1f8-125226735a56 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb1 /media/disk  ext3 defaults 0 2
# /dev/sda5
UUID=8aad1a94-725c-48b0-a5ec-2581a4ccf95d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

i put in 

# /dev/sdb1 /media/disk  ext3 defaults 0 2


but it does nothing at boot up i still have to mount my 2nd hardrive manually
Dont put in the "#".

---

