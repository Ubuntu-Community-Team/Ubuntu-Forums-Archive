---
title: "Ubuntu 19.04 Audio problem"
date: 2019-04-25
forum: General Help
---

### Post by spike0000 on 2019-04-25
Hi all,

I'm new and I want to say thanks to all community

I open this thread because I've got a problem with sounds, in every application (Rhythmbox, Youtube, Amazon Prime Video,  ecc...).
In fact, the sound "jumps" for brief moments (less than 2 sec.) like a DJ skratch.

lspci -v (audio section) in the img below:[URL="https://ibb.co/YWZD21P"]
[IMG]https://ibb.co/YWZD21P[/IMG]
[/URL]
I have this problem with Ubuntu 19.04, 18.04 and Mint before, while in other partition Manjaro performs properly.
Can you help me, please?


Thanks.

---

### Post by Rubi1200 on 2019-04-25
Hi and welcome to the forums :-)

Image is not attached.

In any event, please open a terminal and if you do not already have it, install inxi

```
sudo apt-get install inxi
```

Then run this and post the output here:

```
inxi -GM
```

Thanks.

---

### Post by spike0000 on 2019-04-25
Hi,

below the output:

> 
[COLOR=#3465A4]**Machine:   Type:**[/COLOR] Laptop [COLOR=#3465A4]**System:**[/COLOR] ASUSTeK [COLOR=#3465A4]**product:**[/COLOR] X555YI [COLOR=#3465A4]**v:**[/COLOR] 1.0 [COLOR=#3465A4]**serial:**[/COLOR] <root required> 
           [COLOR=#3465A4]**Mobo:**[/COLOR] ASUSTeK [COLOR=#3465A4]**model:**[/COLOR] X555YI [COLOR=#3465A4]**v:**[/COLOR] 1.0 [COLOR=#3465A4]**serial:**[/COLOR] <root required> [COLOR=#3465A4]**UEFI:**[/COLOR] American Megatrends [COLOR=#3465A4]**v:**[/COLOR] X555YI.510 [COLOR=#3465A4]**date:**[/COLOR] 11/13/2015 
[COLOR=#3465A4]**Graphics:  Device-1:**[/COLOR] Advanced Micro Devices [AMD/ATI] Mullins [Radeon R4/R5 Graphics] [COLOR=#3465A4]**driver:**[/COLOR] radeon [COLOR=#3465A4]**v:**[/COLOR] kernel 
           [COLOR=#3465A4]**Device-2:**[/COLOR] Advanced Micro Devices [AMD/ATI] Jet PRO [Radeon R5 M230] [COLOR=#3465A4]**driver:**[/COLOR] radeon [COLOR=#3465A4]**v:**[/COLOR] kernel 
           [COLOR=#3465A4]**Display:**[/COLOR] x11 [COLOR=#3465A4]**server:**[/COLOR] X.Org 1.20.4 [COLOR=#3465A4]**driver:**[/COLOR] radeon [COLOR=#3465A4]**resolution:**[/COLOR] 1366x768~60Hz 
           [COLOR=#3465A4]**OpenGL:**[/COLOR] [COLOR=#3465A4]**renderer:**[/COLOR] AMD MULLINS (DRM 2.50.0 5.0.0-13-generic LLVM 8.0.0) [COLOR=#3465A4]**v:**[/COLOR] 4.5 Mesa 19.0.2 



Thanks

---

### Post by Rubi1200 on 2019-04-25
Well, your specs should be fine and if, as you said, it works in Manjaro then I suppose it is a problem specific to the Ubuntu/Mint versions.

I know the link says no sound but I think it is worth trying some of the solutions here anyway:
[https://itsfoss.com/fix-sound-ubuntu-1304-quick-tip/](https://itsfoss.com/fix-sound-ubuntu-1304-quick-tip/)

Let us know if it helped.

---

### Post by spike0000 on 2019-04-25
Hi,

it does not work.
I don't understand what kind of problem there is.
Audio goes good, but suddenly sktratch for a moment.


Thanks

---

### Post by Rubi1200 on 2019-04-25
I am also not sure but perhaps try the answer from here:
[https://askubuntu.com/questions/1033405/crackling-and-delayed-sound-after-upgrading-to-18-04](https://askubuntu.com/questions/1033405/crackling-and-delayed-sound-after-upgrading-to-18-04)

You want to open a terminal and then:

```
killall pulseaudio
```

And then:

```
nano /etc/pulse/default.pa
```

Find the line with load-module module-udev-detect and change to this: > load-module module-udev-detect tsched=0

Save and exit

and now go back to the terminal and run:

```
pulseaudio -k
```

Don't think a restart is needed but if needs be restart and hopefully this will resolve it.

---

### Post by spike0000 on 2019-04-25
Hi,

now there's a different skratch sound (like finger on wood) but problem still remains.

Thanks

---

