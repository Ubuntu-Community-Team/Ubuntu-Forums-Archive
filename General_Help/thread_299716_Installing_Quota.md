---
title: "Installing Quota"
date: 2006-11-14
forum: General Help
---

### Post by napoelon on 2006-11-14
I need helping installing quota. Well, its installed, but im following this guide ([http://www.howtoforge.com/perfect_setup_ubuntu_6.10_p4)](http://www.howtoforge.com/perfect_setup_ubuntu_6.10_p4)), and it says the following:
<quote>
Edit /etc/fstab. Mine looks like this (I added ,usrquota,grpquota to partition /dev/sda1 (mount point /; your device name might be /dev/hda1 or similar)):

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=02cc04f2-98cb-41db-8eb3-94de5f19b22b /               ext3    defaults,errors=remount-ro,usrquota,grpquota 0       1
# /dev/sda5
UUID=6b011d54-fb37-469d-9fa8-179b185343c1 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
</quote>

Now my fstab file says the following:

<quote>

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=195c3be1-c1c7-416a-9cef-34c4f1c96a73 none            swap    sw           $
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
</quote>

Can someone please tell me what I should edit/add for the following?

Thanks!

---

