---
title: "cant copy xorg.conf from livecd"
date: 2007-02-08
forum: General Help
---

### Post by embersfade on 2007-02-08
hey guys... recently i tried installing beryl. didnt turn out too well. X wont load at all for me now, and i have no clue what im doing in a terminal.
can anyone tell me how to copy the xorg.conf file from my live cd to my HD?
i dont know how to mount my HD. last time i tried, nothing happened.
any help is greatly appreciated.

Thanks!

---

### Post by amohanty on 2007-02-08
When you boot up the nex time, press ESC and you will see the grub menu.

Pick the option that says recovery mode and it will drop you to a root shell. 
Drop in the cd and at the command prompt type:

mount /media/cdrom0

That will mount your cd for you. THen do the following:

cd /etc/X11
cp /media/cdrom/<whereever the xorg.conf file is> .

I dont have a live cd so cant tell you where to find the file. Also whenever the dpkg-reconfigure util is used it creates a backup, so you might not need to copy from cd. 

just look for a file called xorg.conf.<some number indicating date and time> and copy that to xorg.conf

HTH
AM

---

### Post by bodhi.zazen on 2007-02-08
From the live CD:

To list your partitions : ```
sudo fdisk -l
```

To copy :

```
suod mount /dev/hdxy /mnt
sudo cp /etc/X11/xorg.conf /mnt/etc/X11
```


Where hdxy is your ubuntu root partition ...
[indent]/dev/hda2 perhaps[/indent]

To re-configure X

Boot to HD

In a terminal type : ```
sudo dpkg-reconfigure -phigh xserver-xorg
```

amohanty : 

FYI looking at the Ubuntu CD

> ls /mnt/cd/
md5sum.txt  isolinux  programs   start.ini    README.diskdefines  pool
casper      bin       start.bmp  ubuntu.ico   dists               preseed
install     disctree  start.exe  autorun.inf  pics                ubuntu

HTH

---

