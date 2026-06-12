---
title: "Cant open files or shutdown"
date: 2018-04-13
forum: General Help
---

### Post by nirubu2 on 2018-04-13
Hello
I started up my laptop from suspend mode today and suddenly ubuntu is behaving very weirdly. The wlan isnt able to connect anymore, Im unable to open any files("Unable to open document...") or move/copy stuff("Error while copying"). When I click shut down the screen starts flickering for a sec while the desktop icons disappear(like they would on a normal shut down), but they then immediately reappear and nothing else happens. Holding the power button doesnt change anything either.
A week ago I had a similar problem where the screen just stayed black after decription of the SSD. I fixed that by restarting. Is my SSD broken? What can I do to fix this?
Edit: I also cant use the terminal, do a computer search or pretty much anything else.

---

### Post by TheFu on 2018-04-13
What you are seeing could be the early signs of a failing ssd.   Get those backups working. I started seeing similar issues a little before my SSD died completely. I have backup religion, so when it did fail (never to be accessible again) I had a backup from the last night to restore when a new SSD was bought.

For me, the symptoms (going read-only) happened about once every 2 weeks leading up to the failure, but there's no way to know how much or little time the SSD will last.

Unix systems use temporary files for lots and lots of needs. If the file system is readonly, those temp-files can't be created, so those tasks don't work.

---

### Post by nirubu2 on 2018-04-13
> **TheFu said:**
> What you are seeing could be the early signs of a failing ssd.   Get those backups working. I started seeing similar issues a little before my SSD died completely. I have backup religion, so when it did fail (never to be accessible again) I had a backup from the last night to restore when a new SSD was bought.

For me, the symptoms (going read-only) happened about once every 2 weeks leading up to the failure, but there's no way to know how much or little time the SSD will last.

Unix systems use temporary files for lots and lots of needs. If the file system is readonly, those temp-files can't be created, so those tasks don't work.

What can I do now tho? Its not like I can access any of the files and sadly I dont have any recent backups.

---

### Post by TheFu on 2018-04-13
> **nirubu2 said:**
> What can I do now tho? Its not like I can access any of the files and sadly I dont have any recent backups.

Can you not boot from a flash drive and make a backup of the SSD files to another disk; say either a network disk or even an external USB disk that has been formatted to support Unix permissions? It is important to maintain permissions like ownership, groups and all the permissions and ACLs if you have them.  A copy of the data alone is only 50% of a backup IMHO.

For many disk-related things, booting from a flash drive and using the "Try Ubuntu" choice is how we can see what is happening, what happened yesterday and perform data recovery stuff.  I'm partial to using lubuntu for stuff like this, but any flavor should work for most common systems these days.

---

### Post by nirubu2 on 2018-04-13
> **TheFu said:**
> Can you not boot from a flash drive and make a backup of the SSD files to another disk; say either a network disk or even an external USB disk that has been formatted to support Unix permissions? It is important to maintain permissions like ownership, groups and all the permissions and ACLs if you have them.  A copy of the data alone is only 50% of a backup IMHO.

For many disk-related things, booting from a flash drive and using the "Try Ubuntu" choice is how we can see what is happening, what happened yesterday and perform data recovery stuff.  I'm partial to using lubuntu for stuff like this, but any flavor should work for most common systems these days.

Wouldnt I need to be able to boot at all for that? I cant even shut down.

---

### Post by TheFu on 2018-04-13
> **nirubu2 said:**
> Wouldnt I need to be able to boot at all for that? I cant even shut down.

Even if you hold the power button for 20 seconds?

---

### Post by odunayo on 2018-04-13
Couldn't the system forcefully shutdown if the battery is removed? Since there is no other means possible to shutdown...

---

### Post by wildmanne39 on 2018-04-13
> **odunayo said:**
> Couldn't the system forcefully shutdown if the battery is removed? Since there is no other means possible to shutdown...

Only if he wants to risk crashing his hard drive and corrupting files of course there may be a time when there is no other choice but it is very rare.

How to restart your computer if it freezes

That is - hold down Alt+PrintScreen, and then press R-E-I-S-U-B slowly, one after the other. On some keyboards/systems, you need to use the AltGr key. 

REISUO will do a shutdown rather than a restart but not always.

[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)

That works most of the time in an emergency situation.

---

### Post by odunayo on 2018-04-13
> **wildmanne39 said:**
> Only if he wants to risk crashing his hard drive and corrupting files of course there may be a time when there is no other choice but it is very rare.

How to restart your computer if it freezes

That is - hold down Alt+PrintScreen, and then press R-E-I-S-U-B slowly, one after the other. On some keyboards/systems, you need to use the AltGr key. 

REISUO will do a shutdown rather than a restart but not always.

[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)

That works most of the time in an emergency situation.

I thought as much initially, I knew it could post a major risk, but since there is no other available means...but thanks for your suggestion.

---

### Post by TheFu on 2018-04-13
Journaling file systems should be able to handle that. If the OS is truly locked up already, then the damage has already happened, if any.

---

