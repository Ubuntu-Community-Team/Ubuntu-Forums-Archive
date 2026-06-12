---
title: "Had a few crashes, loss data, xfs?"
date: 2007-05-21
forum: General Help
---

### Post by hanzomon4 on 2007-05-21
Alright I recently had a string of bad luck in regards to system lockup that caused me to do a few cold reboots. I noticed that some settings in my /home/(Like firefox settings) vanished. Things like firefox-theme, history, were just not working. After this happened a 2nd time I feared a **[color=red][size=4]([/size](([/color][b]v[color=orange]*[size=2]![/size]*[/color]rus**[color=red]))[size=4])[/size][/color][/b]. But after I picked my face up off the floor I thought about the possibility that my xfs/home could be the culprit. I know that xfs does something different that makes cold reboots bad. Something about corrupting the journal? 

I'd really appreciate it if someone could confirm my suspicions about my xfs/home being the monster in the closet. Also how would I go about switching back to ext3? Copy data to a backup hard drive format the xfs as ext3 and move files back?

---

### Post by vtel57 on 2007-05-21
Virus? HAHA! Slim chance. ;)

Cold shutdowns are baaaaa-aaad ju-ju for all Linux systems. Data loss is common. The journaling file system is supposed to save you should this ever occur. It's up to you, of course, but ext3 would be my choice.

Luck!

---

