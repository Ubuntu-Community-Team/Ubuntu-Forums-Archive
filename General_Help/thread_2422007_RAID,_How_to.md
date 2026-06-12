---
title: "RAID, How to?"
date: 2019-06-30
forum: General Help
---

### Post by adambond on 2019-06-30
Im currently running two computers. 
Ubuntu 18.04.2 64bit,
And Ubuntu 12.04 32bit

What I have is a bunch of USB thumb drives mounted on a hub. I want to use them as a RAID, i dont care if its JABOD, or RAID0.  Either way doesnt matter. 

Is there a program I need to download to add the RAID utility?  

Thank you :)

---

### Post by DuckHook on 2019-06-30
Stating what follows in only the kindest way, but this is just a disaster waiting to happen.

[LIST]
[*]USB thumb drives are *very* unreliable for main storage.
[*]Running them off an external hub instead of an internal bus multiplies that unreliability by another order of magnitude.
[*]Layering on something like RAID increases your unreliability by a further order of magnitude.
[/LIST]
You are proposing to build a skyscraper on top of a foundation of cardboard.

And 12.04 reached EoL 2 years ago. Since then there have been hundreds of vulnerabilities and associated patches that 12.04 has not fixed and never will.

---

### Post by adambond on 2019-06-30
I already know all that.
Im simply doing a 1 time transfer.

---

### Post by DuckHook on 2019-07-01
I am not a RAID expert, but [this]("https://www.digitalocean.com/community/tutorials/how-to-create-raid-arrays-with-mdadm-on-ubuntu-18-04") may help.

You could also consider forgoing RAID altogether and just use [LVM]("https://wiki.ubuntu.com/Lvm"). Might be easier, but since we have no idea what the background, context or goal is, you will have to judge which method is superior. You have already implied that robustness is not a concern.

---

### Post by rsteinmetz70112 on 2019-07-01
Your best bet is to get a couple or four cheap Hard Drives (or SSDs) and build a new system with raid using mdadm or LVM, it dosen't make much difference. Then transfer the thumb drives to the new hardware. It will be easier, more reliable and you can reuse the thumb drives.

---

