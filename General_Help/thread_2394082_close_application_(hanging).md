---
title: "close application (hanging)"
date: 2018-06-12
forum: General Help
---

### Post by marchello_lippi2 on 2018-06-12
Hi all, 
I got my SoapUI application hanging. Tried to close using Alt+F4, pressing cross in the right upper corner, no luck. 
Tried to see its process name using top, no luck as well. 
Ok, I started another instance of SoapUI and it works so far. But how do I get rid of that hanging window of my previous instance? Seems like reboot is needed, but I don't want to.
Please advise.

---

### Post by Holger_Gehrke on 2018-06-12
You could try running 'xkill' in a terminal and clicking in the  misbehaving window. That would close the connection between the  application and the X-Server. Well-behaved programs shut down when this  happens.

If it's that [SoapUI]("https://en.wikipedia.org/wiki/SoapUI"), then it should come up in top with the column 'command' showing 'java'. Or you could try 'ps -f -C java' in a terminal. this would give you a listing of all running instances of java. you could then use the 'kill' command with the PID of the process to stop it.

Holger

---

### Post by marchello_lippi2 on 2018-06-12
[COLOR=#DD4814][COLOR=#000000][Holger_Gehrke]("https://ubuntuforums.org/member.php?u=1961578"),[/COLOR][/COLOR]
cool, thx
>>> [COLOR=#000000]try running 'xkill' in a terminal and clicking in the misbehaving window[/COLOR]

---

### Post by TheFu on 2018-06-12
xkill.

Run xkill on the same machine running X/Windows, then move the mouse pointer to the window you want to kill and click.  When you run xkill, the mouse pointer should change to a scull and crossbones. ;)   The click sends a "TERM" signal to the window.  A CLOSE signal isn't working for some reason. Code that doesn't handled signals correctly needs to be fixed. If the code isn't handling signals specifically, then there is probably a wild pointer doing harm.

No idea if this will work on Wayland.

---

