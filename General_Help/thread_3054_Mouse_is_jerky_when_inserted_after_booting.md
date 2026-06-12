---
title: "Mouse is jerky when inserted after booting"
date: 2004-11-02
forum: General Help
---

### Post by Daniel G. Taylor on 2004-11-02
Hey!

My first post on these forums. I'm having a slight problem on my desktop system, and it is that my mouse (Logitech MX500, connected to PS/2 instead of USB) sometimes gets well, jerky. The issue arises because I sometimes wind up kicking or otherwise loosening the connection to where the mouse is not connected properly to the system, and it boots up into X without it. I quickly realize it, plug it back in properly, and after a few seconds the system starts responding to input, but the movement is anything but smooth. It's slow and jerky.

dmesg gives me this: "input: PS2++ Logitech MX Mouse on isa0060/seriol"

Does anyone know why this might be happening, and/or how to fix it? I hate to have to reboot to get the mouse working properly again (restarting X doesn't help).

P.S. By solutions I mean other than to stop kicking it and to use USB (which may or may not have the same issue).

---

### Post by ubuntu-geek on 2004-11-09
I would suggest using the USB option of the mouse this will ensure if you accidently unplug it and plug it back there should be smooth operation of the mouse. PS/2 in my experience always acts flaky when plugged back in without rebooting.

Hope this helps.

---

### Post by jdong on 2004-11-10
It's the design of PS2. PS2 isn't designed for hotplugging (i.e. removing / inserting while computer is on); that's why it won't work , or work badly, if you insert the device afterwards.


I agree with ubuntu-geek, that switching to USB is the best option.


P.S. If you can kick _OUT_ the connector, realize how much damage you could be doing to your computer and your mouse! Do try to be more careful!

---

### Post by JonAtkinson on 2004-11-10
It also might be a problem with the sampling rate of the mouse - I'm sure you can get command line utilities which will modify the sample rate, and running one of these after you kick the mouse out may help restore it to being less jerky.

I've previously used tuneps2, avaliable from [here](http://elektra.e-technik.uni-ulm.de/~mbuck/linux/tuneps2.html).

Hope that helps.

--Jon

---

