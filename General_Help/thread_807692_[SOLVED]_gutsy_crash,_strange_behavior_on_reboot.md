---
title: "[SOLVED] gutsy crash, strange behavior on reboot"
date: 2008-05-26
forum: General Help
---

### Post by LashSilence83 on 2008-05-26
here goes:
While running quite a few programs at once like I normally do, I received a message saying that amarok was not responding so even after I clicked force quit, music continued to play. One by one the other apps that were running all froze up and I couldn't access the system monitor or a terminal to kill the processes. After trying ctrl+alt+F1, ctrl+alt+backspace, and ctrl+alt+delete to no avail, I gave up and did a hard reboot. Upon rebooting the system, I get the boot splash and then instead of the usual start up sequence where the desktop shows up and what not, I get a bunch of messages telling me that the system is starting various services and then it hangs on starting common unix printing system. I found that after ctrl+alt+F1 brings me to a terminal I can log in and startx but hardly anything works and nautilus crashes right away. Consequently, I also have no internet connection in ubuntu now. Any ideas? 


I doubt it'll help, but heres the system specs:
MSI K9A2 Platinum (since it's addition, having weird issues)
Athlon X2 6400 3.2ghz
4gb ocz platinum ram
evga 8600 gts 512mb (running ridiculously hot for some reason)
WD sata 500gb & sata 320gb

---

### Post by Living2007 on 2008-05-26
> **LashSilence83 said:**
> here goes:
While running quite a few programs at once like I normally do, I received a message saying that amarok was not responding so even after I clicked force quit, music continued to play. One by one the other apps that were running all froze up and I couldn't access the system monitor or a terminal to kill the processes. After trying ctrl+alt+F1, ctrl+alt+backspace, and ctrl+alt+delete to no avail, I gave up and did a hard reboot. Upon rebooting the system, I get the boot splash and then instead of the usual start up sequence where the desktop shows up and what not, I get a bunch of messages telling me that the system is starting various services and then it hangs on starting common unix printing system. I found that after ctrl+alt+F1 brings me to a terminal I can log in and startx but hardly anything works and nautilus crashes right away. Consequently, I also have no internet connection in ubuntu now. Any ideas? 


I doubt it'll help, but heres the system specs:
MSI K9A2 Platinum (since it's addition, having weird issues)
Athlon X2 6400 3.2ghz
4gb ocz platinum ram
evga 8600 gts 512mb (running ridiculously hot for some reason)
WD sata 500gb & sata 320gb
Your system is overheating, buy a new fan, and decrease the amout of programs you use NOW.

Before your system melts:lolflag:

---

### Post by LashSilence83 on 2008-05-26
Yeah, I've been wondering just how hot some of these components should run and I was right to assume it was way too high. Thank you for your help! This gives me an excuse to get that antec nine hundred I've been wanting... :biggrin:

---

### Post by LashSilence83 on 2008-05-26
ok, well I'm still getting the problems on start up even with my old mobo back in and everything running nice and cool... I'm thinking I may have totally screwed something up by doing a hard reboot. How might I go about fixing that?

---

### Post by LashSilence83 on 2008-05-26
Alright, I reconfigured xorg to work with the new mobo and different gpu and tried setting bum back to default settings. Trouble is I'm still getting the boot splash and then the messages telling me that its starting various services like I explained before. It's still getting hung up on starting c.u.p.s. and then I have to force it to go to a command prompt so that I can startx. After about a minute, all the strange new screen problems go away and my desktop loads fine except network manager can't establish any network connection. This makes no sense to me as live cd's and xp have no issues with connecting atm...

---

### Post by LashSilence83 on 2008-05-26
ok, nevermind. After exhausting all options available to me, I'm going to give up and reinstall. What a total bum out.

---

### Post by Living2007 on 2008-05-26
> **LashSilence83 said:**
> ok, nevermind. After exhausting all options available to me, I'm going to give up and reinstall. What a total bum out.
This seems to be the only option left.

---

