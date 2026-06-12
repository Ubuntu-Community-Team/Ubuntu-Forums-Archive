---
title: "can't start ubuntu after wubi install"
date: 2008-04-28
forum: General Help
---

### Post by jf pion on 2008-04-28
hello

I've installed ubuntu with wubi over XP on O: partition 240 Go with the max size. no pb during the install (4th sata disk 1 To 4 partition, 4 sata disk on mother board, 3 more ide drive on an ide controller card each of them easely open with live CD)

when I try to boot on ubuntu (the choice system work nicely) I get the message :

configfile /ubuntu/install/boot/grub/menu.lst
filename must be either an absolute pathname or blocklist

all the other choice give the same result
I have nothing in the O:\ubuntu\disk\boot\grub

in the C: i only have wubildr and wubildr.mbr, in the boot.ini I have :c:\wubildr.mbr="Ubuntu"

2 install with the file directly downloaded

If I try a normal install ( I have plenty of room) does the system respect the grub (for mandriva 2008.1) or will I have to redo the grub config manually ?

thank a lot

---

### Post by tinybit on 2008-04-28
Can you type in the following command at the grub prompt?

```

rootnoverify ()
find --set-root  /ubuntu/install/boot/grub/menu.lst
configfile  /ubuntu/install/boot/grub/menu.lst

```

Press c to gain the grub prompt and you can input commands there.

You may also experiment with this:

```

configfile  /

```

after "/" you may hit Tab and see if there is ubuntu in the "/" directory.

BTW, at the top of the screen there should be a grub4dos version string. So what version string you can see?

---

### Post by manlyman on 2008-04-29
....Have you tried restarting your computer?

---

### Post by tinybit on 2008-05-01
A bug was found on configfile. Please try the latest build of grub4dos:

[http://grub4dos.jot.com/WikiHome/grub4dos-0.4.3-2008-05-01.zip](http://grub4dos.jot.com/WikiHome/grub4dos-0.4.3-2008-05-01.zip)

Thanks for the report.

---

### Post by dartdog on 2008-05-02
I downloaded the file and extracted it but now what, what do I run? do I need to set parameters? or has this been incorporated to the ISO for the whole system and should I just get a new disk image and start over?

---

