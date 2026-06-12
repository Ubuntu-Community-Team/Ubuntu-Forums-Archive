---
title: "file permissions on newly created directory"
date: 2007-09-17
forum: General Help
---

### Post by jamesr on 2007-09-17
Hi, 

I am in the process of upgrading to Feisty from Edgy. The system was working now it is not fully working  so frustration and errors are creeping in. 

The current problem is that I created a separate /home in an independant partition no problem . Created under edgy and upgraded. I believe that is working on the correct partition and with all of the correct permissions. So I thought I would create 2 additional partitions and mount as /extra and /files. These were created at the same level as the /home directory ie /.

Now that I have upgraded to Feisty I am unable to write to these directories / partitions. I cannot load back the data from the old directories, saved on CDRWs.

I have changed, in an attempt to get the system working, the settings of Fstab to the following
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=b8c41060-342f-46ba-9cb6-211cfff1a3cb /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=b462ab83-49db-44e7-97b3-a415e5da7bfb none            swap    sw              0       0
/dev/hda6       /home           ext3    nodev,nosuid    0       2
/dev/hda7       /extra          ext3    defaults        0       0
/dev/hda8       /files          ext3    defaults        0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/cdrom        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
   
I have also tried```
sudo chown ashteq /extra
``` to no avail. I am trying to do this in odd available moments so my apologies for request for help. I think am going to have to re look at file permissions information again.

---

### Post by McNils on 2007-09-17
If want **ashteq** to own the files this should work.
```

sudo chown -R ashteq /extra
sudo chmod -R u+rwx /extra

```

---

### Post by jamesr on 2007-09-18
Hi McNils,

Thanks for the suggestion but I do not need to use your suggestion. because all the system needed, was a switch off and then a reboot. I know you should not need to reboot especially when the drives are  unmounted  and then remounted. What every was causing the glitch is no longer there.

Thanks again

---

