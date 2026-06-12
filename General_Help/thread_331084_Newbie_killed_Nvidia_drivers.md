---
title: "Newbie killed Nvidia drivers?"
date: 2007-01-04
forum: General Help
---

### Post by yezzer on 2007-01-04
Hey!

I'm new to linux - well - i've installed ubuntu a few times over the last 6 months (and was once scared by a red hat install), and this is my first 'permanent' install of ubuntu. So yeah, i know nothing about *nix, and I may be making huge, terrible mistakes that will have the entire community laughing at me. But hey, making mistakes is a good way of learning ;)


I was trying to get NVTV working, and outputting to TV, and i think i may have removed it and the nvidia drivers :rolleyes: - as when i rebooted I had an error: "fatal server error no screens found"(or something like that) and I was at a command prompt.

Anyhoo - i managed to use nano to change /etc/X11/xorg.conf - and changed 
driver = "nvidia" to driver = "vesa" - and now i can at least get a GUI :D

The problem is now the machine doesnt output to the monitor, or use the nvidia drivers. It's outputting to the TV (which isnt viewable - its corrupted) - and I can only use VNC to actually view the desktop. 

I'd really like to get the nvidia drivers working, and also change the output to my monitor (at least for the moment!) 

Can anyone offer any advice? I really dont want to reinstall ubuntu :(

Cheers!

---

### Post by Sqwishy on 2007-01-04
> **yezzer said:**
> Hey!
will have the entire community laughing at me. But hey, making mistakes is a good way of learning ;)
 haha! naw just kidding. I was a noob once and still is abit, and i've said my fair share of stupid things too :) 

> **yezzer said:**
> 
I was trying to get NVTV working, and outputting to TV, and i think i may have removed it and the nvidia drivers :rolleyes: - as when i rebooted I had an error: "fatal server error no screens found"(or something like that) and I was at a command prompt.
 Were you following a guide? if so can you show me/us?

---

### Post by yezzer on 2007-01-04
> **Sqwishy said:**
>  Were you following a guide? if so can you show me/us?

Errr - no - i was just experimenting and breaking things :-/

---

### Post by angkor on 2007-01-04
> **yezzer said:**
> Errr - no - i was just experimenting and breaking things :-/

:D. If that's your attitude, my guess is you won't be a newbie for long.

As long as you're in the habit of breaking things, try [this guide.]("http://doc.gwos.org/index.php/Nvidia_easy_tv_out")

---

### Post by yezzer on 2007-01-04
fixed it!

i trawl of google found this command:

sudo dpkg-reconfigure -phigh xserver-xorg

Which fixed it. yey :)

i'll check out that post, thank you :)

---

### Post by Rhubarb on 2007-01-04
> Anyhoo - i managed to use nano to change /etc/X11/xorg.conf - and changed
driver = "nvidia" to driver = "vesa" - and now i can at least get a GUI 
Almost, you should change it to:
```
driver = "nv"
```
The nv driver is the nice open source 2D driver that works with nVidia cards, it is the default one that is used after a fresh install of Ubuntu.
So if you can't get into a gui, either restore your backup xorg.conf, or change the driver to "nv".

> sudo dpkg-reconfigure -phigh xserver-xorg
Not sure what the "-phigh" switch does (will look this up tonight yeah!), but I'm glad you figured out how to get it all running again.
I personally use the "dpkg-reconfigure xserver-xorg" command so I can install ubuntu on one computer, rip out the hard drive, and put it into a different (CD-ROMless) computer.
- I'd like to see windowz do that!

Finally, I'd like to say congratulations for figuring it out yourself!  We're all learning here, and I'm amazed at what I can do with Ubuntu every week.

---

### Post by yezzer on 2007-01-04
> **Rhubarb said:**
> Almost, you should change it to:
```
driver = "nv"
```
The nv driver is the nice open source 2D driver that works with nVidia cards, it is the default one that is used after a fresh install of Ubuntu.
So if you can't get into a gui, either restore your backup xorg.conf, or change the driver to "nv".


Ahh, i'd been wondering what the difference between nvidia and nv was :)

> **Rhubarb said:**
> 
Not sure what the "-phigh" switch does (will look this up tonight yeah!), but I'm glad you figured out how to get it all running again.
I personally use the "dpkg-reconfigure xserver-xorg" command so I can install ubuntu on one computer, rip out the hard drive, and put it into a different (CD-ROMless) computer.
- I'd like to see windowz do that!

Finally, I'd like to say congratulations for figuring it out yourself!  We're all learning here, and I'm amazed at what I can do with Ubuntu every week.

Heh, thanks. Ubuntu is great, and has the potential to be amazing :D

---

