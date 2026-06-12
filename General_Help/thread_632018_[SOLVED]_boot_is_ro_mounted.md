---
title: "[SOLVED] /boot is ro mounted"
date: 2007-12-05
forum: General Help
---

### Post by airman_dopey on 2007-12-05
Greetings all.

First and foremost, let me say that this program is by far the coolest I have seen this year. I didn't think dual booting was possible this way, but it has really come in handy. I am currently deployed to the middle east and cannot under any circumstances mess up my laptop. So Wubi is perfect for me to have Linux on my computer.

That being said, I have been trying to update the bootup splash screen and am having a problem writting to boot. What I have done so far is downloaded an .so file from Gnome Eye Candy, ran the code ```
sudo update-alternatives --config usplash-artwork.so
``` and selected the new splash screen, then ran ```
sudo update-initramfs -u
``` At that point it gives me this error:

WARNING: /boot is ro mounted.
update-initramfs: Not updating /boot/initrd.img-2.6.22-14-rt

I have tried editing menu.lst and changing all of the RO to RW and gone into windows and made the ubuntu directory NOT read only (hope that makes sense) and it will still not work. I know the splash screen is working because it changed the powerdown splash. Just not the boot up. Thanks in advance to anyone willing to help

-Dopey

---

### Post by colo on 2007-12-05
As a one-time-solution, ```
sudo mount -o remount,rw /boot
``` should be OK.

---

### Post by anon2243 on 2007-12-05
I had the exact same problem and doing this helped:

mkinitramfs -o /boot/initrd.img-`uname -r`

---

### Post by airman_dopey on 2007-12-05
The code:

```
sudo mount -o remount,rw /boot
```

Actually didn't do anything for me. Gave the same error. However, the last post did it exactly. My boot up splash is now set the way I want it. Now to figure out how to change that hideous brownish-orange color to black just before the login screen is all I have left.

Either way, Thank you so very much for your help!

-Dopey

---

### Post by ago on 2007-12-06
create a new initrd without updating it, see above suggestion

---

### Post by anon2243 on 2007-12-07
glad i could help you from hours of mindless googling :)

---

