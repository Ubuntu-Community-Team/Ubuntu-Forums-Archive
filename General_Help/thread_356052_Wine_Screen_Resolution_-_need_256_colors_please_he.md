---
title: "Wine Screen Resolution - need 256 colors please help"
date: 2007-02-08
forum: General Help
---

### Post by andytof47 on 2007-02-08
Hi 

I'm Running Wine - Installed from automatix

I am trying to run a kids game that needs 256 colors - thats what the dialogue box is telling me

In windows I would just change the resolution easily with the systems gui

Buuut It doesn't seem so easy in edgy

Any help?


cheers:KS

---

### Post by MoLE on 2007-02-16
This seems to be a well-known problem.  There seems to be a method for doing this using xnest.  I would suggest:
```
sudo aptitude install xnest
```
then follow the instructions on the [WineWiki]("http://wiki.winehq.org/User_FAQs")

---

### Post by Adam_GUI on 2007-07-21
> **MoLE said:**
> This seems to be a well-known problem.  There seems to be a method for doing this using xnest.  I would suggest:
```
sudo aptitude install xnest
```
then follow the instructions on the [WineWiki]("http://wiki.winehq.org/User_FAQs")

Sorry to bump such an old thread.  But, I'm having the same problem.  I apt-got xnest, but the wine Wiki page seems down....I'll check again.  Nope, no main wiki page.

Played around a bit.

Running wine C:\\COMPANY\\FOLDER\\PROGRAM.exe -xnest gives me the same result.
How do I set xnest to an 8-bit display?

EDIT:
Found this post, here:  [http://ubuntuforums.org/showpost.php?p=2667240&postcount=2](http://ubuntuforums.org/showpost.php?p=2667240&postcount=2)
I'm getting an error message that no driver could be found.  How do I go about adding a driver?

---

### Post by MoLE on 2007-07-22
Have you tried the workarounds on the [wine site]("http://wiki.winehq.org/256ColorsWorkarounds")?

---

