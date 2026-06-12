---
title: "Pre boot pictures?"
date: 2019-05-05
forum: General Help
---

### Post by aughey on 2019-05-05
Back in the day when I had an Amiga A1200 it could display a pre boot picture. I see Windows 10 has nicked the idea. Can Ubuntu perform the same trick and if so how?

---

### Post by TheFu on 2019-05-05
A doubt any computer can display an image before the BIOS is displayed, but you can replace the splash screen.
[https://www.howtoforge.com/tutorial/grub-2-boot-loader-menu-and-splash-screen-image/](https://www.howtoforge.com/tutorial/grub-2-boot-loader-menu-and-splash-screen-image/)
and
[https://help.ubuntu.com/community/Grub2/Displays#Creating_User_Splash_Images](https://help.ubuntu.com/community/Grub2/Displays#Creating_User_Splash_Images)

Sometimes knowing the correct term to feed google helps. "splash"

I just did this by placing an image that meets the required specifications into /boot/grub/, then running
```
$ sudo update-grub
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found background image: Brooks_River_Bears.png
Found linux image: /boot/vmlinuz-4.15.0-48-generic
Found initrd image: /boot/initrd.img-4.15.0-48-generic
Found linux image: /boot/vmlinuz-4.15.0-47-generic
Found initrd image: /boot/initrd.img-4.15.0-47-generic
Adding boot menu entry for EFI firmware configuration
done

```
Seemed pretty easy.  The image you want probably needs to be resized to the natural size for the screen - 1920x1080 or 1280x768. If you use .png, then it only needs be RGB and non-indexed.  If you use .jpg, it can only have 8-bit colors (256).

---

### Post by TheFu on 2019-05-05
Didn't work for me.

So, I followed the easy instructions, but didn't reboot until a few hours later.  It didn't work on my system. Could have been the encryption, the use of LVM or because I use a different login manager. IDK.```

$ file B*g
Brooks_River_Bears.png: PNG image data, 1620 x 1080, 8-bit/color RGB, non-interlaced
```
which I think should work on this machine.  It is 1920x1080 native resolution.

---

