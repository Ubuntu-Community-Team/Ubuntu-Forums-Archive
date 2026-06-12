---
title: "Uninstalling Kubuntu"
date: 2007-02-09
forum: General Help
---

### Post by Jay-Jay on 2007-02-09
OK. Here's the situation. I have two hard drives. One with Ubuntu, the other with Kubuntu. Now I  want to format the disk with Kubuntu, but I'm not sure if that will also erase the boot information for that drive. Will I have to remove the boot information for that drive manually or will it erase the boot information automatically with the formatting of the drive?

---

### Post by shak on 2007-02-09
Manually if the boot information is stored in the MBR the Master Boot Record. 

Simple formatting won't erase it. 

But it's difficult to give you a specific answer because you can mess things up easily.

In a nutshell:

You can format the Kubuntu harddisk if you store all Boot-Information in the MBR of the Ubuntu harddisk. 
See the Grub infopage for removing Boot options

or do a ```
 man grub 
```

After that you have to make sure that  the Bootable Flag on the Ubuntu harddrive is set.

---

### Post by Jay-Jay on 2007-02-09
OK. it seems as if the MBR is on the drive that I want to format. So how do I copy it to the Ubuntu hard drive?

---

### Post by shak on 2007-02-09
the most painless way should be to use this guide: 

[http://doc.gwos.org/index.php/Restore_Grub](http://doc.gwos.org/index.php/Restore_Grub)

Be sure to follow this guide exactly and write down the numbers of your harddisk partitions on paper before - this will be very handy
ex.
 /dev/hda1 (Ubuntu Harddrive with /root aso) 
 /dev/hdb2 (Kubuntu) and so on

if all went well you can format your Kubuntu harddisk afterwards. there is no need for doing it before - just in case you need to boot back before you proceed.

With gparted you can change view, resize, whatever...

[http://www.gnu.org/software/parted/index.shtml](http://www.gnu.org/software/parted/index.shtml)

regards

---

