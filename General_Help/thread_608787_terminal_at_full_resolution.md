---
title: "terminal at full resolution"
date: 2007-11-10
forum: General Help
---

### Post by eldragon on 2007-11-10
hi, is there a way to have the terminals at [ctrl][alt][fx] on the native resolutions of my screen?

ive got a 1680x1050 screen and would love to have the terminals at that resolution instead of the crappy 640x480 or 800x600 or whatever it defaults on?

i use the terminals a lot and feel im missing out with those big fonts :(

thanks

---

### Post by Lem on 2007-11-10
You can add a vga option to grub for the default frame buffer;

vga=xxx

         640x480   800x600   1024x768   1280x1024   1600x1200   Ask user at boot.
8 bits   vga=769   vga=771   vga=773    vga=775     vga=796     vga=ask
16 bits  vga=785   vga=788   vga=791    vga=794     vga=798     vga=ask
32 bits  vga=786   vga=789   vga=792    vga=795     vga=799     vga=ask

For a temporary try; press esc at the grub loader stage, then e to edit, and e again to edit the first boot line.. add your vga option to the end

To do permanently..

edit /boot/grub/menu.lst

---

### Post by hamsteroid on 2007-11-17
Hi,

I tried the above, by adding **vga=795** to my kernel line to /boot/grub/menu.lst and removing the splash and quiet parameter. Upon reboot I don't see anything until I get to the login screen. I have ubuntu 7.10 and a Nvidia GT7600 which works fine anyway. I have the latest restricted drivers installed which I accepted when installing Gusty. My native lcd res is 1280x1024.

I also tried editing at boot time instead of editing the menu.lst file. The same blank screen result until login time.

Can anyone help me in trying something else? I would really like to be able to use the plain terminal at 1280x1024 or 1024x768?

---

### Post by zeax on 2007-11-18
edit /etc/initramfs-tools/modules 

 ```
sudo vi /etc/initramfs-tools/modules 
```

and adding these:
```

fbcon
vesafb
vga16fb 
```

than 
```
sudo update-initramfs -u  
```

---

