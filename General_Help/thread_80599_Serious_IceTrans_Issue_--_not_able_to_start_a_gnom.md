---
title: "Serious IceTrans Issue -- not able to start a gnome session"
date: 2005-10-22
forum: General Help
---

### Post by tregetour on 2005-10-22
I get the gnome graphical login. Enter my uname & password. And then It tells me that my session lasted less than 10 seconds and spews back to the login screen. The failsafe sessions does the same, only the xterm session works. So I have nothing but the command line. The error it gives is:

_IceTransNoListen: unable to find transport tcp
_IceTransmkdir: ERROR: euid !=0,directory /dev/X will not be created
_IceTransmkdir: ERROR: Cannot create /dev/X
_IceTransPTSOpenServer: mkdir(/dev/X) failed, error=13
_IceTransOpen: transport open failed for pts/golem
_IceTransMakeALLCOTSServerListners: failed to open listener for pts
_IceTransISCOpenServer: Protocol is not supported by a ISC connection
_IceTransOpen: transport open failed for isc/golem
_IceTransMakeALLCOTSServerListners: failed to open listener for isc
_IceTransSCOOpenServer: Protocol is not supported by a SCO connection
_IceTransOpen: transport open failed for sco/golem
_IceTransMakeALLCOTSServerListners: failed to open listener for sco

Any help getting my GNOME back would be very very much appreciated!!

[[p.s. I had to copy the error message my hands so minor discrepencies may have crept in.]]

Thank you in advance again! [I'm stuck on an old windows machine till this gets fixed.]

---

### Post by souled on 2005-10-23
I am getting this exact same problem. I have no idea what's causing it or how it happened. After 4 days of uptime, I decided to restart my computer and I starting getting this error. Please post if you find a solution!

---

### Post by AllenP on 2005-10-23
I'm having the same problem. It's the second time that it's happened to me. I really dont feel like reinstalling ubuntu again now that i got it working the way that i want.
Help would be appreciated.

---

### Post by souled on 2005-10-23
I've fixed the problem. Somehow, the .ICEauthority file changed permissions (not sure how or what the file is), so I just use sudo chown, and it worked. One question to those getting this problem though. When GDM starts up, are the colors all funky or is it just me? Because I'm not sure if this is from the ICE problem or a video problem. It's mostly another source of error but I need to make sure.

So again, use ```
sudo chown (username) .ICEauthority
```

---

### Post by VR6Pete on 2005-10-23
I've had this problem, I just renamed .ICEauthority and gnome re-created it for me, I'll bare te chown fix in mind - thanks.

---

### Post by tregetour on 2005-10-23
Thank y'all. One of the reasons I love Ubuntu is the great community!

---

### Post by Suman on 2005-10-26
Thanks a zillion "souled" for posting the solution. I was very close in re-installing Ubuntu all over again. My problems started (so it seems) after installing amarok. BTW I'm a Linux/Ubuntu noob and loving every bit of it.

---

### Post by Matriz on 2005-10-28
thanks...i had this problem on breezy prebuild and now i have it again on final..hope that metod works...ubuntu has great community indeed.

---

### Post by linuxwhatsthat on 2005-11-10
Hooah Soldiers AA up and runnin now thanks to this post:)
Works great in linux:)

---

### Post by rjwood on 2005-11-10
[quote=tregetour]I get the gnome graphical login. Enter my uname & password. And then It tells me that my session lasted less than 10 seconds and spews back to the login screen. The failsafe sessions does the same, only the xterm session works. So I have nothing but the command line. The error it gives is:

_IceTransNoListen: unable to find transport tcp
_IceTransmkdir: ERROR: euid !=0,directory /dev/X will not be created
_IceTransmkdir: ERROR: Cannot create /dev/X
_IceTransPTSOpenServer: mkdir(/dev/X) failed, error=13
_IceTransOpen: transport open failed for pts/golem
_IceTransMakeALLCOTSServerListners: failed to open listener for pts
_IceTransISCOpenServer: Protocol is not supported by a ISC connection
_IceTransOpen: transport open failed for isc/golem
_IceTransMakeALLCOTSServerListners: failed to open listener for isc
_IceTransSCOOpenServer: Protocol is not supported by a SCO connection
_IceTransOpen: transport open failed for sco/golem
_IceTransMakeALLCOTSServerListners: failed to open listener for sco

Any help getting my GNOME back would be very very much appreciated!!

[[p.s. I had to copy the error message my hands so minor discrepencies may have crept in.]]

Thank you in advance again! [I'm stuck on an old windows machine till this gets fixed.][/quote]

I think k3b is the culprit. It was for me anyway

---

### Post by souled on 2005-11-10
For me it was amaroK

---

### Post by ringding on 2005-11-20
[QUOTE=rjwood]I think k3b is the culprit. It was for me anyway[/QUOTE]

I think you may be right .....  this happened to me right after I burned my 1st CD with k3b.......

Thanks "souled"

My video was fine.......

---

### Post by kevin_hill54 on 2005-11-22
Nothing worse than turning off the computer during a thunderstorm only to find it doesn't start when you turn it back on.

I had a minor panic but wrote down the message and went to work.

Thanks to this forum the panic is over and I will go home and fix the problem.

My computer has been running for several weeks without turning off and I have installed and upgraded a lot of stuff so I can't shed any light on what caused the problem.

I will report back if I can think of a reason.

Thanks again everyone for being such a great community

Kevin

---

### Post by souled on 2005-11-22
[QUOTE=ringding]My video was fine.......[/QUOTE]

Yeah I found out something was wrong with my ATI drivers.

---

### Post by christhemonkey on 2006-01-10
This is exactly what was wrong with my system the ICEauthority thing, love this community so much :D

---

