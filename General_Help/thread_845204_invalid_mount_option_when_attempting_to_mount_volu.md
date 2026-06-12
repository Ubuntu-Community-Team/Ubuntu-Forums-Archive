---
title: "invalid mount option when attempting to mount volume 'UDF VOLUME'&quot;"
date: 2008-06-30
forum: General Help
---

### Post by amamdispencer on 2008-06-30
Hi everyone,
New to Linux and ubuntu and need help on the following:
1) can't open my empty re-writable disks, keep getting the message 'invalid mount option when attempting to mount volume 'UDF VOLUME'". 

2) how do i download and install third party software programmes from their websites? Do not know where to save them so that they work.

3) what are bin files, where do i save them and how do i open them

4) some downloads are saved as archive files, don't know the head or tail of what to do with them.

5) Can any one recommend a good anti-virus software that works with ubuntu?


thank you very much.

---

### Post by VMC on 2008-06-30
Here's a link with a fix for mounting UDF DVD's:
[http://amazingrando.wordpress.com/2007/05/02/how-to-mount-udf-dvds-in-ubuntu/](http://amazingrando.wordpress.com/2007/05/02/how-to-mount-udf-dvds-in-ubuntu/)

---

### Post by amamdispencer on 2008-06-30
Thanks for the reply, however the link didn't solve my problem.

Heres what my fstab looks like after following the links directives and i still get the same can't mount udf volume message.

Would really appreciate further assistance.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/host/ubuntu/disks/root.disk /               ext3    loop,errors=remount-ro 0       1
/host/ubuntu/disks/boot /boot           none    bind            0       0
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
/dev/scd0 /media/cdrom0 auto user,noauto 0 0

---

