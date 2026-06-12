---
title: "No boot after new hard driver added"
date: 2007-02-08
forum: General Help
---

### Post by lhabjane on 2007-02-08
I've installed ubuntu on serial ata drive connected at SATA4.
Now I've added a new hard drive at SATA1. It won't boot now! It just freezes at the start of that  progress bar. (my sata1 hard drive is actually the windows hard drive that I disconnected before installing Ubuntu)

---

### Post by taylonr on 2007-02-09
I had a problem where I had disconnected my HDDs to wipe clean some old HDDs.  I busted a cable, replaced it and reconnected my original drives and had the same thing.  

Turns out my Ubuntu would not boot because it was looking for an HDA and HDB, but I only had an HDB.  When I tried connecting both HDDs I couldn't get it to boot because I had a 40pin cable instead of 80.

Anyway, I'd recommend taking off the new HDD, and look at your fstab.  I believe there is a way you can specify the entries there by UID instead of by hda or hdb.  It is quite likely that the new HDD has taken over the name for the old one (hda has become hdb or hdc etc.)

---

