---
title: "cannot unmount drive"
date: 2013-09-22
forum: General Help
---

### Post by jj4 on 2013-09-22
I am trying to clone a usb to another usb (bootable).
I used dd to do this but the other drive does not boot so I wanted to wipe it and start again.
However, I cannot unmount the 2nd USB. It says it is mounted to /
I trie din gparted then I tried sudo umount but it can't find the drive.
Any ideas what to try next?

```

j@spain ~ $ df
Filesystem           1K-blocks    Used Available Use% Mounted on
/dev/sdb1             15388032 9750456   4855908  67% /
udev                   1998092       4   1998088   1% /dev
tmpfs                   803532    1104    802428   1% /run
none                      5120       0      5120   0% /run/lock
none                   2008828     632   2008196   1% /run/shm
none                    102400       8    102392   1% /run/user
/home/spain/.Private  15388032 9750456   4855908  67% /home/spain
jason@spain ~ $ sudo gparted
[sudo] password for jason: 
======================
libparted : 2.3
======================
^j@spain ~ sudo umount /dev/sdc1
umount: /dev/sdc1: not mounted
j@spain ~ $ 


```

[ATTACH=CONFIG]246428[/ATTACH]

---

### Post by TheFu on 2013-09-22
You cannot **umount** an actively used partition. That means if you are running from it, you can't umount it. 
Also, not every USB flash drive can be bootable. There seem to be incompatibilities between different flash makers and USB ports that I've never seen explained.  Using dd to clone a USB disk seems dangerous, unless they are 100% identical.  OTOH, I've never had much luck creating a multi-boot from Linux or [UNetBootIn]("http://unetbootin.sourceforge.net/") on either Windows or Linux .... oddly, [Yumi]("http://www.pendrivelinux.com/yumi-multiboot-usb-creator/") works every time, but it is a Windows tool.

For creating a single-OS bootable flash drive, I'd guess  [http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-ubuntu](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-ubuntu) would be the way I did it.  I always try to use the Ubuntu-based documentation first. I find it is created by people who know what they are doing and don't take unnecessary steps.

Sorry, didn't help with the dd issue, but hopefully, provided a way to get the task completed.

---

### Post by jj4 on 2013-09-22
> **TheFu said:**
> You cannot **umount** an actively used partition. That means if you are running from it, you can't umount it. 
Also, not every USB flash drive can be bootable. There seem to be incompatibilities between different flash makers and USB ports that I've never seen explained.  Using dd to clone a USB disk seems dangerous, unless they are 100% identical.  OTOH, I've never had much luck creating a multi-boot from Linux or [UNetBootIn]("http://unetbootin.sourceforge.net/") on either Windows or Linux .... oddly, [Yumi]("http://www.pendrivelinux.com/yumi-multiboot-usb-creator/") works every time, but it is a Windows tool.

For creating a single-OS bootable flash drive, I'd guess  [http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-ubuntu](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-ubuntu) would be the way I did it.  I always try to use the Ubuntu-based documentation first. I find it is created by people who know what they are doing and don't take unnecessary steps.

Sorry, didn't help with the dd issue, but hopefully, provided a way to get the task completed.

that's the problem, I plug the 2nd usb in and it thinks it is mounted on the actively used partition / but it isn't.
How can I have 2 USBs mounted to /
?

---

### Post by TheFu on 2013-09-22
If you used dd and both devices are identical, then both probably have the same UUID - can you check that?  Somehow, you need to make the UUID different on one of the flash drives .... or access them by device path, not UUID

That's the best I got. ;)

---

### Post by jj4 on 2013-09-22
> **TheFu said:**
> If you used dd and both devices are identical, then both probably have the same UUID - can you check that?  Somehow, you need to make the UUID different on one of the flash drives .... or access them by device path, not UUID

That's the best I got. ;)

I can't access it though at all? gparted can see it but when I use df, it doesn't list it.

---

### Post by TheFu on 2013-09-22
Use a 3rd boot device, then access each of the flash drives 1 at a time.
I must not understand something important. Sorry for my failure.

---

