---
title: "Having trouble mounting sshfs directory into MergerFS"
date: 2019-12-28
forum: General Help
---

### Post by Tadaen_Sylvermane on 2019-12-28
I've been using MergerFs with nfs successfully for awhile now but I'm trying to streamline a bit. Maybe it isn't simplifying like I thought. I'm trying to test using sshfs rather than nfs shares. Less configuration ultimately. I have no problem mounting my remote directories with sshfs via
```
sshfs jason@remote.box:/testing /testing
```
However when I try to add this to my MergerFs pool I'm not entirely sure what happens. The space doesn't show up on a df check and when I look at the directory in the / directory with ls -l the directory has a bunch of question marks in front of it. That is where I'm stuck. I've been messing with the other user option in /etc/fuse.conf but not having any success thus far. I'm not sure how to search to fix this, if it is even possible. If I should just stick with nfs then so be it. I'd rather move to sshfs if I can get this to work. Where do I go from here?

---

### Post by Tadaen_Sylvermane on 2019-12-28
Marking as solved. Following the Arch wiki was better than the other stuff. Worked a treat with allow_other in the options line.

---

