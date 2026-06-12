---
title: "[SOLVED] Can't uninstall broken deb."
date: 2008-02-05
forum: General Help
---

### Post by papafreebird on 2008-02-05
Okay what I did was converted an rpm to a deb using alien.  The conversion went okay.  I tried to install the new deb and it failed.  The problem is the program is now showing up in my synaptic package manager but I can't remove it.  I've tried to remove it it through synaptic, apt-get, and aptitude to no avail.  So now I have updates I cant get to because the software index is broken.  I've tried sudo apt-get install -f  to fix the index but no joy.  

Is there anything I can do to fix this short if reformating and reinstalling.

edit
solved!  See link in my second post for more info.

---

### Post by az on 2008-02-05
> **papafreebird said:**
> Okay what I did was converted an rpm to a deb using alien.  The conversion went okay.  I tried to install the new deb and it failed.  The problem is the program is now showing up in my synaptic package manager but I can't remove it.  I've tried to remove it it through synaptic, apt-get, and aptitude to no avail.  So now I have updates I cant get to because the software index is broken.  I've tried sudo apt-get install -f  to fix the index but no joy.  

Is there anything I can do to fix this short if reformating and reinstalling.

You certainly don't need to reformat!

post the output from

sudo apt-get -f install



If it tells you to run  

sudo dpkg --conrifure -a

then run that.

---

### Post by nibirumarduk on 2008-02-05
Tried sudo dpkg -P packagename or sudo apt-get --purge remove packagename yet?

---

### Post by papafreebird on 2008-02-23
Thanks for replying to my thread!

Sorry for my delay in responding.  I forgot to put instant email notification for replies when I originally posted this so I didn't know anybody posted.  

I tried the suggestions from az earlier (before I realized you responded actually) and they didn't work... however

I solved this problem by following the instructions at this link.
[http://ubuntuforums.org/showpost.php?p=931082&postcount=14](http://ubuntuforums.org/showpost.php?p=931082&postcount=14)

Thanks for trying to help
papafreebird

---

