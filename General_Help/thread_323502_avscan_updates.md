---
title: "avscan updates??"
date: 2006-12-22
forum: General Help
---

### Post by Radiolad on 2006-12-22
Hi, I've asked this question on the PPC area to no avail so maybe someone can advise here.

I'm running AVSCAN on my iMac G3 PPC using DAPPER.
As far as I can see it is the 'latest' version.
My question is: How is the proceedure for updates instigated?
I'm running Grisoft AVG on my x86 'Windows' PC and the updates are usually everyday on an automatic basis. (is there a PPC version of Grisoft for Dapper ... I can't find one )

Do I need to do a manual check every few days ...or is LINUX/DAPPER safe from those pesky virus writers?  :evil: :evil: 
I'm also running FIRESTARTER and that is kept VERY busy from the moment I turn it on (a lot of potential intruders come a-knockin' on my door )

Cheers, Radiolad :)

---

### Post by rowanparker on 2006-12-23
You shouldn't need an Anti-Virus on Linux.

---

### Post by logos34 on 2006-12-23
AVG for Linux has to be updated periodically.  

You have to be root to fetch updates.

$ sudo avggui

Click Update.

To automate scans and updates:
AVG menu>Service>Program settings>scheduler>test sheduler or update scheduler.

I have mine set to update at reboot and do a scan daily.

I also run Firestarter (actually its just a frontend to configure iptables--which is allegedly the most secure firewall because it doesn't leave any ports open by default)
 
my 2 cents: I think it's a good idea to run av because even if linux isn't vulnerable we can still act as unwitting transmitters of viruses; and the more people who run av, the better early warning and tracking we have of new threats.

---

### Post by Radiolad on 2006-12-23
Hi, Many thanks for you help and advice.
I like to think I've got a 'bolt on the door' just incase ;)   Do I enter from a 'terminal'? (newbie!)
for ROOT ? :-k 
Cheers.  Radiolad.

---

### Post by logos34 on 2006-12-23
wait, I misunderstood--you're using the GTK frontend to ClamAV!  You mentioned using Grisoft AVG windows edition so I thought 'AVSCAN' was a typo and you really meant you were running 'AVGSCAN' (the AVG for Linux command to run a scan).  

There's no deb package for AVG, only an rpm.  You have to convert it using alien.  I'm running 32-bit edgy on i686 architecture, don't know if this would work on PPC mac.  

But ClamAV is just as good, use that.  I used it before switching to AVG.  You just can't automate scans and updates--at least not in clam.  I think you can use something like KCron or some other task scheduler for that.

---

### Post by logos34 on 2006-12-23
this might interest you:

[http://ubuntuforums.org/showthread.php?t=136064](http://ubuntuforums.org/showthread.php?t=136064)

can't see why it woudn't work on your Dapper ppc

---

