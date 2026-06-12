---
title: "just upgraded to 6.10"
date: 2006-11-01
forum: General Help
---

### Post by Magiczero on 2006-11-01
hi

I just upgraded my dell computer to 6.10!  I like it but a few problems!  

1.  When I boot up i see the grub and kernel but i see no ubuntu logo with progress my screen goes blank 
Then once it checks everything I see the username box then once i login everything is fine!!!  

My screen res right now is set at 1280 x 1024....  I am pretty sure that before I did the upgrade it was set at 1280 x 800.

Can someone help please?
Thanks

Note:  I did the upgrade from 6.06 to 6.10 using update maniger

---

### Post by autocrosser on 2006-11-01
I can't give you the exact answer, but I can point out the path---in your /boot/grub/menu.lst there is a section where you can specify the vga setting--I don't know what the setting you need is, but I would say that's the problem-- You might also take a look at /etc/usplash.conf--it should say xres=1280 yres=1024

look for the section in /boot/grub/menu.lst---

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash elevator=cfq

I think you need vga=793--but don't quote me--the next option--elevator=cfq changes some defaults:D

---

### Post by LenzM on 2006-11-01
> **autocrosser said:**
> I can't give you the exact answer, but I can point out the path---in your /boot/grub/menu.lst there is a section where you can specify the vga setting--I don't know what the setting you need is, but I would say that's the problem-- You might also take a look at /etc/usplash.conf--it should say xres=1280 yres=1024

look for the section in /boot/grub/menu.lst---

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash elevator=cfq

I think you need vga=793--but don't quote me--the next option--elevator=cfq changes some defaults:D

1280x1024 is vga=794
from
[https://help.ubuntu.com/community/USplashCustomizationHowto](https://help.ubuntu.com/community/USplashCustomizationHowto)

I had the same problem on my machine at work, so I'm going to try this tomorrow too.

---

