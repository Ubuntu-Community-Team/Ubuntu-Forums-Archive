---
title: "[SOLVED] Lost Gksudo Nautilus"
date: 2008-01-06
forum: General Help
---

### Post by Arcnsparc on 2008-01-06
I suck.  R60 Gutsy

Okay, so I was trying to install some Nautilus scripts by unpacking them into home/.gnome2/nautilus-scripts accordng to this HOW-TO: [http://lifehacker.com/software/featured-linux-download/supercharge-your-right+click-menu-with-nautilus-scripts-269043.php](http://lifehacker.com/software/featured-linux-download/supercharge-your-right+click-menu-with-nautilus-scripts-269043.php)

Now I know i messed up such a simple thing somewhere because I cant get gksudo to open anymore, it crashes before the browser opens.  I tried to get back to where I put the files through the terminal but I couldn't see them in the terminal.  I removed nautilus with sudo aptitude remove nautilus and then reinstalled it the same way.  I thought this would fix it but it didnt... I am too afraid to try anything else without a bit of advice.  Should I switch to a different file browser to fix the problem?



EDIT: I installed Konqueror and removed both the file folder of scripts and the TAR file, both of which were stupidly placed in home/.gnome2/nautilus-scripts.  Gksudo nautilus still will not run so I did sudo aptitude reinstall nautilus.  Still no success with gksudo nautilus, however plain nautilus works just fine.  I find this very odd.

---

### Post by Arcnsparc on 2008-01-06
I got it all figured out....

I had to do the reinstall, and then remove the junk from the scripts folder.  But nothing worked right until I did a reboot, which fixed everything.  All I have to do now is to make nautilus my default file browser again...  If you came to this thread look for an answer I hope something here helped, good luck.  Im marking it SOLVED.

---

