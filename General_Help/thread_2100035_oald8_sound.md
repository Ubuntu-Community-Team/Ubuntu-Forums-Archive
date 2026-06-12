---
title: "oald8 sound"
date: 2012-12-31
forum: General Help
---

### Post by irancplusplus on 2012-12-31
Hi
Oxford Advanced Learners' Dictionary 8 (**oald8**) worked well in Kubuntu 12.04. Then I installed Ubuntu 12.10 but **oald8** has no sound in ubuntu12.10, even with **festlex-oald** installed.
What's the problem?

---

### Post by dino99 on 2012-12-31
i does not know that prog, but check the settings first. Maybe the old kubuntu settings disturb/broke the actual installation. (erase or rename the old settings for that app)

look inside .local and/or .gconf, .config, .gnome2 in your /home (ctrl+h to unhide them)

---

### Post by irancplusplus on 2013-01-04
solved.


I ran the command to open oald:
**padsp '/home/[user_name]/oald8//oald8'**

padsp brings back sound.

I also changed the oald icon command to 

**padsp '/home/[user_name]/oald8//oald8'**

so it opens oald8 with sound.

thanks to
[http://ubuntuforums.org/showthread.php?t=2010331](http://ubuntuforums.org/showthread.php?t=2010331)

---

