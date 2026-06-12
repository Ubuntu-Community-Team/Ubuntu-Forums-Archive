---
title: "Desktop freezed but mouse and superkaramba still works"
date: 2008-02-26
forum: General Help
---

### Post by ravi.xolve on 2008-02-26
I use Kubuntu 7.10. The problem is that if I leave my pc unattended for a few minutes the CPU usage goes to 100% (this I know through superkaramba theme) and the task bar becomes unresponsive - no tooltips, no clicks nothing. And adding to it what problems me most is that the system tray clock, superkaramba themes still show the output, the music in background still works and I can still move the mouse.

I usually run amaroK, Kopete, superkaramba, konqueror and konsole. I have tried closing various applications but still the problem persists. Please Help.

---

### Post by ravi.xolve on 2008-02-26
Hey please somebody helpppppp!!!! :cry:

---

### Post by ravi.xolve on 2008-02-26
I identified the problem. Its Xorg that consumes all of the CPU please help me now. :(

---

### Post by jschaab on 2008-02-26
I think I'm having the same or a similar issue with my Xubuntu installation, although the frequency is lower. I installed Xubuntu 7.10 on Saturday, and so far have experienced 3 freezes. When this happens by desktop becomes completely unresponsive, except that the mouse will move (the cursor will not change though, so it remains a text entry cursor even if I move it to a place that would normally cause it to revert to an arrow). I can still ssh into the machine from my Mac, and saw that Xorg is using approximately 97% of my cpu.

---

### Post by ravi.xolve on 2008-02-26
Thats exactly the problem. I hope somebody solves it here.

---

### Post by O_Man_RA23 on 2008-02-26
May be a little off topic, but a VERY similar thing used to happen to me in Winblows XP.  Anything that was made by MicroShaft and accessed the intahweb (ie Outlook, Internet Exploder or MSN Messenger) would lock my computer up if left idle for 10mins or so.  The CPU would be at 100% (AMD 64bit processor, 3200+) and ram usage would be quite a way up (2Gbyte total on my system... it would chew about 3/4 of it).

Hope this might point somebody towards finding your issue... and just because Xorg is using the resources, does not mean that Xorg is the cause of the problem.

---

### Post by tripmix on 2008-03-28
I think this has something to do with xorg and superkaramba not palying nice at the moment. The problem goes away for me if I stop superkaramba.

---

