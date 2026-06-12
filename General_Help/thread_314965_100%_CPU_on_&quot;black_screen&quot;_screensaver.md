---
title: "100% CPU on &quot;black screen&quot; screensaver"
date: 2006-12-08
forum: General Help
---

### Post by timetunnel on 2006-12-08
Hi there,
I use the "black screen" screensaver that just shows a black screen when the screensaver starts. :eek: I also have set it to lock the session so that I have to enter my password when I want to use the computer again. 

The problem is that the CPU seems to go up to 100% while the black screen sceensaver is active. When I re-login, the temperature is up to 71 and more degrees celsius, which goes down to 48 degrees after re-login.

The black sceen should't use very much resources obviously, so I wonder what the reason could be. How could I nail down the culprit?

Thanks,
Jens

---

### Post by wedge2k on 2007-03-13
I have a similar issue, I have my screensaver just blank and hits 100% cpu the whole time. 

I have a laptop (IBM x31) latest patches Kubuntu 6.10  

This shouldn't be a graphics driver issue, its just blanking the screen.  Any thoughts?

---

### Post by cdyson37 on 2007-03-21
Exactly the same problem with my Toshiba laptop - very irritating since whenever the screensaver comes on the fan starts whirring at high speed! Anybody know how to fix...?

---

### Post by timetunnel on 2007-03-21
I tried to narrow it down some time ago and sometimes it even happened when the "blank screen screensaver" *wasn't* in action. On my PC, it doesn't *always* happen, and it doesn't happen as soon as the screensaver starts, but sooner or later. Sometimes not at all. I don't remember anymore why, but after a while I began suspecting "beagled", which seems to think "hey, that thing is idle now for quite a while, let's rummage the harddisk for new things to index"...

---

### Post by cdyson37 on 2007-03-21
I just tried killing all beagle related things from the command line and letting the blank screensaver come on and no significant cpu usage was recorded, so it looks like resource hogging on the part of beagle is the culprit. I'm worried it'll knacker my CPU fan at the present rate! I don't want to switch it off completely, perhaps it can be set to only scan once a day...?

---

### Post by dtmilano on 2007-03-28
See also [https://launchpad.net/ubuntu/+source/beagle/+bug/77106](https://launchpad.net/ubuntu/+source/beagle/+bug/77106)

---

