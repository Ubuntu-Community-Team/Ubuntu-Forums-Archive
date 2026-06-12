---
title: "screenlets"
date: 2008-04-02
forum: General Help
---

### Post by bluefox83 on 2008-04-02
Not certain if this really goes in here, but I can't really think of anywhere else to put it so...

I downloaded a screenlet called Pandora. The problem, is when i click for Screenlets to install it, everything goes fine at first, even says it's been installed sucessfully. then it starts spawning multiple copies of the screenlets daemon! it never stops! i have to "killall python" to get it to stop. anyone know how to fix that?

---

### Post by Crafty Kisses on 2008-04-02
> **bluefox83 said:**
> Not certain if this really goes in here, but I can't really think of anywhere else to put it so...

I downloaded a screenlet called Pandora. The problem, is when i click for Screenlets to install it, everything goes fine at first, even says it's been installed sucessfully. then it starts spawning multiple copies of the screenlets daemon! it never stops! i have to "killall python" to get it to stop. anyone know how to fix that?

That's weird, do they keep spawning, or at a point they stop?

---

### Post by Whise on 2008-04-02
that happends because you have pandora screenlet...

---

### Post by AutoGyro on 2008-04-18
> **bluefox83 said:**
> Not certain if this really goes in here, but I can't really think of anywhere else to put it so...

I downloaded a screenlet called Pandora. The problem, is when i click for Screenlets to install it, everything goes fine at first, even says it's been installed sucessfully. then it starts spawning multiple copies of the screenlets daemon! it never stops! i have to "killall python" to get it to stop. anyone know how to fix that?


I'm having the same problem, and it appears to be caused by the Pandora screenlet.  How does one remove it?  I've tried, but considering I'm still new to the whole Linux thing, I don't know how to completely get rid of the malicious code.  I've tried complete removal through Synaptic, deleting the hidden config files, and even
```
sudo apt-get remove --purge screenlets
```but once I reinstall the package, the same problem occurs!  Any *real *help is greatly appreciated!

EDIT:

Okay, so I should have taken another 5 minutes to sift through Google before I posted this.  Apparently, the Pandora screenlet is missing a line of code as referenced in the comments here: [http://www.gnome-look.org/content/show.php/Pandora+Screenlet?content=72525](http://www.gnome-look.org/content/show.php/Pandora+Screenlet?content=72525)

Anyway, delete the Pandora folder from your home/"user"/.screenlets folder to fix the problem.  Apparently, this isn't the first screenlet to have this problem--the Slacker screenlet (also by the same author?) had the same problem.

---

