---
title: "Option parsing failed: Cannot open display:"
date: 2015-04-21
forum: General Help
---

### Post by carr3 on 2015-04-21
Hi,

I am trying to run a simple program that runs a system call to play a sound.  Here is the command: 

system("canberra-gtk-play -f leftwave.ogg")

This program is run at bootup through the /etc/rc.local file on  ubuntu 14.04.  The rest of the program works fine except for this line of code.  I output the error to a txt file, which says:

Option parsing failed: Cannot open display:

I'm not sure how to resolve this problem.  Any suggestions would be appreciated.

Thanks,
Carr

---

### Post by Holger_Gehrke on 2015-04-21
For some reason canberra-gtk-play needs access to the x-display. /etc/rc.local runs as root. The display doesn't belong to root and there's no .Xauthority file in root's home giving the MIT-magic-cookie that would be needed for access. Use something else to play the sound. ogg123 from the package vorbis-tools comes to mind.

---

### Post by matt_symes on 2015-04-21
Hi

canberra-gtk-play looks to need X running and the DISPLAY variable set. I suppose the gtk part is a bit of a give away there.

Does your script need to be run from rc.local or can you run it as an autostart program in Unity just after login and when X is guaranteed to be running ?

Does it have to use canberra-gtk-play to play the sound ?

You could also try setting the DISPLAY variable just before you call your script and hope that LightDM will supply the X environment. I have no idea if this would work though.

Kind regards

---

### Post by carr3 on 2015-04-21
Thanks for the feedback.  I do not need to use canberra-gtk-play to play the sound, but it is the only thing that has worked for me so far.  I have tried some other libraries, such as SFML, but none seemed to work.  I also need to run the program without my system connected to a monitor.  In regards to setting the DISPLAY variable, can you still set the DISPLAY variable even if you don't necessarily need to use the display?  I simply just unplug the HDMI from my system.

Thanks,
Carr

---

### Post by Holger_Gehrke on 2015-04-21
The aforementioned ogg123 works just fine in a virtual console without the DISPLAY variable, so it should work in your script ... and setting DISPLAY would not help much with your problem for the reason I gave in post #2.

---

### Post by matt_symes on 2015-04-21
Hi

> **Holger_Gehrke said:**
> and setting DISPLAY would not help much with your problem for the reason I gave in post #2.

Holger_Gehrke is right here. I should have though about it before i posted.

Kind regards

---

### Post by carr3 on 2015-04-22
Thanks! Installed ogg123 and everything works now!

---

