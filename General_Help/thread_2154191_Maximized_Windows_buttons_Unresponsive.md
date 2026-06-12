---
title: "Maximized Windows buttons Unresponsive"
date: 2013-06-13
forum: General Help
---

### Post by cruz12141214 on 2013-06-13
hello currently I am using 

[B]Ubuntu 13.04 x64
gnome session fallback
compiz 0.9.9

Asus g74sx[/B] <---the hardware sould not matter in this case

and here is the issue

any time I open a window that **STARTS MAXIMIZED** the windows title bar is unresponsive IE any clicks on it 
pass right through to other windows or the desktop

now this is really annoying I have been trying google for some time now 
the only thing that turns up is information on this bug WHICH IS NOT THE ONE IM DEALING WITH
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/1158161](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/1158161)

I have no idea what to do 
the only temp fix for it is to some how get the window to unmaximize which is hard to do if i have no access to the buttons

---

### Post by mc4man on 2013-06-13
This is likely your issue - 
[https://bugs.launchpad.net/compiz/+bug/1158267](https://bugs.launchpad.net/compiz/+bug/1158267)

It has a proposed patch & some comments mention workarounds on a user basis

In any event, like most current 13.04 bugs, if a fix is committed/released it will most likely not ever show up in 13.04 packages

---

### Post by cruz12141214 on 2013-06-14
but isnt that patch for the other error?

---

### Post by CatKiller on 2013-06-14
No, this bug manifests in lots of ways. The Compiz window decoration code is a bit of a mess and needs major cleanup. I'm running an experimental branch which solves this issue, but tends to cause others.

In the meantime, you can use whichever task manager you're using to unmaximise the window. The buttons should work normally then.

---

### Post by cruz12141214 on 2013-06-14
well thats going to be a pain

---

### Post by cruz12141214 on 2013-06-15
I tried to see if i can reproduce this bug with emerald and compiz, and so far so good it has not happened

---

