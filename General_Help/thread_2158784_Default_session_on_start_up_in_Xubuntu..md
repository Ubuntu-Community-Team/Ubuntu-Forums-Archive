---
title: "Default session on start up in Xubuntu."
date: 2013-06-30
forum: General Help
---

### Post by charlie_barkin on 2013-06-30
how to I prevent this from showing up when I start up my computer in xubuntu
[IMG]http://i136.photobucket.com/albums/q197/charlie_b_barkin/IMG_20130630_152252.jpg[/IMG]
it is pretty anoying

---

### Post by Bucky Ball on 2013-06-30
I did a minimal install recently and had this exact same problem, wracking my brain as to how I fixed it, though.

For starters, make to log out or restart but check the box 'Save Session' is not ticked before you do. Mine was and I figured it had something to do with that. 

I'll keep trying to think of how I solved this. I'd say make that change and perhaps shutdown or restart rather than logout and in.

---

### Post by Bashing-om on 2013-06-30
charlie_barkin; Hi !

Looks like a different issue ... but;

++
xfwm is the window manager, it has nothing to do with the panels -> different problem.
In this case maybe the session cache got corrupted ?
First try starting the panel from the login session, ctl+alt+f1;
login to the text console;
Terminal command:
```
xfce4-panel &
```
Anyway, your panel settings are safe in ~/.config
What results ?
You can also clear the session cache: logout, ctrl+alt+f2, login in the text console again and
```
rm -rf .cache/sessions
```
ctrl+alt+f7,  and login again to the GUI console.
Now if all looks good, save the session: Setting manager > Session and startup > Session > Save session
----------------
If there continues a problem, comply with Bucky Balls's directive and start another thread with a descriptive title to gain visibility.

[INDENT][INDENT]workie great ?[/INDENT][/INDENT]

---

### Post by Bucky Ball on 2013-06-30
*Post moved to own thread in **General Help**.*

Sorry, my mistake. For some reason I thought this post was the first in a new thread but was in fact buried on an old one, so this post has been moved to its own thread. 

Please do not hijack threads. It is confusing, dilutes effort, reduces your chances of help and is unfair to OP. 

Please feel free to change the title of the thread to something more descriptive and if you can't, give me a word and I'll do it for you. Cheers.

---

