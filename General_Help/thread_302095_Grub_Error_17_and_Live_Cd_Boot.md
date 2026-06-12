---
title: "Grub Error 17 and Live Cd Boot"
date: 2006-11-18
forum: General Help
---

### Post by rosieg on 2006-11-18
Hi,

I had a dual partition Edgy and XP. Decide to do clean install (of Dapper)and remove XP partition. Doenloaded ISO file and burnt. Wacked in drive. Went through setp process. Was beginning to format / as ext3 when someone took laptop off basestation (which contains CD drive). After shriek of horror was immediately returned but install would not resume. Turned computer off in order to boot of liveCD and start over. Will no longer boot from LiveCD goes to GRUB 1.5 then hangs with error 17. 

How can I make it boot from the CD?

Heeeeelp

Rosie

Am now trying to use my XP rescue disks which so far it has booted from which is a good sign. I do have all my personal stuff backed up, but I wish there was someway I didn't have to reinstall windows first - is it possible that removing the base station during installation damaged the liveCD?

---

### Post by DaveBorealis on 2006-11-18
> **rosieg said:**
> is it possible that removing the base station during installation damaged the liveCD?

My guess is that grub was installed, and now when you try to boot from the live CD you're actually booting from grub on the MBR and the partially installed-to partition.  Seems like the live CD is being ignored, but Windows rescue CD does boot the system.  If it were me, I'd burn another live CD (slowly) and rule out the possiblility of either a damaged CD or of a coincidentally defected CD that you just happen to have been trying to use when someone took your computer off the base during the install.

Best regards,
Dave

---

### Post by jimbob on 2006-11-18
If you don't really need the live CD I would recommend downloading and burning the alternate CD.

Some folks have reported problems using the live CD to install.
&#65279;________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by rosieg on 2006-11-18
Thanks for your help guys.  I reinstalled xp using my xp rescue cds (worryingly it didn't work!) and after that the system was able to boot from the CD again, and now I have a shiny new system...

---

