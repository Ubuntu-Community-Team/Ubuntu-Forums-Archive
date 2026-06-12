---
title: "Compiz not loading correct at start"
date: 2008-05-22
forum: General Help
---

### Post by Gripp on 2008-05-22
it started when i went through the control center to "appearance" and messed with the visual effects.  even though none of them are selected anymore on boot compiz fails to completely load.  

my solution thus far has been to start up the Fusion Icon and restart the window manager. 

but so how do i fix that?

---

### Post by mano cazalet on 2008-05-22
first i would check if in Advanced Desktop Effects Setting you have enabled the Window decorations. There should be a command there: 
emerald --replace

---

### Post by Gripp on 2008-05-22
it was turned on.  first i tried turning it off, but it removed all of the borders.. i tried reloading compiz but found it didn't help so i turned it back on

and the command was gtk-window-decorator --replace
i tried changing that to emerald --replace and rebooting, but still got the same result

---

### Post by mano cazalet on 2008-05-22
ok

let's see what happens if you add emerald --replace to  your startup programs in system/preferences

---

### Post by BCtom on 2008-05-23
I upgraded to Hardy......

I have being following this thread. I am getting the same results. I installed the Compiz eye candy Advance Desktop Effects Settings program, and had it working wonderfully, then I rebooted--and nothing--no stat-up, or activation afterwords. Not even the Cairo-Clock works..... My Compix Fision icon will not work either...

I just did a complete reinstall, but I keep getting the same--no desktop eyecandy.

This is what I get when I try starting in the Terminal calling "Compiz."

> Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:3582 (rev 02) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity 
It worked wonderfuly with Gutsy on this machine, a HP Pavilian dv1010ca.

---

### Post by Gripp on 2008-05-31
It helped - but not fully.

i know at least get the title bar on my programs at boot. but the rest of the Compiz components fail to load.  i.e. wobbly windows, cube, transparencies, etc. still have to load the icon and reload to fix that. 

and BCTom - you do have the correct drivers for your vid card installed, right?

---

### Post by BCtom on 2008-05-31
> **Gripp said:**
>  ....and BCTom - you do have the correct drivers for your vid card installed, right?

Gripp, actually I should have gone back here once I solved the problem. Yes, it was the driver(s). I had both Nvidia and Intel drivers loaded at the same time. Once I got rid of all the incorrect drivers, I rebooted, I had the 3D desktop working again. 

During my upgrade, for wahtever reason, Hardy loaded up both sets of drives. I guess the configuration does not fully take place until the system reboots--in my case a couple of times--before everything is bug free.

But I have to say, Hardy seems to work a lot better on this machine than Gutsy did. The Cube is very smooth compared to before.  Thanks Gripp.

---

### Post by darojasp on 2008-10-29
I am having the very same problem. Did you find a solution already?

---

