---
title: "Using GParted to remove ntfs partition"
date: 2008-04-08
forum: General Help
---

### Post by Mlehliw on 2008-04-08
My computer at work has two partitions one large one for XP and a smaller one for Linux. I never use XP so I want to nuke that partition and give it to Linux. Can GParted do this, is it safe? I imagine I might need to manually edit grub or something if I do this, but I don't think that should be too tricky.

I would use partition magic but we don't have it at work. Our IT guy suggested I ghost the Linux partition and clean the harddrive and install the image. I guess that would work but I would have to kill an hour or so at work just to do this. Any suggestions?

---

### Post by neurostu on 2008-04-08
Yes you can manage a NTFS parition from GParted.  Just boot into the GParted Live cd. Delete the ntfs partition, then resize your ext3 partition.  Last week I resized my windows partitions and moved my linux partition with GParted and had no problems at all.

However if you have mission critical data you should BACK IT UP

WARNING: This may take a long time (several hours)  DO NOT interupt it.  Many people have interupted GParted only to find the interrupting it completely destroys the partition tables and requires a reformat to fix.

---

