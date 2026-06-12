---
title: "Default group for new users"
date: 2008-01-24
forum: General Help
---

### Post by swerdna on 2008-01-24
Newbie to Ubuntu. Hi, just installed my first Ubuntu. I notice that files I create belong to user james and group james. Is that right? And when I look into System --> Admin --> users & groups, I see that james's main group is "james". Have I done something wrong here; I would normally expect the group for james to be users??

Thanks 
Swerdna

---

### Post by p_quarles on 2008-01-24
No, you haven't done anything wrong. Every user automatically has its own group, and is automatically part of it. If you want a group for all users, you would need to add that manually.

---

### Post by swerdna on 2008-01-24
> **p_quarles said:**
> No, you haven't done anything wrong. Every user automatically has its own group, and is automatically part of it. If you want a group for all users, you would need to add that manually.
Ahh... Hmmm.. Thanks. I'm not used to that coming from Suse. But I can see that it has some additional inter-user security when compared to all users primarily belonging to one group. Oh well, pressing on with the voyage of discovery.....

Swerdna

---

### Post by p_quarles on 2008-01-24
SUSE is aimed at the enterprise market, so having folder sharing set up by default makes sense. Ubuntu does automatically add all human users to some groups, though: dialout, cdrom, floppy, audio, and so forth. The groups that users need for basic functionality.

---

