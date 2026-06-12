---
title: "Windows Gone Wild"
date: 2007-12-27
forum: General Help
---

### Post by djgotsoul on 2007-12-27
Hello,

Hopefully someone out there with more Ubuntu experience than I can help me with this one.  Yesterday, upon returning home, I switched on my computer and once I logged in to my Ubuntu account, I found that all the windows (regardless of the application I opened) are missing that top bar that generally displays the name of the application and has the three buttons to minimize, maximize, or close the window.  Also, moving and resizing windows has become impossible via the conventional way.

I can still do all these things if I right-click on the window's name in the task panel, but not on each window itself.

Can anyone help me with this unique problem?  I've never seen anything like it.

Thanks
DJGotSoul

---

### Post by dasunst3r on 2007-12-27
It seems to me that your window borders are missing.  To get them back, do the following:
[list=1]
[*]Go to Applications -> Accessories -> Terminal.
[*]Type in the italics portion of this line: *metacity --replace &*
[*]Type *exit*
[/list]
*metacity* is the thing responsible for drawing what you described, called "window borders."  Hope this helps!

---

### Post by jken146 on 2007-12-27
Don't forget to save your session afterwards.

---

### Post by t3hi3x on 2007-12-27
lol, the name of the post makes me want to help.

anway, basically there are a few programs that run that bar:

if you arent using effects its metacity

if you are using effects its emerald

try hitting ALT + F2 and type in ```
metacity --replace
``` if that doesnt work try ```
emerald --replace
```.

that should make them appear again.

---

### Post by dasunst3r on 2007-12-27
The reason why I wanted *djgotsoul* to use the terminal was because Alt+F2 does not seem to work when the window borders are gone for me.  Can someone confirm/refute this?

---

### Post by djgotsoul on 2007-12-28
I tried the Alt+F2 method and it worked perfectly.  Thanks so much!!

---

