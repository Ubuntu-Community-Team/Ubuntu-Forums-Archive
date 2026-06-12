---
title: "Getting &quot;Installation failed&quot; when trying to create gparted live bootable usb"
date: 2014-07-20
forum: General Help
---

### Post by mwk29162 on 2014-07-20
Error says "could not move syslinux files in"/media/3720-2DA2" [Errno 2] No such file or directory. Maybe "tmp/tmpjPxhDn" is not an Ubuntu image?" When I try to boot with it it gets to the "Use at your own risk" warning and then stops at the blinking cursor and does nothing. I'm trying to format a hard drive for a Windows 8 installation and they say trying to use the gparted function in Ubuntu won't work. I have to use the gparted live. Can anyone help with these problems please, it would be very much appreciated! Thanks.

---

### Post by yancek on 2014-07-20
How are you trying to create this bootable image, what software are you using?  Is there a reason you can't burn it as an image to a CD?

---

### Post by mwk29162 on 2014-07-20
I'm using startup disk creator from ubuntu system tools. I could use the live cd if I had sn mt cd to burn but I don't That is why I'm trying to use the usb flash drive.

---

### Post by gedakc on 2014-07-20
You might try [tuxboot]("http://www.tuxboot.org/"), which was developed specifically to write images like the GParted Live .iso file to a USB flash drive.

---

### Post by mwk29162 on 2014-07-20
Tuxboot worked perfectly, thanks! Windows 8 will still not install tho. Guess I have to buy another hard drive. No matter what anyone says Linux will not run everything unless you got "state of the art' equipment. If you're rich enough to have that kind of equipment you can run anything you want no matter how much it suxs! I hate windows.

---

