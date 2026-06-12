---
title: "OpenOffice Slow in Gutsy?"
date: 2007-11-27
forum: General Help
---

### Post by FXFman1209 on 2007-11-27
Ever since I upgraded to Gutsy, whenever I go to OpenOffice from another program, the icons take a few seconds to load.

Is anyone else having this problem? Can anyone help me?

---

### Post by mjitkop on 2007-11-27
I have the same problem too. Not only is it extremely slow on my PC but sometimes it freezes completely. This happened once when I tried to copy and paste the content of a live chat session. OpenOffice Writer froze when I did paste and I never got my data pasted. I had already closed the live session window so I lost all my data. :mad: Lesson learnt.
Hopefully this will be fixed in the next version of OpenOffice or Ubuntu.

---

### Post by ajgreeny on 2007-11-27
> Ever since I upgraded to Gutsy, whenever I go to OpenOffice from another program, the icons take a few seconds to load.

Is anyone else having this problem? Can anyone help me?Which icons do you mean?  Those in the taskbar or are you talking about the splash screen at startup of OOo?  Have you tried the quickstart utility for OOo which can make a document open in about 4 -5 seconds from cold on my machine (sempron 2400+, 1GB ram, ati 9200SE graphics).  It is worth using, if not.

---

### Post by secret_squirrel on 2008-01-03
I've seen this as well.  It's a real issue and nothing to do with the Quickloader.

I'm running Gutsy on a Thinkpad T42 - reasonably speedy CPU, 1.5GB RAM.  No performance issues on the PC: no swapping, no excessive disk i/o, CPU OK. 

Most apps are fine, but OOo is very sluggish.  It starts up OK, but then immediately redraws the icons along the top, taking a few seconds.  Normal typing is OK, but menus are slow and the icons get redrawn all the time. In calc, switching between tabs is painfully slow.  

I thought it might be an issue with the Ubuntu build of OOo (which had crashing issues on my wife's Gutsy PC) so I uninstalled and installed OOo 2.3.1 from the OpenOffice.org website.  Made no difference at all.

Any other ideas would be gratefully received.

---

### Post by secret_squirrel on 2008-01-09
More info on this issue.  Unfortunately, I'm going to have to switch to another distro soon if I can't figure this out.

OpenOffice is slow in some ways: redrawing button icons is very slow, as is redrawing tabs in calc.  Typing is also sluggish, but navigating around a spreadsheet is normal speed, as is opening new documents and cut/paste.

Although Firefox is fine, Thunderbird is sluggish, especially for typing, so it isn't just OpenOffice.  

Other apps all seem fine, but I've noticed that opening some apps (inc. Firefox, but not most native Gnome apps) I can see the border lines being drawn before the app opens.

---

### Post by techstop on 2008-01-09
I find that tweaking the memory settings as shown here really help with the speed of OOo.

[http://www.zolved.com/synapse/view_content/28209/How_to_make_OpenOffice_run_faster_in_Ubuntu](http://www.zolved.com/synapse/view_content/28209/How_to_make_OpenOffice_run_faster_in_Ubuntu)

Let me know how you go....

---

### Post by njparton on 2008-01-09
Try uninstalling compiz and then setting metacity as your default gnome window manager.

---

### Post by secret_squirrel on 2008-01-09
Thanks for the suggestions.

I've now tried both of those: increasing the graphics memory in OOo, uninstalling Compiz and using metacity (well, in Gutsy I can't find anything that explicitely says "metacity" as there was in previous versions, but in System > Preferences > Appearance > Visual Effects I've set "none").

Unfortunately, none of it's made any difference at all - symptoms exactly as before.

---

### Post by njparton on 2008-01-09
If you uninstall compiz then you'll probably have to reassign metacity as the default window managed by running gconf-editor and hunting down the option.

If you're not missing title bars or experiencing any other odd behaviour then chances are you've not fully uninstalled compiz (although I may be wrong).

---

### Post by secret_squirrel on 2008-01-09
Thanks.  

I ran gconf-editor and tracked down the setting in Desktop > Gnome > Applications > Window Manager.  It was already set to use /usr/bin/metacity so I think Compiz is out of the picture.

---

