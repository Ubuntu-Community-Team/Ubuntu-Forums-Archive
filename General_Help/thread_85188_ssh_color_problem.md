---
title: "ssh color problem"
date: 2005-11-02
forum: General Help
---

### Post by Antioch on 2005-11-02
Im trying to run an x application through ssh (which I run with the -Y flag) but I recieve the follow error when I try to launch a program (cadence IC deisgn tools) :
*WARNING* Atr: Failed to find 8-plane PseudoColor visual

Does anyone know how to fix this? Its pretty much a show stopper for me.

(Aside from running xorg in 8 bit color mode, because that is ridiculous. If I use windows and an x emulator I can tell it to fake 8bit color depth, so Im sure  must be able to do similar things in LINUX. Especially when Ive sen the program running through remote-login on a mac.)

Thanks!

---

### Post by Kyral on 2005-11-02
You need to run SSH with the -X flag ;P

---

### Post by RAOF on 2005-11-02
I don't think that's the problem, actually.  As far as I can tell from man ssh, the -Y flag does just the same as the -X flag, but disables some security checking.

That said, I don't actually have anything else to help.  Maybe it's worth a try ;)

---

### Post by Antioch on 2005-11-02
[QUOTE=RAOF]I don't think that's the problem, actually.  As far as I can tell from man ssh, the -Y flag does just the same as the -X flag, but disables some security checking.

That said, I don't actually have anything else to help.  Maybe it's worth a try ;)[/QUOTE]

Thats correct, they do practically the same thing. But, I went ahead and tried it, because sometimes the solution is right under your nose - but the result was the same. :(

---

### Post by jonzep on 2005-11-02
try with "-cc 3"

---

### Post by Antioch on 2005-11-02
[QUOTE=jonzep]try with "-cc 3"[/QUOTE]

I also googled and found that, however that is for use with some vnc, not with the ssh bin, or for use with the cadence software. For kicks I tried it with the cadence software but nothing happened, and ssh registers it as invalid, which it is as its not listed in the man pages at all.

Any more ideas?

Ive looked through the ssh man pages and theres nothing about color depth or anything.

---

### Post by manurastogi on 2007-09-28
I am getting pretty much the same problem . Did you find a cure ?

Basically if I modify the xorg.conf file and set the default depth to 8 bits Cadence works. However that modifies the entire dektop tto 8 bit resolution as well. 

If I keep the xorg.conf at 24 bit resolution then I get the Warning : Atr thing (originally posted on the thread ) 

I have also tried getting multiple X11 servers on the machine by the changing the  /etc/X11/gdm/gdm.conf file how ever that started two paraller servers on vt7 and vt9 with same bith width of 8 bits.


Thanks 

-Manu

---

