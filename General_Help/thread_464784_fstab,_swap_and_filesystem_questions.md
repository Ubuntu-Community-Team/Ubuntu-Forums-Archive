---
title: "fstab, swap and filesystem questions"
date: 2007-06-05
forum: General Help
---

### Post by SpanishFranks on 2007-06-05
Here is my fstab file
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1 -- converted during upgrade to edgy
UUID=c8d1f4d9-3e2e-4cd4-8c6d-59f53c3b5ff8 / ext3 defaults,errors=remount-ro,user_xattr 0 1
# /dev/hda5 -- converted during upgrade to edgy
/dev/sda5 none swap sw 0 0
/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto     0       0
```

It's a mix of UUIDs and dev names. My swap partition doesn't mount at boot (not since kernel update). The output from```
sudo blkid
``` is ```
/dev/hda5: UUID="7370b8fb-daab-4e72-827e-e87ad505fb87" TYPE="swap" 
/dev/hda1: UUID="c8d1f4d9-3e2e-4cd4-8c6d-59f53c3b5ff8" SEC_TYPE="ext2" TYPE="ext3" 
/dev/mapper/hda5: TYPE="swap" UUID="7370b8fb-daab-4e72-827e-e87ad505fb87" 
/dev/mapper/hda1: UUID="c8d1f4d9-3e2e-4cd4-8c6d-59f53c3b5ff8" SEC_TYPE="ext2" TYPE="ext3" 

```

What are these /dev/mapper/.. mounts? Should I give my /dev/hda5 swap partition the UUID from the blkid output?

Thanks

---

### Post by confused57 on 2007-06-05
Here's an example of how your swap partition is mounted using UUID:
[http://users.bigpond.net.au/hermanzone/p10.htm#Edgy_Efts_new_etcfstab_files_with](http://users.bigpond.net.au/hermanzone/p10.htm#Edgy_Efts_new_etcfstab_files_with)

---

