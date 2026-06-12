---
title: "Terminal Video Issue"
date: 2007-02-08
forum: General Help
---

### Post by ahsile on 2007-02-08
Ever since I upgraded to Edgy I've had a problem with the terminal while I'm logged into an xorg session. If I boot into recovery mode, there are no issues whatsoever.

What happens, is that whenever I swap to a terminal (CTRL-ALT-[F1->F6]) the screen comes up entirely mangled (I have attached a picture with a link to a full res image on my personal site).

[[IMG]http://zenwerx.com/personal/gallery/thumbs/e6be484409f5e1621d86ea44b3999351.JPG[/IMG]]("http://zenwerx.com/personal/gallery/index.py/Screenshots/IMG_2709.JPG")

I have an ATI X800 graphics card running on a P4 2.8G machine. I am running kernel 2.6.17-10, although this has been happening with older kernels as well, and the fglrx driver for my ati card. The monitors in the picture are 20" wide screen lcds, but this issue has persisted since before I got them and was using dual 17" crts.

Does anyone have ideas on how to fix this?

---

### Post by Deliann on 2007-02-10
> **ahsile said:**
> Does anyone have ideas on how to fix this?

Had the exact same problem (nice picture!) with my ATI Radeon Mobility X1700 until a moment ago.

I'll say it's the fglrx driver's fault: wasn't experiencing the problem prior to using it. (But "have" to use it, damn exotic video card . . .)

After searching the forums I was able to fix it on the second try with info from [this thread]("http://ubuntuforums.org/showthread.php?t=28220") by 

```
sudo gedit /boot/grub/menu.lst
```

And then adding the "vga=792" part to

```
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/sda3 ro quiet splash vga=792
```

Means to use a resolution of 1024*768 at 24 bit.

I tried 795 (1280x1024@24bit) at first but that was refused at boot time and I had to choose from a bunch of other available values.

Hope that helps, and many thanks to ATI for some quality work. >:(

---

### Post by ahsile on 2007-02-11
Thanks for the reply! That got it up and working nicely. I tried the 1280x1024 first, but usplash and the terminal both looked very stretched. I tried the 1024x768 afterwards and it looks much better.

Previously the usplash was all grainy like it was coming up in 8 or 16 bit color as well, and this has fixed both issues.

Cheers!

:)

---

