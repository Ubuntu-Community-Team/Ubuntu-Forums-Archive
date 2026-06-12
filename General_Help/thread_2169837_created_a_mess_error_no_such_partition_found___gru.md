---
title: "created a mess error: no such partition found   grub rescue"
date: 2013-08-23
forum: General Help
---

### Post by btrix on 2013-08-23
hello,

i had windows 8 on my laptop with 4 partitions C, D, E, F.
i installed ubuntu 12.04 0n E drive.
now i had shrinked the D volume and made a silly mistake of labeling it as F. so F was gone and shown as free space i think i lost my data on F drive.
so i booted my pc and got **error no such partition found   grub rescue** >
now what should i do to make ubuntu and windows run in dual boot and rescue my data from F drive. i have used testdisk but it didnt work.
i am using livecd of ubuntu now.
used boot repair but to no use  i am new to ubuntu
rootnoverify command not found
makeactive cmd not found
chain loader +1 cmd not found
boot cmd not found
tried all these no use

plz help

---

### Post by Quackers on 2013-08-23
You could boot from your Windows repair/installtion cd/usb and repair the MBR so that you can get Windows booting again.
Once that's done you can re-install grub from the Ubuntu live cd/usb to get both systems booting again.

---

### Post by btrix on 2013-08-24
can u help me rescue my data. i have used testdisk but doesnt work for me
plz help

---

### Post by Quackers on 2013-08-24
Have you tried booting from your Windows installation cd/usb and selecting repair the installation? If so, what happened?
If all is lost (though it may not be - unless Testdisk has over-written your partitions)) you could be able to get all your data back using the Ubuntu live cd/usb "try Ubuntu" desktop (copying your data).

---

### Post by btrix on 2013-08-24
well it said fixmbr is complete when i boot it doesnt show any error only curser.
also plz help me install grub using live cd of ubuntu

ok am in mess now. used gparted and it is not showing linux and swap. 
[IMG]http://i41.tinypic.com/mjwp6c.png[/IMG]
thnx

---

