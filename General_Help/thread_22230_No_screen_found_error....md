---
title: "No screen found error..."
date: 2005-03-26
forum: General Help
---

### Post by jehnx on 2005-03-26
I'm sorry if I shouldn't be asking this here, but I had a program during my installation:

At the end, there is no GUI.  When I view the error log, it is saying that xwindows can't detect a screen.  I've currently got a ViewSonic 17 inch LCD (model VA720), and a PCI Radeon 9200 as my graphics card.

Here are the specs to my monitor:  [http://www.viewsonic.com/support/desktopdisplays/lcddisplays/aseries/va720/](http://www.viewsonic.com/support/desktopdisplays/lcddisplays/aseries/va720/)

I imagine I can edit something and get this working manually, but as I'm quite new to Linux I'm not sure where I should be going to fix the problem.

Anyone know what I can do?  Help is appreciated.  :)

---

### Post by alastair on 2005-03-26
What says :

/etc/X11/xorg.conf

/var/log/Xorg.0.log

---

### Post by ntd on 2005-03-26
Try hitting ctrl+alt+f7 and see if anything pops up

---

### Post by jehnx on 2005-03-26
I figured out my problem!

See, during the installation, it asks what resolutions you would like the programs to try your monitor as.  It says you can check them all or check none of them, and either way it'll just try everything.  Well, previously I had been checking none of them at all, so that it could try all resolutions (I wasn't sure of my maximum), but after seeing that /etc/X11/xorg.conf was completely blank, I decided to try to check a few of them.  Well, I did that, and it worked great.  :)

Thanks for your help folks!

---

