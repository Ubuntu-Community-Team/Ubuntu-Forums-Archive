---
title: "slow after upgrade"
date: 2007-10-19
forum: General Help
---

### Post by goldan on 2007-10-19
Hi i upgraded to 7.10 from network.
now my computer is realll slow i bearly can firefox 
any idea why ?
and how can i fix it ?
i choose no effects in the effects window
pleas help
thanks ahead.

---

### Post by mlissner on 2007-10-19
You need to figure out what the offending process is. Try running ```
top
```, and see what is on top in terms of processes.

My bet is that tracker is building your database, in which case, all is well.

---

### Post by goldan on 2007-10-20
'well i do have trackerd
and tracker-extract
but its over a day already
for how long should it run ?

---

### Post by goldan on 2007-10-20
well now.. the tracker extract cant see it on top anymore
and the computer is sure is a litlle more faster. can browse the net noW :D
that sucked.
over 24 hours it was like that weird i didnt read it on the fourm or on ubuntu site abou this kinda thing could happen.
not to say the upgrade went all wrong and i had to ask some expert to fix my comp without reinstalling everything. :\

---

### Post by -Zeus- on 2007-10-20
what's your system specs?

---

### Post by mlissner on 2007-10-20
Yeah, if you have a rather old system with a rather lot of files, emails, etc., tracker is going to take some time to do its thing. What it is doing is building a database of all your information.

Try searching for something arcane on your computer, you'll be surprised how quickly it comes up. This is the upside to the time it takes it to build the database.

That does sound extreme though.

---

### Post by goldan on 2007-10-21
zeus:
p4 1.6Ghz 256 sdram 40gb HDD

---

