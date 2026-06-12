---
title: "FTP Automation"
date: 2007-12-28
forum: General Help
---

### Post by manfarb on 2007-12-28
I'm new to Ubuntu, but have really taken a liking to it.  I'm in the process of replacing the Windows XP box with a Ubuntu box that I use to backup all my Web sites.  On the XP box I've been using SyncBack SE and really like it.  I'm able to schedule it to login to my sites and FTP everything down to a local hard drive.  It's a GUI interface, which I much prefer to command-line.

I have Ubuntu 7.10 installed and working just fine.  I installed gFTP, but that doesn't seem to allow for the scheduling/automation that I need.  Can someone help direct me to the right package?

---

### Post by tehet on 2007-12-28
I don't know about FTP and GUI solutions but you might want to look into rsync + cron (or anacron). That's most commonly used for for automated syncing /back-ups.

---

### Post by manfarb on 2007-12-28
Thanks Tehet.  I see both of those packages are already installed on my 7.10 box.  I'm sure I can find documentation on how to use them.  Sounds like it will be a good solution.

---

### Post by SOULRiDER on 2007-12-28
I was gonna suggest cron and wget instead of cron and rsync.
You should be able to find guide son how to do this without much trouble, but you can also check out the manuals for both programs by typing these commands in a terminal.
```
man wget
man cron
```

---

### Post by manfarb on 2007-12-28
I sure wish there was a GUI interface for rsync or wget.  I found and installed Grsync, but it only accommodates local sources.  Guess I need to decide if I have the time to read and understand all the documentation.  Thanks for your help tehet and SOULDiDER.

---

### Post by tehet on 2007-12-28
> **manfarb said:**
> Guess I need to decide if I have the time to read and understand all the documentation.
Or you could just copy/paste [these commands](http://www.howtoforge.com/mirroring_with_rsync) :)

---

### Post by manfarb on 2007-12-28
Thanks for the link tehet.  I just installed a 200 GB and a 250 GB drive into the Ubuntu box.  I want do software RAID between them, but I'll buy a RAID controller if need be.  Once I have them mirrored I'll be using the array as the target for my backups.

---

### Post by fjgaude on 2007-12-28
> **manfarb said:**
> I sure wish there was a GUI interface for rsync or wget.  I found and installed Grsync, but it only accommodates local sources.  Guess I need to decide if I have the time to read and understand all the documentation.  Thanks for your help tehet and SOULDiDER.

Grsync handles other than local sources... it works on a LAN nicely. At least it does for me, both to and from remote boxes.

Typical destination: stardust:/home/raid/

where stardust is the host at IP 192.169.100.103

---

### Post by manfarb on 2007-12-28
I'll give that a try.  Thanks fjgaude.

---

