---
title: "How can I re-install OpenGL?"
date: 2014-12-21
forum: General Help
---

### Post by josh109 on 2014-12-21
I can't launch most games because I'm having an OpenGL issue. I think that I just need to remove and then re-install openGL, but I can't find anything on how to do this (](*,)). Does anyone know how to remove and then install the latest version of OpenGL?

---

### Post by sudodus on 2014-12-21
Please tell us about your graphics chip/card and about your current graphics driver. Mark and paste the output of the following commands into a reply and put it within code tags.

```
sudo lshw -C display
```

```
lspci|grep -i vga
```

and check with the GUI program ***hardinfo***. See the data for

*Computer -- Display*

There might be an entry for OpenGL

You can find details via the tips in the following link

[http://askubuntu.com/questions/23238/how-can-i-find-what-video-driver-is-in-use-on-my-system](http://askubuntu.com/questions/23238/how-can-i-find-what-video-driver-is-in-use-on-my-system)

---

### Post by josh109 on 2014-12-21
> **sudodus said:**
> Please tell us about your graphics chip/card and about your current graphics driver. Mark and paste the output of the following commands into a reply and put it within code tags.

```
sudo lshw -C display
```

```
lspci|grep -i vga
```

and check with the GUI program ***hardinfo***. See the data for

*Computer -- Display*

There might be an entry for OpenGL

You can find details via the tips in the following link

[http://askubuntu.com/questions/23238/how-can-i-find-what-video-driver-is-in-use-on-my-system](http://askubuntu.com/questions/23238/how-can-i-find-what-video-driver-is-in-use-on-my-system)


Response from sudo lshw -C display (i'm new to the forums, I don't know how to "mark")
  *-display               
       description: VGA compatible controller
       product: Curacao XT [Radeon R9 270X]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:43 memory:d0000000-dfffffff memory:fdf80000-fdfbffff ioport:ee00(size=256) memory:fdf00000-fdf1ffff

Response from lspci|grep -i vga
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Curacao XT [Radeon R9 270X]

My graphics card runs through (what I think is) the PCIE slot on my motherboard, but this *is not the cause of the problem, as the games worked before.*
My graphics card is an AMD(/ATI) Curacao XT Radeon R9 270X (and it says ASUS on the card itself).
Below is a picture of my graphics card, in case this for some reason helps. (Yes, my computer is in a milk crate- it's custom made and cases are expensive, especially custom ones, and it cools the best)

[IMG]http://i.imgur.com/cQIALpc.jpg[/IMG]

---

### Post by sudodus on 2014-12-21
It might help to try with a proprietary driver for your Radeon card, but I have not much experience of that kind of graphics. I use nvidia and intel graphics. So I invite people who have experience of Radeon graphics to help.

---

### Post by josh109 on 2014-12-21
> **sudodus said:**
> It might help to try with a proprietary driver for your Radeon card, but I have not much experience of that kind of graphics. I use nvidia and intel graphics. So I invite people who have experience of Radeon graphics to help.

What's a proprietary driver?

---

### Post by Yellow Pasque on 2014-12-21
Give output of glxinfo:
```
glxinfo
```

---

### Post by sudodus on 2014-12-21
> **josh109 said:**
> What's a proprietary driver?

In contrast to most software in linux, a proprietary driver is not free, and the source code is not public. A proprietary driver is owned by a company, usually the company that sells some hardware, for example a graphics card, a wifi card, a printer. You can find some proprietary drivers in the Software Center, and you can also install those drivers with terminal window commands. Those drivers are tested with Ubuntu. Other drivers are available from the company that sells the hardware.

---

### Post by josh109 on 2014-12-21
> **Temüjin said:**
> Give output of glxinfo:
```
glxinfo
```

There's too much to fit in one terminal window, so what did fit in the terminal window is here. [http://pastebin.com/JHyVMer1](http://pastebin.com/JHyVMer1)
Something happened around line 147

---

### Post by deadflowr on 2014-12-22
It would seem that glxinfo is too big for the current scroll back of your terminal.
(You seem to be missing some pertinent info which is usually in the beginning of the output)

Perhaps try one of these to get the full output

Either try to put the output into a text file with something like
```
glxinfo > glxinfo.txt
```
this will make a file that will be in your home folder, called as noted glxinfo.txt.

Or open the terminal go to the menu section Edit > Profile Preferences > Scrolling.
Check the box for unlimited and re-run the glxinfo command again; posting to pastebin again.
( you could resize the scroll back; default is 512, but it's quicker/easier/simpler to just make it unlimited since you really have no idea how far to set the scrollback.)

---

### Post by mc4man on 2014-12-22
I've only used Intel & Nvidia but if I had that card (recent high end) I first research if the current 14.04 repo Ati drivers are good for it and or  look at the recent Ati ubuntu packages for 14.04 on the Ati site.
(- if from the site also on how to use.
Current repo driver(s) should show up in Software & Updates > Additional Drivers tab

---

### Post by Yellow Pasque on 2014-12-22
Well, we don't need the entire glxinfo output. This will do:
```
glxinfo | grep version
```

---

### Post by josh109 on 2014-12-22
> **deadflowr said:**
> It would seem that glxinfo is too big for the current scroll back of your terminal.
(You seem to be missing some pertinent info which is usually in the beginning of the output)

Perhaps try one of these to get the full output

Either try to put the output into a text file with something like
```
glxinfo > glxinfo.txt
```
this will make a file that will be in your home folder, called as noted glxinfo.txt.

Or open the terminal go to the menu section Edit > Profile Preferences > Scrolling.
Check the box for unlimited and re-run the glxinfo command again; posting to pastebin again.
( you could resize the scroll back; default is 512, but it's quicker/easier/simpler to just make it unlimited since you really have no idea how far to set the scrollback.)

The glxinfo.txt file was too big to upload, so I'll put it in pastebin. There's something about openGL around line 42.
[http://pastebin.com/BC9J4UGr](http://pastebin.com/BC9J4UGr)

---

### Post by josh109 on 2014-12-22
> **Temüjin said:**
> Well, we don't need the entire glxinfo output. This will do:
```
glxinfo | grep version
```

My output was:
server glx version string: 1.4
client glx version string: 1.4
GLX version: 1.4
OpenGL core profile version string: 3.3 (Core Profile) Mesa 10.3.0
OpenGL core profile shading language version string: 3.30
OpenGL version string: 3.0 Mesa 10.3.0
OpenGL shading language version string: 1.30
OpenGL ES profile version string: OpenGL ES 3.0 Mesa 10.3.0
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 3.0

---

### Post by sudodus on 2014-12-22
You have OpenGL version 3, that comes with the open driver Gallium. But versions 1.30 and 10 are also mentioned. (I don't know much about the drivers for AMD Radeon cards.)

```
OpenGL vendor string: X.Org
OpenGL renderer string: Gallium 0.4 on AMD PITCAIRN
OpenGL core profile version string: 3.3 (Core Profile) Mesa 10.3.0
OpenGL core profile shading language version string: 3.30


OpenGL version string: 3.0 Mesa 10.3.0

OpenGL shading language version string: 1.30
OpenGL ES profile version string: OpenGL ES 3.0 Mesa 10.3.0
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 3.0
```

To compare, I have OpenGL version 4, that comes with my nvidia proprietary driver for a card that is a few years old.

```
OpenGL renderer string: GeForce GT 430/PCIe/SSE2
OpenGL version string: 4.2.0 NVIDIA 304.125
OpenGL shading language version string: 4.20 NVIDIA via Cg compiler
```

I think you would get a newer version of OpenGL with a proprietary driver for your AMD Radeon card, or at least another version, at it is worth trying how it works.

---

### Post by josh109 on 2014-12-22
[B][U][I][SIZE=7][FONT=century gothic]SOLVED!

[/FONT][/SIZE][/I][/U][/B]_*[SIZE=7][FONT=century gothic][/FONT][/SIZE]*[SIZE=7][FONT=century gothic][/FONT][/SIZE]_[SIZE=7][FONT=century gothic][SIZE=4]All I had to do was install the correct drivers, I didn't have the correct drivers for my graphics card. It wasn't an openGL problem.
\\:D/
Thank you to all that helped![/SIZE]
[/FONT][/SIZE]

---

### Post by sudodus on 2014-12-22
Congratulations :KS

Please tell us the name of the driver that made the graphics work, and from where you got it (the Ubuntu repositories or directly from the manufacturer) :-)

---

