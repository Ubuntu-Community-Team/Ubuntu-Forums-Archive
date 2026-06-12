---
title: "Grub - Usplash &quot;you passed an undefined mode&quot;"
date: 2007-11-21
forum: General Help
---

### Post by therealbrewer on 2007-11-21
My laptop has 1600x1200 native resolution. I want to set the Usplash screens to use this resolution. So I edited /etc/usplash.conf to have

xres=1600
yres=1200

Then I did

sudo dpkg-reconfigure -phigh usplash

As I understand it, this created new splash screens in the proper resolution.

Then I added

vga=799

to the end of the kernel line in /boot/grub/menu.lst to set the resolution.

Problem is however, upon booting, I get a "you passed an undefined mode" error. If I delete the vga=799, and change the usplash.conf back to 1280x1024, then Usplash comes up in 1280x1024 with no error, and then Gnome starts up in 1600x1200 as usual, but this is not what I want. I tried vga=798 and 797 as well (lower color 1600x1200 modes) but got the same error.

Is there a way to determine allowable modes with grub? Is there something else I can do to make 1600x1200 work? I assume these are Vesa modes since this all happens before the NVidia driver is loaded. Is there some way to determine what 1600x1200 Vesa modes will work with my hardware?

Help please!

---

### Post by therealbrewer on 2007-11-21
OK, well I have more info. Apparently my laptop screen has incorrect info in it's EDID:

```
~$ sudo ddcprobe

vbe: VESA 3.0 detected.
oem: NVidia
vendor: NVidia Corporation
product: NV11 Board Chip Rev B2
memory: 32768kb
mode: 640x400x256
mode: 640x480x256
mode: 800x600x16
mode: 800x600x256
mode: 1024x768x16
mode: 1024x768x256
mode: 1280x1024x16
mode: 1280x1024x256
mode: 80x60 (text)
mode: 320x200x64k
mode: 320x200x16m
mode: 640x480x64k
mode: 640x480x16m
mode: 800x600x64k
mode: 800x600x16m
mode: 1024x768x64k
mode: 1024x768x16m
mode: 1280x1024x64k
edid: 
edidfail


```

So, even though my monitor can do 1600x1200, grub can't know that because the monitor won't tell it.

Is there any way to override this and tell grub to use the 1600x1200 anyway???

---

