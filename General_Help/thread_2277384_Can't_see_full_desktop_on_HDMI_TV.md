---
title: "Can't see full desktop on HDMI TV"
date: 2015-05-08
forum: General Help
---

### Post by cable_guy on 2015-05-08
Hi all,

I can't work out how to fit the desktop on my TV screen properly, it hangs over each edge by quite a distance and is making (the already difficult) MythTV backend even more troublesome.

I have tried clicking on the monitor settings but can only change resolution and nothing related to overscan/underscan.

Happy to do stuff at the command line if that's what's necessary (From my brief dealings with this sort of stuff many years ago I seem to remember an Xorg.conf file?)

thanks in advance.

---

### Post by gordintoronto on 2015-05-08
Most times, this can be fixed from the menus on the TV!

---

### Post by frank18 on 2015-05-08
> **cable_guy said:**
> Hi all,

I can't work out how to fit the desktop on my TV screen properly, it hangs over each edge by quite a distance and is making (the already difficult) MythTV backend even more troublesome.

I have tried clicking on the monitor settings but can only change resolution and nothing related to overscan/underscan.

Happy to do stuff at the command line if that's what's necessary (From my brief dealings with this sort of stuff many years ago I seem to remember an Xorg.conf file?)

thanks in advance.

First you have to tell us what  computer and Video card you have?
for exemple my Hp DV6 1259DX has intel HD2000 card  i have overscan on tv cuts edges and i can't do anything about it,

my lenovo intel I5 2400  i have PCi ATI HD 6540 card and i install   [FONT=Calibri, Arial, sans-serif][COLOR=#000000] AMD Catalyst&#8482; proprietary driver, then i can use the res can option.[/COLOR][/FONT]

---

### Post by cable_guy on 2015-05-09
hi, I have a HP Microserver, and a Nvidia Geforce 210 inside it, I don't have any over/underscan settings on the TV itsself so I'm hoping I Can resolve in software somehow.

---

### Post by frank18 on 2015-05-09
> **cable_guy said:**
> hi, I have a HP Microserver, and a Nvidia Geforce 210 inside it, I don't have any over/underscan settings on the TV itsself so I'm hoping I Can resolve in software somehow.


The over-scan or under-scan settings are not in  most display  tvs but in the video card manager center settings,at least in my HD 6540 ati catalytic center,my LCD tv had over scan and couldn't control pc so i adjusted it in the catalytic manager center, so now i can control pc in the display,also can control color,brightens and contrast, and other stuff.but i had to download special drivers to do that, you have to check if your Nvidia Card has drivers for that, go to Nvidia web site and see if there are other new drivers that you can install to do that.

also check this out 


[http://forums.fedoraforum.org/showthread.php?t=278707](http://forums.fedoraforum.org/showthread.php?t=278707)

---

### Post by trag on 2015-05-10
If you are unable to find a software solution, then I recommend a HDMI/VGA adapter between your PC and monitor. Convert your HDMI output to VGA and set the monitor to VGA receive and you will default to 1368x768 or something similar with no over/under scan. the audio will be Mono not Stereo sadly.

---

### Post by cable_guy on 2015-05-16
> **frank18 said:**
> The over-scan or under-scan settings are not in  most display  tvs but in the video card manager center settings,at least in my HD 6540 ati catalytic center,my LCD tv had over scan and couldn't control pc so i adjusted it in the catalytic manager center, so now i can control pc in the display,also can control color,brightens and contrast, and other stuff.but i had to download special drivers to do that, you have to check if your Nvidia Card has drivers for that, go to Nvidia web site and see if there are other new drivers that you can install to do that.

also check this out 


[http://forums.fedoraforum.org/showthread.php?t=278707](http://forums.fedoraforum.org/showthread.php?t=278707)


Thank you for the help. All I needed to do was open the NVidia tool from the "start menu" and adjust resolution and underscan settings. :) Solved.

---

