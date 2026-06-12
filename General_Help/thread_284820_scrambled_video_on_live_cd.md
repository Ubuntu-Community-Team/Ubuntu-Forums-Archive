---
title: "scrambled video on live cd"
date: 2006-10-26
forum: General Help
---

### Post by madFusiob on 2006-10-26
i have a WinFast PX6800 GS Extreme video card installed and when i attempt to run ubuntu 6.10 from the cd everything goes well until it gets to the desktop. basically the screen gets scrambled and nothing is recognizable. does anyone know if that video card is compatible with this version? i looked on some lists of supported cards but i didnt see it. i came here to see if anyone could help me. i've also tried running ubuntu 6.06 from the cd and it does the exact same thing.

---

### Post by orb9220 on 2006-10-26
That is very much a possible answer. Try booting with second boot option safe graphics mode.

---

### Post by madFusiob on 2006-10-26
i tried that and the same thing occurs :(.

---

### Post by DeathOnJuice on 2006-10-26
I had the same problem with the beta CD with an eVGA 7800GT; I hoped they would have fixed it by now. I would suggest trying the alternative install CD, then installing drivers and stuff afterwards if needed. This CD has a text-based install.

I hope it works for me, too. Give it a shot!

---

### Post by DeathOnJuice on 2006-10-27
Bump - any luck? I haven't tried yet the alternative CD yet, but I know the normal one doesn't work whether I'm in safe graphics mode or not. I'm starting to wonder whether or not I should even upgrade.

---

### Post by DeathOnJuice on 2006-10-28
In case you're still around and have the problem, I fixed it and posted a guide:

[http://www.ubuntuforums.org/showthread.php?p=1680357#post1680357](http://www.ubuntuforums.org/showthread.php?p=1680357#post1680357)

---

### Post by madFusiob on 2006-11-03
thanks i'll check it out

---

### Post by randolph on 2006-11-03
Hi, i have same problem with a GF6800 and Live-CDs with Ubuntu 6.06 and 6.10. On my old TFT 15" Samtron 51S i can start only 6.06 in safe grafics mode, with 6.10 i have no luck (i can't get a console with control-alt-f1...). I played around in BIOS with the "agp aperture size", try it out. In the next days i will test it with another monitor because someone in the german ubuntuforum (forum.ubuntuusers.de) supposed only newer monitors can handle the frequences of the nvidia-drivers in the Live-CD.
Sorry for my poor english!

greets, randolph

---

### Post by randolph on 2006-11-04
No good news. I took a 17" Acer AL 1715 with hsync 30-83, vsync 55-75 and max. 1280x1024 screen and started the 6.10 LiveCD. I got only a black screen with a functionless curser, no matter if i used normal grafics or save grafic mode. I can't get a console for contr-alt-f1, difference modes with F4 have no effect, cheatcodes with F6 like fb=false or vga=normal are ineffectual. O.k., i'm satisfied with my installed Dapper, and my GF6800 is good for Stellarium, Tuxracer and other little entertainments. Maybe some day a new nvidia-driver for 6.10 will rising...
Greets, randolph

---

### Post by randolph on 2006-11-06
Now I can start Live-CD of Edge Eft (Ubuntu 6.10) with my GF6800!

Solution:
In the first bootscreen select F6 for additional options. Delete "quiet" and "splash" and write "break=bottom" in front of the two lines at the end
[enter]
After some times of recognition several hardware-components you are now in a console. For editing the xorg.conf type:

chroot  /root  nano  /etc/X11/xorg.conf  [enter]

Now scroll down to - Section "Device" -
Below the lines of
- Identifier "NVIDIA catchmeifyoucan" -
and
- BusID "PCI:1:0:0" -
you see
- Driver "nv" (may be...)

Replace it with
- Driver "vesa" -

Scroll down to the bottom.

Then [contr-x] for terminate nano, answer with "y" to store the changed xorg.conf, then type "exit" [enter] for terminating the console and continuing the process of booting.
And Voila! Coffee-Creme-Desktop in vesamodus with sound and all you need...

That's a solution for MY system, but there seems to be a chance to configure several things in the xorg.conf of a Live-CD...
A big thanks to [www.launchpad.net](www.launchpad.net) and the posting of Tormod Volden at 2006-11-05 15:31:36 UTC.
Link: [https://launchpad.net/distros/ubuntu/+bug/67487](https://launchpad.net/distros/ubuntu/+bug/67487)

My system:
K7S8X Rev3 with Bios 2.60, GeForce 6800FX, AthlonXP 2400+, 1GB Ram Infineon, 2 HDDs, CDRW, DVD.

I wish you will have some success.
randolph

---

