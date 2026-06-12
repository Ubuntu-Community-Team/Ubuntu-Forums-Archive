---
title: "fstab auto mount/umount /dev/sdb1 partition"
date: 2012-11-14
forum: General Help
---

### Post by uzoyabuzo on 2012-11-14
Hi out there, [I]hope someone can help me to solve a problem that I have concerning the automating umount of a mounted /dev/sdb1 partition. 

I  have got an usb key with 2 partitions (/dev/sdb1 and /dev/sdb2), the  sdb2 partition is a BootIt partion and we will not care about this one. 

When I insert the usb key on my laptop, the /dev/sdb1 partition is automatically mounted to /media/[/I]2df8c6da-2dac-4c9a-81e2-aca0048ac5e1 folder). The /etc/mtab file is updated with this :

**/dev/sdb1 /media/2df8c6da-2dac-4c9a-81e2-aca0048ac5e1 ext2 rw,nosuid,nodev,uhelper=udisks 0 0**

When I remove the usb key the /dev/sdb1 is automatically unmounted, and the corresponding line in the mtab file is removed too.

Now,  I'd like to have the /dev/sdb1 be mounted to a folder named something  like /media/sdb1. So, I've added the following line to my /etc/fstab :

**/dev/sdb1 /media/sdb1 ext2 rw,user,noauto,nosuid,nodev,uhelper=udisks 0 0**

Now,  when I insert the usb key, the /dev/sdb1 partition is mounted to the  /media/sdb1 folder (great). But,... when I remove the usb key from the  laptop again, the /dev/sdb1 is not automatically unmounted and there  still is the following in the /etc/mtab file :

**/dev/sdb1 on /media/sdb1 type ext2 (rw,noexec,nosuid,nodev,uhelper=udisks,user=uzoyabuzo)**

The  only way to have the partition unmounted is to do it manually. So my  questions are : is it still possible to have it unmounted automatically ?  am I doing something wrong ?

Thanks for your help !!
uzo

---

### Post by pkadeel on 2012-11-14
partitions and drives mounted via fstab can only be unmounted with root access

---

### Post by Morbius1 on 2012-11-14
When you plug in an external usb drive it will mount to /media/LABEL if there is a label or to /media/UUID if there is no label.

Since yours is mounting to /**media/2df8c6da-2dac-4c9a-81e2-aca0048ac5e1** it's because it has no label. So the easiest solution is to give it one. There's a command line way to do that which I have forgotten at the moment so just install and use gparted to do it.

I would not use sdb1 if I were you however since that’s just going to be confusing to have a label by that name. Choose something that makes sense to you and is unique.

---

### Post by uzoyabuzo on 2012-11-14
Thanks for your answers ! I've used google and found the command line to change the disk label : sudo e2label /dev/sdb1 usbkey. Now the /dev/sdb1 partition mounts to /media/usbkey, and unmounts when I remove the usb key... (simple and easy to remember...). Thanks !

---

