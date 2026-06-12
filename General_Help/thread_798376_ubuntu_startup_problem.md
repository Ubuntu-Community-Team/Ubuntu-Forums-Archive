---
title: "ubuntu startup problem"
date: 2008-05-18
forum: General Help
---

### Post by Sinmok on 2008-05-18
Hiyo.

I recently decide to give linux a try and just recently installed ubuntu 8.
Before we start I must warn you i've never actually used any linux distribution before, so i'm a total rookie..

Anyway, to the point.

When I turn on my computer, I come to this bootup screen where it says something along the lines of:

*(my apologies if these aren't the correct numbers...*)
ubuntu linux generic 2.0.26 <**----The one that doesn't work!**
ubuntu linux generic 2.0.26 (recovery)
ubuntu linux generic 2.0.24 **<---- The one I have to manually select every time !**
ubuntu linux generic 2.0.26(recovery)
ubuntu linux generic 2.0.20
ubuntu linux generic 2.0.26(recovery)
ubuntu linux memtest (something like that)
Other operating systems:
Windows XP professional

Basically, my problem is that my default it is loading the 2.0.26 version, but, unfortunately, after the loading screen, (the ubuntu orange bar thing) the screen just hangs in a black screen. Therefore i'm forced to manually select the working version of 2.0.24 every time, which can get a little frustrating.

Does anyone know why the bootup isnt working? Or how I can just select the working version to be the default bootup?

Much appreciation in advance for any help.

---

### Post by TeoBigusGeekus on 2008-05-18
Post us the contents of your menu.lst file
```
gksudo gedit /boot/grub/menu.lst
```
(.LST)

---

### Post by Sinmok on 2008-05-18
## ## End Default Options ##

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=2c149ce1-d780-4051-a375-3b03365f44b5 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=2c149ce1-d780-4051-a375-3b03365f44b5 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, kernel 2.6.22-14-generic
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=2c149ce1-d780-4051-a375-3b03365f44b5 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 8.04, kernel 2.6.22-14-generic (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=2c149ce1-d780-4051-a375-3b03365f44b5 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 8.04, kernel 2.6.20-16-generic
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=2c149ce1-d780-4051-a375-3b03365f44b5 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.20-16-generic (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=2c149ce1-d780-4051-a375-3b03365f44b5 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd1,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by TeoBigusGeekus on 2008-05-18
Somewhere in the file, before these entries, there should be a line
```
default 0
```
Change that to 
```
default 2
```
to have grub load the stable kernel.

---

### Post by Sinmok on 2008-05-18
Wow, worked perfectly. You the MAN!

Cheers.

---

### Post by TheHL2Guy on 2009-12-12
I think the problem is the update. I't doesn't work. That's the problem but i dont know how to solve it :?

I have a startup problem too. Chek it out:
[http://ubuntuforums.org/showthread.php?t=1353295](http://ubuntuforums.org/showthread.php?t=1353295)


-TheHL2Guy Productions

---

