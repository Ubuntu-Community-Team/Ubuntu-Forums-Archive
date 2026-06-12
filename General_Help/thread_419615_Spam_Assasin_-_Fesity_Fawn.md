---
title: "Spam Assasin - Fesity Fawn"
date: 2007-04-23
forum: General Help
---

### Post by Gorlist on 2007-04-23
Hi, yesterday upgraded to Feisty Fawn, so far no problems accept Spam Assassin appears not to be filtering emails? (ive gone from nearly never having to spam to loads of spam unfiltered). 

Ive tried removing and reinstalling Assassin, though no luck - any suggestions?

Regards!

---

### Post by Gorlist on 2007-04-24
Any one? at the moment its not moving any email to the Junk folder, though ive checked to make sure its enabled in Evolution.

Regards!

---

### Post by rbmorse on 2007-04-24
Start a mail download with Evolution.  Press <ctrl>+<esc> to open the task window and see if there is a process for Spamassassin and one spamd for each mail account running.

---

### Post by Gorlist on 2007-04-25
Thanks for the reply, if I hit ctrl + esc whilst downloading email nothing appears?

---

### Post by rbmorse on 2007-04-25
My fault.  That's a KDE trick and I forgot where I was.  

Open Gnome's task manager then start Evolution and begin to retireve mail, It should spawn processes for spamassassin and spamd. 

If it doesn't, spamassassin isn't loaded or not properly setup, I'd start with removing it,followed by reinstalling it from repository.

---

### Post by Giorgio on 2007-04-28
Same problem here after upgrading to feisty. Solved unchecking the bogofilter plugin in plugin preferences.

---

### Post by Gorlist on 2007-04-30
Hi,

**@ rbmorse ** -  where abouts can I find Gnomes Task Manager? I have tried a full reinstall of Spam Assassin by the synaptic package manager.

**@ Giorgio** - Oh right!, so you disabled the "bogofilter" and that fixed the issue? 

Regards!

---

### Post by dcstar on 2007-04-30
I ended up no longer using Spamassassin and changing over to Bogofilter, now my Evolution Junk filtering seems a lot faster... :)  (disable the Spamassassin plugin, though)

---

### Post by Giorgio on 2007-05-02
> **Gorlist said:**
> 
**@ Giorgio** - Oh right!, so you disabled the "bogofilter" and that fixed the issue? 

Right. This unblocked things for me.

---

