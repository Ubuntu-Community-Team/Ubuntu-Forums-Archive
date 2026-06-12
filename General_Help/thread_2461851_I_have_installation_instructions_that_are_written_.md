---
title: "I have installation instructions that are written in Greek"
date: 2021-05-08
forum: General Help
---

### Post by dora5 on 2021-05-08
I need to put memtest86 on a usb drive.

Here are the instructions.

1. Download the MemTest86 USB image.
2. Unzip the package (unzip memtest86-usb.zip). An image file and a readme.txt file will be created in the
current directory.
3. Plug in the USB drive
4. Determine which device the USB drive is assigned as (eg. /dev/sdc)
5. As root, use the 'dd' command to write the image to the USB drive. For example,
sudo dd if=memtest86-usb.img of=<dev>
where <dev> is the device the USB key is assigned to. Use the base device (ie. /dev/sdc) not a partition
designation (ie. /dev/sdc1).

I need to know EXACTLY what to do.  "as root" is some kind of a Chinese term that seems to have several very different real life meanings.

I tried it in the home directory and in /Downloads/Memtest which is where the files are.  Neither worked.

The command I typed was sudo dd if-memtest86-usb.img of=/dev/sdb which is the usb drive.   

I'm at work and I need to use memtest86 on the usb drive right now - not research stuff.  I just need someone to give me the commands to use.

I'm using Ubuntu 18.04.

Thanks!

Yours,
Dora Smith

---

### Post by Holger_Gehrke on 2021-05-08
You have a typo in the dd command:
> 
sudo dd if[COLOR=#ff0000]-[/COLOR]memtest86-usb.img of=/dev/sdb

should be
```

sudo dd if[COLOR=#00ff00]=[/COLOR]memtest86-usb.img of=/dev/sdb

```
'if=' means 'set the **i**nput **f**ile to'. With a dash instead of the equal sign the command makes no sense and dd should print 'dd: unrecognized operand ...'  and tell you to read the help.

The 'as root' thing is already taken care of by prefixing the dd command with 'sudo' (**s**witch **u**ser and **do**; if you don't tell sudo to switch to a specific user it will switch to 'root' - which is the administrative user account).

Holger

---

### Post by dora5 on 2021-05-08
Thanks!   I bet I had an actual equal sign when I used it.   It didn't seem to work though.

Won't be testing it - it suddenly occurred to me all I had to do was boot into Windows.  Works slllloooooooooooowly but there.

But thanks!

Dora

---

