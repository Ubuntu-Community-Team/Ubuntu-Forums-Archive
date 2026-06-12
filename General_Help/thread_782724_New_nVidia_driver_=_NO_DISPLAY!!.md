---
title: "New nVidia driver = NO DISPLAY!!"
date: 2008-05-05
forum: General Help
---

### Post by eatfruit on 2008-05-05
Hi there, this is my first post so please direct me if I'm in the wrong place or wotnot...

I have been using Hardy without any issues since it came out.  The yesterday I changed the nVidia driver for my GeForce 4 to the one marked new ( i think it was *nVida-glx (new)* or something like that).  The computer carried on working fine.  But the next time I booted after the innitial loading screen the monitor blacks out and goes to stand-by.  I know its gotten to the login screen as it makes the noise.  If i turn the monitor back on all it comes up with are some flashing horizontal lines.  I've tried several monitors (both LCD and CRT and both worked before) and also tried booting in recovery mode but to no avail.  [guess the lesson is - if it aint broke don't mess with your graphics driver!]

I know the hardware is all fine as the XP partition still works fine.  Can anyone help?  I'm a bit of a newb so will prob need a bit of a step by step guide!

If I download a live CD could I boot from that and change the driver? or is there a way of reverting to the old settings? or is it gonna be a case of reinstalling the whole OS?

Any advice would be greatly appreciated
Many thanks:confused:

---

### Post by Archmage on 2008-05-05
Either you boot in recover mode and than use the option "fix my grafics" or if this doesn't help than drop into root promt from the recovery option and remove it over the interface. (aptitude remove packagename).

---

### Post by eatfruit on 2008-05-05
Thanks, 
I'm not at home at the mo but i'll double-check again tonight but I think the screen still blanked out in recovery mode! Is that unusual.
Whats the difference between the different rt, generic and recovery mode options in the grub? does it matter which recovery is selected?

Thnks for your help

---

### Post by cdenley on 2008-05-05
It sounds like you installed the realtime kernel. Either kernel will work when you boot into recovery mode. Installing nvidia-glx-new was a bad idea. This is from the package description...
> 
If you have a GeForce4, you may need the nvidia-glx
package.

The reason there are three different versions of the non-free nvidia driver is because nvidia stops supporting older video cards on new drivers they release. If you manage to get to a terminal, use this command
```

sudo apt-get install nvidia-glx

```

If the screen "blanks out", try ctrl+alt+f1.

---

### Post by eatfruit on 2008-05-06
Nice one! cThat worked a treat...
...well I say treat... it would only go up to 800resolution.  But after a little hunt through the forums and a lot of fiddling its all sorted.
Thanks loads
:p:D:p

---

