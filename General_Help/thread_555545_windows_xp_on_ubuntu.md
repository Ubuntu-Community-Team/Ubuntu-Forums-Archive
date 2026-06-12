---
title: "windows xp on ubuntu"
date: 2007-09-20
forum: General Help
---

### Post by flykude on 2007-09-20
i downloaded the qemu software that would enable me run windows xp on my system without having to dual-booth,but any time i try to install,i get the following problem on my terminal window...i'll need your help on this as i am new to linux.please.
the output on the terminal displays this.:

flykude@flykude-laptop:~$ mkdir winxp
flykude@flykude-laptop:~$ cd winxp/
flykude@flykude-laptop:~/winxp$ qemu-img create winxp.img 9000M
Formating 'winxp.img', fmt=raw, size=9216000 kB
flykude@flykude-laptop:~/winxp$ qemu -boot d -hda winxp.img -cdrom /dev/cdrom -m 256-localtime
You do not have enough space in '/dev/shm' for the 256 MB of QEMU virtual RAM.
To have more space available provided you have enough RAM and swap, do as root:
umount /dev/shm
mount -t tmpfs -o size=272m none /dev/shm
Or disable the accelerator module with -no-kqemu
flykude@flykude-laptop:~/winxp$

---

### Post by ddrichardson on 2007-09-21
How much physical and swap RAM have you?

---

### Post by flykude on 2007-09-23
yeah, my physical ram size is 256 MB,and for the swap,i really dot know,but i suspect it is the culprit.i really would like to know how to increase its size without having to format my system.
thanks

---

### Post by kay65535 on 2007-09-23
Try looking for **gparted**: I'm not sure if it can resize partitions without deleting data, but if it can, you just have to make one of your other partitions smaller and make your swap partition bigger (or create one if you havent got one).

=> Just looked at their homepage: yes, it looks like it doesn't kill the data while resizing ;-) (I've never used it though.)

Good luck! :-P

---

### Post by ddrichardson on 2007-09-23
Increasing the swap space is not going to speed up the system. Virtualization  benefits from more memory, in this configuration a dual boot would provide better performance.

In any case, you can resize with gparted in the repos, then from the command line:```
sudo swapoff /dev/swappart
sudo mkswap /dev/swappart
sudo swapon /dev/swappart
```Obviously "swappart" is whatever the swap partition is.

Increased swap usage will also increase disk access and decrease the disks lifespan.

---

### Post by Ozeuss on 2007-09-23
> **flykude said:**
> i downloaded the qemu software that would enable me run windows xp on my system without having to dual-booth,but any time i try to install,i get the following problem on my terminal window...i'll need your help on this as i am new to linux.please.
the output on the terminal displays this.:

flykude@flykude-laptop:~$ mkdir winxp
flykude@flykude-laptop:~$ cd winxp/
flykude@flykude-laptop:~/winxp$ qemu-img create winxp.img 9000M
Formating 'winxp.img', fmt=raw, size=9216000 kB
flykude@flykude-laptop:~/winxp$ qemu -boot d -hda winxp.img -cdrom /dev/cdrom -m 256-localtime
You do not have enough space in '/dev/shm' for the 256 MB of QEMU virtual RAM.
To have more space available provided you have enough RAM and swap, do as root:
umount /dev/shm
mount -t tmpfs -o size=272m none /dev/shm
Or disable the accelerator module with -no-kqemu
flykude@flykude-laptop:~/winxp$
If you have 256MB of ram, you cannot allocate all of it to winxp, since ubuntu is already using it. unfortunately, 256 is not enough to run ubuntu and another OS in virtualization on top at decent speeds. i suggest you dual boot, or buy a memory card..

---

### Post by amightyo on 2007-12-18
I wish to hibernate and hence that is why I wish to increase swap partition as I made it 500MB and wish to increase it to 1GB or 2GB as I am using a 1GB RAM. When I try to hibernate the system hangs and complains of less swap size. I need a way of increasing without reformatting ubuntu as I have a lot of programs already running well and I dont want to reinstall the programs. Thanks so much.

---

