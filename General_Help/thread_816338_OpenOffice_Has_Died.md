---
title: "OpenOffice Has Died"
date: 2008-06-02
forum: General Help
---

### Post by blink0072005 on 2008-06-02
Hopefully this is the right forum.  So you know, I'm currently on Heron.

I've been trying to update my Openoffice.org through Synaptic, but no matter what I do, I get an error akin to "E:  openoffice.org-writer is in a very bad inconsistent state...".  I really don't know what to do here, I've researched this a bit and tried various combinations of "dpkg --configure -a", "apt-get clean", "apt-get update", "apt-get install -f", and "apt-get -f install".  I've also tried going into /var/cache/apt/archives and deleting the writer .deb, but that doesn't help anything.

It won't let me install any of the other packages without this one, and I can't open my actual OpenOffice writer program anymore.  Any help would be amazing.

---

### Post by cmnorton on 2008-06-02
What about de-installing and purging open office, and then re-installing it?

---

### Post by blink0072005 on 2008-06-02
> **cmnorton said:**
> What about de-installing and purging open office, and then re-installing it?

I was hoping to not have to do that.  Is there some way I can remove OpenOffice without losing things like my custom dictionary?  (Is this the difference between "Mark for Removal" and "Mark For Complete Removal"?).  

Also, I'm not sure if this has anything to do with it, but before this happened, the update manager told me it could only do a partial upgrade, but always hung on when I tried to do that (I don't remember how I searched the forums to fix it).  I also have all sources checked for updates, including Proposed Updates (is that a problem, or fine in general?)  Sorry for the newbie questions, but I'm still (relatively) new to Ubuntu.  Thanks.

---

### Post by cmnorton on 2008-06-03
There is probably a way to preserve your dictionary. I do not know how to do that. You can always try re-installing without purging, and see how that goes, but you may lose your dictionary in that case as well.

---

### Post by rbmorse on 2008-06-03
Your user dictionary is located in /~/.openoffice.org2/user/wordbook/standard.dic if you accept the default, or whatever name you assigned if you created a user dic with a different name.  Copy the file off to a safe place and then restore it after you purge and reinstall the application software. 

Note...it might be a good idea to test the new installation before you restore the dictionary file just to make sure the problem isn't caused by a corrupted .dic. Stranger things have happened.

---

### Post by blink0072005 on 2008-06-04
So I ended up reinstalling and it worked.  Apt-get never would let me remove openoffice.org-writer though, even with sudo.  Thanks on the dictionary tip, it wasn't that...I don't know really know what went wrong, but I'll consider this solved.

---

### Post by hihihi on 2008-06-05
somethings messed up.
everytime i get the updates from openoffice, its just a partial one and i end up always with dependencie problems, grml

---

### Post by pawelmsdb on 2008-06-23
Hi there, I have a similar problem. after installing updates in hardyheron my open office.org. wouldn't start. what should i do?

---

