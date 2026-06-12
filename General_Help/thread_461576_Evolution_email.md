---
title: "Evolution email"
date: 2007-06-01
forum: General Help
---

### Post by BobLand on 2007-06-01
I just abandoned JPilot because it refuses to import my contact lists from either TB2 or PalmVI.  Out of 150 contacts I only get partial data for 32.

I just installed Evolution.  When I imported a ldif file that I had lying around it filled up memos and calendars that I thought JPilot deleted.  So, I'd like to stabalize my data before moving elsewhere.

My main problem is writing new email.  The "To:" button brings up a random list of names between B and C.  I can't seem to change this behavior.  Googled "Evolution Contacts" and came up with about 200 versions of a 6 entry thread but not much else that even hinted at what might be the problem.

Sadly, most posters agreed that Linux does not have anything that resembles a working PIM.  I've used the Palm Desktop for that past 5 years and it served me well.  But no such app exists for Linux.  Currently, I'm using TB2 which is OK but I need the ToDos, Memos, and Calendar (hate Lightning) functions.

Is it possible to load the "To:" button with the complete contacts list?

Thanks,
bobland

---

### Post by BobLand on 2007-06-02
Anybody?

---

### Post by zanglang on 2007-06-02
I agree on Linux lacking a consistent, stable PIM, Evolution doesn't cut it for me as well. :/

While I can't offer you any advice on the TO: problem (you should probably try checking if this behaviour has been documented before on [Launchpad]("http://bugs.launchpad.net/ubuntu"), and if not, submit a bug for it. Also, for lighter weight apps, you can try Contacts, Tasks and Dates ('aptitude install contacts dates'). Tasks is available here: [http://pimlico-project.org/](http://pimlico-project.org/)

---

### Post by BobLand on 2007-06-02
The biggest problem I have with Evolution, JPilot and Kontact is the inability to import full data sets from the palm.  Each app will import different parts or incomplete parts.

I'm thinking my only resource at this point is to rig up the Palm Desktop in Windows using Wine.  Since my memory has become somewhat unreliable I depend very heavily on a PIM. 

All of the above are so buggy that they scare me.  Here today, gone tomorrow.

Is this a problem unique to Linux?

---

### Post by BobLand on 2007-06-02
I installed pimlico, at least I think I did.  
```
sudo apt-get install contacts dates tasks
```

What I got did not look like pimlico.  To make matters worse, the data was corrupted just like it is in DeEvolution.

I added the line in sources.list but don't know where to go from there.

---

### Post by pt123 on 2007-09-22
thanks but you need to update the sources list.

---

