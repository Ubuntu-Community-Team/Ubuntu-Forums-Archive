---
title: "White screen hard crash"
date: 2008-05-19
forum: General Help
---

### Post by havchr on 2008-05-19
Hi! I've just got a new machine, XFX motherboard , nvidia 680i chipset, 2 gig of DDR2 RAM (corsair iirc), XFX 8800 GTS alpha dog edition. 

I'm using the onboard soundcard which is nvidia HDA type.

However, my problem is, that I've experienced three times, a white screen that hangs the entire system. changing to terminal ctrl-alt-f# does not work, ctrl-alt-backspace does not work. ctrl-alt-del does not work. I've only been able to turn of the machine by holding the power button down for a long time.

After such a crash has happend, the machine seems like it has trouble booting. Maybe it is a temperature issue, but I could not find anything about it in logs, and I've tried to monitor my temp regularly and it has never gone over around 50 C.

Symptoms; all the times I have been playing music with amarok, running some opengl program and possibly had firefox running as well.

"Fix"/inspect not tested yet is to run ssh-deamon and log into box to see if I can get a terminal though the network.

If anyone have any tips to help me, I'd be glad, because I cannot afford to buy windows at the moment.

---

### Post by ryanhaigh on 2008-05-20
First step would be to disable destkop effects from system>preferences. If you determine that this 'fixes' the issue you can then try and figure out what is causing the problem. 

The system is probably scanning your disk after a bad shutdown (holding the button) which is why it may seem to be 'having trouble'.

For situations like this where the system seems completely unresponsive you can try this [http://en.wikipedia.org/wiki/Magic_SysRq_key#Raising_Elephants](http://en.wikipedia.org/wiki/Magic_SysRq_key#Raising_Elephants)

---

### Post by TheDriller on 2008-11-14
i'm having the same crash on a Fujitsu Seimens Amilo laptop. AMD Turion processer ATI Radeon 200m graphics card, 2Gb RAM, running Intrepid Ibex, but it happened once during an attempted upgrade from hardy to Intrepid.

every time it has happened, firefox is the common link andit only happens when firefox is running, usually just after i have cicked a link or something.

---

