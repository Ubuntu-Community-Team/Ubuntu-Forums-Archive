---
title: "Edgy usplash theme very dark"
date: 2006-11-02
forum: General Help
---

### Post by kevinatkins on 2006-11-02
Hi,

I've just upgraded from Dapper to Edgy, doing a dist-upgrade.

Everything seems to be fine, except that the usplash screen shown during boot is very dark. At first, I thought the screen had gone blank, but looking carefully, I can see the Ubuntu logo and progress bar - they're just very very dark, except for the last 0.5 second or so, when the screen briefly flashes at the correct brightness just prior to starting X.

Has anyone else noticed this? I've tried rebuilding the initrd image with a lower usplash resolution, changing framebuffer resolutions, to no avail.

Any help would be welcome - the new scheme looks good.

Many thanks,

Kevin.

---

### Post by kevinatkins on 2006-12-06
OK, I've finally managed to sort this out, and thought I'd document here in case anyone else is having similar problems..

It seems that on my system, with the vesa framebuffer running at default resolution / colour depth (800x600 / 8 bit colour), that was the cause of the problem. Resetting the colour depth to 16 bits solved the brightness problem. I did this by appending 'vga=788' to the kernel boot options in /boot/grub/menu.lst. I had tried higher resolutions before, but kept getting 'undefined mode number' errors - looks like my hardware will only run at 800x600 on the framebuffer.

The final thing I had to do was correct the now off-centre (off-center) splash - I did this by resetting the resolution to 800x600 in /etc/usplash.conf and then running 'sudo update-initramfs -u' - finally I have a nice splash screen!

---

### Post by ivomans on 2006-12-25
Kevin: thanks for sharing your solution here. I had the same problem and adding the ´vga=788' solved the issue for me as well.

---

