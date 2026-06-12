---
title: "USplash uses wrong resolution at boot, right resolution at shutdown..."
date: 2007-11-05
forum: General Help
---

### Post by Mr. Picklesworth on 2007-11-05
In /etc/usplash.conf, I have xres=1280 and yres=1024. This is reflected when I shut down the computer.

However, usplash still uses 1024x768 when booting!

Here is the entry I am using to boot, from menu.lst:
```
title           Ubuntu 7.10, kernel 2.6.22-14-386
root            (hd1,1)
kernel          /boot/vmlinuz-2.6.22-14-386 root=UUID=fff83654-9e8f-45c4-8715-7ced31792b72 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-386
quiet
```

Should it be figuring this out via usplash.conf, or must I also set that somewhere else? (Is there a magical tool that will just do it for me?)

---

### Post by misfitpierce on 2007-11-05
Set new reso in there then open terminal and do

sudo update-initramfs -u

Should make new bootimage with usplash correct size. This needs to be fixed in hardy heron for sure. I saw this on mine and friends computers on 64 bit installs.

---

### Post by DasCrushinator on 2007-11-06
> **misfitpierce said:**
> Set new reso in there then open terminal and do

sudo update-initramfs -u

Should make new bootimage with usplash correct size. This needs to be fixed in hardy heron for sure. I saw this on mine and friends computers on 64 bit installs.

I did this and never got an error during any of it, but I rebooted and it still doesn't work for me.

Is it maybe because I have a widescreen (1440x900) monitor?

---

### Post by Ehtetur on 2007-11-07
I have  the same issue with the fingerprint usplash theme on a wide screen monitor ...
The answer the maker of the fingerprint usplash theme gave regarding using it on widescreens may or may not apply to you...

Basically, he didn't have a widescreen availble for testing his usplash theme.

---

### Post by namanbagga on 2007-11-07
[Here's]("http://www.namanb.com/2007/11/ubuntu-710-bootup-resolution-problem.html") the complete solution to the problem

---

### Post by Mr. Picklesworth on 2007-11-07
Unfortunately, I am morally opposed to writing my screen resolution into any more than 2 configuration files. (Doing usplash's is ugly enough). I will just suffer, then be very happy and thankful when someone comes up with a more clever system.

Thank you for the solution, though!

---

### Post by Rocket2DMn on 2008-02-11
Wrong thread, disregard.  Sorry.

---

