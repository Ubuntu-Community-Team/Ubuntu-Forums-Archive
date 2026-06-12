---
title: "Usplash widescreen question"
date: 2007-04-21
forum: General Help
---

### Post by Pausanias on 2007-04-21
I have a widescreen laptop at 1680x1050.

When I boot using the most recent desktop Feisty CD, the Ubuntu logo displays correctly at full resolution!

When I boot from my harddrive (upgraded from a Feisty beta install and up-to-date), the Ubuntu logo is stretched horizontally (i.e. has wrong aspect ratio).

Since the software on the install CD is the same as the software on my hard drive, I'm guessing I'm missing some kernel boot option that makes usplash display correctly. Anybody have an idea what that could be?

Thanks!

---

### Post by der_joachim on 2007-04-21
Somewhere in the HOWTO subforum there is a HOWTO for tweaking grub. However, AFAIK your rosolution is not fully supported. I cannot find it at the moment, but there's apparently an alternative that actually supports widescreen monitors.

---

### Post by mrguytx on 2007-04-22
you probably need to add "vga=791" to temporarily put your boot resolution into 1024x768.
add that at the end of your boot line in grub.


> **Pausanias said:**
> I have a widescreen laptop at 1680x1050.


When I boot using the most recent desktop Feisty CD, the Ubuntu logo displays correctly at full resolution!

When I boot from my harddrive (upgraded from a Feisty beta install and up-to-date), the Ubuntu logo is stretched horizontally (i.e. has wrong aspect ratio).

Since the software on the install CD is the same as the software on my hard drive, I'm guessing I'm missing some kernel boot option that makes usplash display correctly. Anybody have an idea what that could be?

Thanks!

---

### Post by Zorael on 2007-04-22
I have the same problem, with the same native resolution.

[quote=mrguytx]you probably need to add "vga=791" to temporarily put your boot resolution into 1024x768.
add that at the end of your boot line in grub.[/quote]

Well, even at 1024x768 the proportions are still off, since the screen itself is wide..

---

### Post by youknowit on 2008-02-14
This may help:

[http://samiux.wordpress.com/2007/11/05/boot-up-screen-usplash-bug-fix-for-ubuntu-710/](http://samiux.wordpress.com/2007/11/05/boot-up-screen-usplash-bug-fix-for-ubuntu-710/)

Cheers,

---

### Post by dcstar on 2008-02-14
> **Zorael said:**
> I have the same problem, with the same native resolution.

Well, even at 1024x768 the proportions are still off, since the screen itself is wide..

If the resolution you want is available in the various "standard" VGA video modes, then it will work, if it is not (like 1440x900 on my system), then changing the usplash file to a non-standard setting won't make any difference.

AFAIK this part of the boot-up sequence occurs before any of the "X" video drivers are loaded, so you only get the inbuilt VGA modes (which don't seem to include widescreen formats).

Here is a list of modes that should be available (from [http://tldp.org/HOWTO/Framebuffer-HOWTO-5.html)](http://tldp.org/HOWTO/Framebuffer-HOWTO-5.html)):

```
Colours   640x400 640x480 800x600 1024x768 1152x864 1280x1024 1600x1200
--------+--------------------------------------------------------------
 4 bits |    ?       ?     0x302      ?        ?        ?         ?
 8 bits |  0x300   0x301   0x303    0x305    0x161    0x307     0x31C
15 bits |    ?     0x310   0x313    0x316    0x162    0x319     0x31D
16 bits |    ?     0x311   0x314    0x317    0x163    0x31A     0x31E
24 bits |    ?     0x312   0x315    0x318      ?      0x31B     0x31F
32 bits |    ?       ?       ?        ?      0x164      ?
```

---

