---
title: "Optimizing Partitions after removal of Windows"
date: 2017-02-11
forum: General Help
---

### Post by DB4711 on 2017-02-11
Hello,

I had a dual boot Ubuntu / Windows. Now I removed all Windows partitions and want to use unallocated space for home, root...

My partition layout is surely not ideal. I have one extended SDA with all ubuntu partitions in it. Former Windows space is not inside it.

not allocated
/dev/sda4       extended
     ____/dev/sda5       ext4      root
     ____not allocated
     ____/dev/sda6       swap    root
     ____/dev/sda7       ext4     home

What can I do to optimize my partition layout and resize root and home?! Currently gparted does not allow me to resize my partitions. I think because of the extended SDA?!

---

### Post by yancek on 2017-02-11
Posting the output of the command:  sudo fdisk -l(lower case letter L in the command) would be useful.

It depends upon what you want.  If you have an already functioning Ubuntu installed and want to use the space previously used by windows, you can simply create partitions and format the space to use and mount it as a data partition.  That would probably be the simplest.  You could also move the /home or / system partition, moving home would likely result in less potential for harm.  Post the output of fdisk.

---

### Post by ajgreeny on 2017-02-11
A screenshot of the gparted window would also be useful as it will show the physical layout of free space and partitions on the disk and their sizes. Without that info it is impossible to know what is possible or sensible to consider.

Nevertheless I am with yancek here, and would advise you at this stage not to mess around moving your current Ubuntu partitions which might upset the grub boot system, but simply to use the unallocated space as a new ext4 partition, and use it as data or backup or whatever you want.
We can easily arrange for that partition to be mounted at boot and available to you as a read/write partition once we know what you would like to do.

---

### Post by ajgreeny on 2017-02-11
A screenshot of the gparted window would also be useful as it will show the physical layout of free space and partitions on the disk and their sizes. Without that info it is impossible to know what is possible or sensible to consider.

Nevertheless I am with yancek here, and would advise you at this stage not to mess around moving your current Ubuntu partitions which might upset the grub boot system, but simply to use the unallocated space as a new ext4 partition, and use it as data or backup or whatever you want.
We can easily arrange for that partition to be mounted at boot and available to you as a read/write partition once we know what you would like to do.

---

### Post by DB4711 on 2017-02-12
Hello,

thanks for your answers. Yes, it will be best to add a new partition and don't play around with grub and so on ;)

---

### Post by ajgreeny on 2017-02-13
Great news!

Please mark as SOLVED from the Thread Tools menu up-top if this query is now answered to your satisfaction. It is a great help to users searching the forum.

---

