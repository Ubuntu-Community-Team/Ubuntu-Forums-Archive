---
title: "problem with ubuntu boot splash"
date: 2007-02-27
forum: General Help
---

### Post by mackinax on 2007-02-27
Unless I remove the boot "splash" option (from menu.lst), my monitor gives a "frequency over range" error during the splash stage at bootup. Either way, everything is fine once X starts.

I don't really mind having a text bootup, but I'd still like to know how to fix this.

Thank you

---

### Post by louis_nichols on 2007-02-28
Try setting the vga mode when booting. This is done by adding a parameter vga=xxx at the end of the kernel boot parameters. Available options are:


   ```
# VESA framebuffer console @ 1024x768x64k
   vga = 791
   # Normal VGA console
   # vga = normal
   # VESA framebuffer console @ 1024x768x64k
   # vga=791
   # VESA framebuffer console @ 1024x768x32k
   # vga=790
   # VESA framebuffer console @ 1024x768x256
   # vga=773
   # VESA framebuffer console @ 800x600x64k
   # vga=788
   # VESA framebuffer console @ 800x600x32k
   # vga=787
   # VESA framebuffer console @ 800x600x256
   # vga=771
   # VESA framebuffer console @ 640x480x64k
   # vga=785
   # VESA framebuffer console @ 640x480x32k
   # vga=784
   # VESA framebuffer console @ 640x480x256
   # vga=769
```

You should choose a compatible one. Fo example, I run my desktop at 1280x960 and use vga=791 at boot.

Or maybe this can be solved by reconfiguring usplash:

```
sudo dpkg-reconfigure usplash
```

---

### Post by mackinax on 2007-02-28
Thank you Louis.

I've tried setting the VGA mode and it made no difference. I now reconfigured ''usplash'' per your suggestion, and it also didn't help.

> > sudo dpkg-reconfigure usplash
update-initramfs: Generating /boot/initrd.img-2.6.17-11-generic

Is the generation of usplash dependant upon variables that are set during installation? Because the auto-detection of my video hardware at installation was messed up, I had to reconfigure X11 right away. Maybe something else needs to be changed first for the usplash to be generated correctly?


correction: ''vga=769'' doesn't give a frequency error - just a blank screen

---

### Post by mackinax on 2007-02-28
I searched for the terms ''reconfigure usplash'' and found out that there is a usplash configuration file: ''/etc/usplash.conf''

It did infact contain wonky settings from the install auto-detect (4096x4096) - so I changed it to 1024x768 and then ran ''dpkg-reconfigure usplash'' again, now the splash works fine!

Thanks Louis. :)

---

### Post by louis_nichols on 2007-02-28
Welcome! Glad it's sorted! :)

---

### Post by filogo on 2007-03-28
Thank you, same problem here. There was a incoherence between boot vga setting and the usplash.conf. Now with a 1280x800 screen I boot perfectly with resolution 1024x768 in usplash.conf and vga=768 in /etc/grub/menu.lst :)

---

### Post by graabein on 2007-04-01
Same thing happened to me. I knew about the vga boot option but was unaware of the usplash config-file. Looks great now.



EDIT: False alarm. The (Xubuntu) boot splash is too far to the right and down. Not centred. Not aesthetic.[LIST]
[*]*/etc/usplash.conf* says 1280x1024
[*]*/boot/grub/menu.lst* says vga=791
[*]*/etc/X11/xorg.conf* says 1024x768 with default depth = 24
[/LIST]
I've tried adjusting all of them but no luck. Rats!!

---

### Post by louis_nichols on 2007-04-02
> **graabein said:**
> Same thing happened to me. I knew about the vga boot option but was unaware of the usplash config-file. Looks great now.



EDIT: False alarm. The (Xubuntu) boot splash is too far to the right and down. Not centred. Not aesthetic.[LIST]
[*]*/etc/usplash.conf* says 1280x1024
[*]*/boot/grub/menu.lst* says vga=791
[*]*/etc/X11/xorg.conf* says 1024x768 with default depth = 24
[/LIST]
I've tried adjusting all of them but no luck. Rats!!

usplash doesn't take that big resolutions. Use something like 1024x768 (or another value, proportional to your screen size) in usplash.conf. My normal resolution on the monitor is 1280x960, but I use 1024x768 for usplash. After this, run a *dpkg-reconfigure usplash* and it will be ok.

EDIT: let me rephrase: it looks like usplash would accept the higher resolution, but it can't be displayed on it because of the vga option in menu.lst. So, the resolution set for usplash needs to be exactly the same with the one configured using the vga option. otherwise, it will indeed look off center. Unfortunately, the vga option is pretty limited in range. It's not that bad, though. Usplash looks pretty cool in lower res, too.

---

### Post by Derspankster on 2007-10-27
I have the same issue and have tried all that has been suggested with no success. My issue with the off center usplash actually began before I upgraded to Gutsy while I was still running Feisty.  I have no idea when it happened but when I first installed Feisty it was OK. My usplash is currently set at 1024/768 and my screen resolution is 1280/1024. I've tried resetting upslash to 1280/1024 and that results in a screen that is off center to the right and not the left. Upon reboot the usplash returns to off center left. My vga=791 and I have not tried altering that. I've reconfigured usplash after each attempted change.

---

### Post by wooster_borg on 2007-10-30
Thanks a Bunch, I had the same "Out of Frequency " problem with gutsy and the solution works like a charm !! I love Ubuntu !!!! :D

---

