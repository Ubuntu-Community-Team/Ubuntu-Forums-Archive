---
title: "Wont dual boot ubuntu, defaults to XP"
date: 2007-10-15
forum: General Help
---

### Post by tvetter05 on 2007-10-15
I think I had a successful installation of 7.04 (alternate download ISO), but when I rebooted after installation, it booted up XP-64bit, and it continues to default to XP.  I put the CD back in and went to boot from first hard disk and it loaded Ubuntu and showed the login screen perfectly.  After logging in it only showed a orange screen, my mouse cursor and some garbled pixels and my P/S2 keyboard wouldn't work (mouse is USB).
I also tried the recovery mode to reinstall GRUB but that had no effect.  
I installed on 2nd IDE master and XP is on a SATA RAID 0.
Help please. I'm a Linux newb btw.   

I think I made /root and /swap for partitions.  

AMD Athlon X2 4400+
2 GB PC3200
2x WD 250gb SATA 7200 rpm 16mb Cache in RAID 0
40gb western digital 7200rpm drive
Nvidia GeForce 7800gt 
Asus A8N SLI-Deluxe
Windows XP 64-bit Professional

---

### Post by darksizzle on 2007-10-16
If you are doing a sata and an ide combination there should be an option in your bios that let's your choose your hard drive boot order.  At least that's what the deal is on our boxes at work.  Your ide ubuntu drive needs to be the first to boot for grub to be found.

---

### Post by tvetter05 on 2007-10-16
Thanks, changing the disk boot priority worked, but once Ubuntu is booted the GUI is all messed up and I cant do any thing but move my mouse.

---

### Post by tvetter05 on 2007-10-16
Do I need to instal video drivers or repair the GUI package or what?

---

### Post by confused57 on 2007-10-16
> **tvetter05 said:**
> Do I need to instal video drivers or repair the GUI package or what?
You can try changing your video driver to "vesa", in order to boot to a GUI...boot into Recovery mode, enter:
```
nano /etc/X11/xorg.conf
```
make sure to use an uppercase X and (one)(one)

Page down to the video device driver...Ubuntu probably assigned "nv" as the driver, change it to "vesa"(with quotes)...then Ctrl+x, y, enter...this will save the file.  Then I believe all you have to do now is press "Esc" to boot to a GUI(hopefully)...if not, try rebooting.

If you're able to boot to a GUI, you could use Envy to install Nvidia drivers for your card:
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

