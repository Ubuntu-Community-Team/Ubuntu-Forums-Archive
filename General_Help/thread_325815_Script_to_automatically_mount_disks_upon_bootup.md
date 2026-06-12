---
title: "Script to automatically mount disks upon bootup?"
date: 2006-12-26
forum: General Help
---

### Post by cody50 on 2006-12-26
Whenever I reboot my computer (ubuntu Dapper), I have to go to the disks-admin utility and manually enable/mount my partitions on my second ide hdd. 

Is there an easy way to automate this? I don't know much about bash scripting, but is there anything in that area or another area that could help solve this annoyance?

---

### Post by Dubbayoo on 2006-12-26
> **cody50 said:**
> Whenever I reboot my computer (ubuntu Dapper), I have to go to the disks-admin utility and manually enable/mount my partitions on my second ide hdd. 

Is there an easy way to automate this? I don't know much about bash scripting, but is there anything in that area or another area that could help solve this annoyance?

That is the purpose of /etc/fstab. Are they enabled for auto mounting there?

---

### Post by cody50 on 2006-12-26
so if this is the contents of that file,

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0


```

I would want to add a line such as,

/dev/hdb1   /myMountPoint   ext3    

and then i'm not sure about the <options> or <dump> <pass>.

---

### Post by bulldog on 2006-12-26
This is all you need I suppose,

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

[http://www.ubuntuforums.org/showthread.php?p=1837572#post1837572](http://www.ubuntuforums.org/showthread.php?p=1837572#post1837572)

---

### Post by Medieval_Creations on 2006-12-26
> **cody50 said:**
> 
I would want to add a line such as,
/dev/hdb1   /myMountPoint   ext3    
and then i'm not sure about the <options> or <dump> <pass>.

You are right, the line you would add to fstab would be

```

/dev/hdb1  /myMountPoint  ext3  defaults  0  0

```

I can't remember exactly what the options & dump/pass are, but the options sets various permissions on that drive when it is mounted.  The drop/pass has to do with if the data is stored when the system does backups.

---

### Post by cody50 on 2006-12-26
Looks like everything worked great.

Thanks everyone.

---

