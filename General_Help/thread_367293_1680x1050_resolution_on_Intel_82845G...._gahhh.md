---
title: "1680x1050 resolution on Intel 82845G.... gahhh"
date: 2007-02-22
forum: General Help
---

### Post by vendejp on 2007-02-22
I know these things get posted all the time, Im on the verge of giving up, so before I do I may as well post.  Ive spent hours sifting through the forums and trying different solutions.

I cant get 1680x1050 resolution for the life of me.

Attatched is my xorg.conf file and the Xorg.log is too large to upload, so it can be found here:
[http://www.brightshift.com/Xorg.0.log.txt](http://www.brightshift.com/Xorg.0.log.txt)

Running Edgy 6.10
Monitor is an Acer AL2016W
Graphics Card: Intel 82845G
Graphics card is set to use 8MB

Ive tried everything from lowering the DefaultDepth, using 915resolution to hack in my resolution (even though I dont think this is the right card for it), to installing the xserver-x-org-video-intel driver and changing the driver in the xorg.conf file to "intel", to bumping the vertical refresh up to 160, etc.

why is this so complicated?

thanks in advance

---

### Post by NewOldTimer on 2007-02-22
you've done so much why not look at another page, maybe you've already seen this?
[http://ubuntuforums.org/showthread.php?t=351647](http://ubuntuforums.org/showthread.php?t=351647)

---

### Post by ramjet_1953 on 2007-02-22
I'm not sure if your card is supported, but you could try the intel driver called 915resolution, which is available via Synaptic Package Manager.
 There is a help file included in the download.

Regards,
Roger :cool:

---

### Post by vendejp on 2007-02-22
Thanks for the suggestions, but as I said, Ive already tried 915resolution.  I did just try it again though following the instructions from the other post listed (there are so many variations, why not).

Changing the bits/pixel on mode 30 wouldnt take, so I also change mode 54.  I didnt have /etc/default/915resolution file as the user suggested, but I created and edited it anyway.

josh@earth:~$ sudo 915resolution -l
Intel 800/900 Series VBIOS Hack : version 0.5.2

Chipset: 845G
BIOS: TYPE 2
Mode Table Offset: $C0000 + $38a
Mode Table Entries: 18

Mode 30 : 1680x1050, 8 bits/pixel
Mode 32 : 1680x1050, 8 bits/pixel
Mode 34 : 1024x768, 8 bits/pixel
Mode 38 : 1280x1024, 8 bits/pixel
Mode 3a : 1600x1200, 8 bits/pixel
Mode 3c : 1920x1440, 8 bits/pixel
Mode 41 : 1680x1050, 16 bits/pixel
Mode 43 : 1680x1050, 16 bits/pixel
Mode 45 : 1024x768, 16 bits/pixel
Mode 49 : 1280x1024, 16 bits/pixel
Mode 4b : 1600x1200, 16 bits/pixel
Mode 4d : 1920x1440, 16 bits/pixel
Mode 50 : 1680x1050, 32 bits/pixel
Mode 52 : 1680x1050, 32 bits/pixel
Mode 54 : 1024x768, 32 bits/pixel
Mode 58 : 1280x1024, 32 bits/pixel
Mode 5a : 1600x1200, 32 bits/pixel
Mode 5c : 1920x1440, 32 bits/pixel


no go, I still can only use 1280x1024

thanks anyway.

---

### Post by vendejp on 2007-02-24
im surprised to say ive made some progress.  i used the 915resolution hack again to add the 1680x1050 resolution using the 16 bits/pixel mode and then setting the DefaultDepth to 16.

The resolution actually shows up in the resolution settings and I can select it.  Now onto the next problem.  The monitor is a 20 inch widescreen Acer (AL2016W model).  Now the monitor doesnt seem to detect the resolution.

There is an "Auto config" setting on the monitor that detects the resolution and configs the monitor and it works fine for other resolutions and 1680x1050 in windows, but here in ubuntu the monitor seems to think its 1280x1024.

As a result, the screen basically scrolls off the edges of the monitor and i have to pan left, right, up, down.

915resolution wont let me hack in this res with 24 bits/pixel.  I dont know if maybe thats the problem.

gahhhhhh

---

### Post by vendejp on 2007-03-10
i gave up, bought a $45 nvidia card

---

### Post by isecore on 2007-03-10
This is just pure speculation from me, but I feel that 8 mb of video memory is a rather low setting for that kind of resolution. I have absolutely no experience with Intel-graphics, but again, my gut-instinct and experience tells me that 8 megs of vram is very low. 

If it's a dynamically allocated vram then I suggest setting the limit to something more reasonable such as 32 megabytes or more and see if that solves the problem.

---

