---
title: "Supergrub doesn't load."
date: 2007-11-24
forum: General Help
---

### Post by henthorn on 2007-11-24
I can't boot because I get the Grub Loading stage 1, error 17 message.  I have burned an iso of supergrub and it appears on the CD.  However, I have the CD drive set as the first boot choice in Bios but when I try to boot the CD drive light flickers a couple of times and then it goes back to the Grub Loading stage 1.5, error 17 message. I am not too sharp with computers.  What might be the problem?

---

### Post by kellemes on 2007-11-24
Have you burned SGD the ISO-image? Instead of simply burning the file?
See here for instructions.. simply replace the LiveCD with SGD..
[https://help.ubuntu.com/community/BurningIsoHowto]("https://help.ubuntu.com/community/BurningIsoHowto")

---

### Post by kellemes on 2007-11-24
delete.

---

### Post by ajgreeny on 2007-11-24
Or try the following:-

Boot into the ubuntu live CD
open a terminal and run :
    sudo grub
This gets you to a simple grub command line.
Then:
    find /boot/grub/stage1
This will tell you where your /boot/grub/stage1 is which is needed to boot ubuntu. Replace the question marks in the following command with the output of the this last command :
    root (hd?,?)
[like : root (hdo,1) ,probably]
then:
    setup (hd0)
This is where your windows partition and MBR normally is, but if you want grub on another disk, use hd1, etc as appropriate. It's much easier to use the windows MBR and then just change the default boot system later if others in the family demand windows boots by default.
Then:
    quit
Finally reboot, and hopefully you will now have a working grub bootloader.

---

### Post by henthorn on 2007-11-25
> **ajgreeny said:**
> Or try the following:-

Boot into the ubuntu live CD
open a terminal and run :
    sudo grub
This gets you to a simple grub command line.
Then:
    find /boot/grub/stage1
This will tell you where your /boot/grub/stage1 is which is needed to boot ubuntu. Replace the question marks in the following command with the output of the this last command :
    root (hd?,?)
[like : root (hdo,1) ,probably]
then:
    setup (hd0)
This is where your windows partition and MBR normally is, but if you want grub on another disk, use hd1, etc as appropriate. It's much easier to use the windows MBR and then just change the default boot system later if others in the family demand windows boots by default.
Then:
    quit
Finally reboot, and hopefully you will now have a working grub bootloader.

Thanks ajgreeny,

I tried that.  When I typed in find /boot/grub/stage1 I got an Error 15: File not found message.

---

### Post by henthorn on 2007-11-25
OK.  I finally made a copy of supergrub that works.  At least it boots up.  However no matter what I try I still keep getting the Error 15, File not found message.

---

### Post by henthorn on 2007-11-25
Worked a little more and was able to open the XP partition, but get the Error 15 message when I tried to open the Ubuntu partition with supergrub.

---

