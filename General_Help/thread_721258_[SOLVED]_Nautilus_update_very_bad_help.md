---
title: "[SOLVED] Nautilus update very bad help"
date: 2008-03-11
forum: General Help
---

### Post by Akovia on 2008-03-11
Hi,
I have noticed some nautilus updates that were listed under important but just got around to letting it update. When I logged in this morning, My program launcer bars were gone. I have a desktop cube with compiz, but the applet bars with all the programs, time, notification area, etc. are all missing.

Unfortunately, I'm not yet adept enough to even figure out how to get a console open. Luckily my browser was still open from last seesion allowing me to write this. I did r-click on desktop and tried turning off compiz but it didn't help. I also restarted X a few times but it stays the same. Even if I could get to a console I'm not sure if I would know where to start. I wish there was a way to turn back from that update. 

Please if someone could get me going in the right direction and if there is a way to turn back from the update that would be even better.

Regards,
Ako

---

### Post by scragar on 2008-03-11
use alt+F2 to get a launch command box and type:
```
gnome-terminal
``` this will give you a terminal to work in.

first things first, restarting nautilus:
```
killall nautilus
```

if that didn't fix anything(and nautilus opened up with your home dir in), try manualy launching the panels:
```
gnome-panel
```

---

### Post by Akovia on 2008-03-11
First, thanks for the quick response.

> use alt+F2 to get a launch command box and type:
Didn't work. Luckily after trying alt-tab I discovered my gnome file manager was open so I made my way to /usr/bin/gnome-terminal

Killall did close out but reopened my file manager but still no panel.

Trying to start manually produced:
A panel is already running.

I turned off my compiz and even tried hovering my mouse over the area just to make sure it wasn't transparent.

I do have a console and a file manager now though.

Ako

---

### Post by scragar on 2008-03-11
(nautilus is supposed to reopen, I was hoping that restarting it would fix the problem, or atleast give some info about it).

you could try killing of the panel's in the same way, see if you can open them properly then:
```
killall gnome-panel
gnome-panel
```

---

### Post by Akovia on 2008-03-11
You rock!

It didn't restart from the killall command, but this time it appeared when I started it from the console.I'm not sure what happened but I'm gonna try and reboot now to see if it happens again. Will report back.

Either way, thanks so much for the quick help.

Ako

---

### Post by Akovia on 2008-03-11
Ok,
It survived a reboot even though it was slower than usual. I hope that whatever happened was a fluke and worked itself out, but that's usually not the case for me. =P At least I have a supportive community to fall back on which calms my nerves.

I'll give it today to see if everthing holds together and if it does I'll mark this as solved. Once again I can't thank you enough for the help. I'm gonna spend some time to figure out why <Alt+F2> didn't open a console and try to fix that in case something like this happens again.

Best Regards,
Akovia

---

### Post by Akovia on 2008-03-12
Everything is still holding together. Looks like a fluke.

Ako

---

