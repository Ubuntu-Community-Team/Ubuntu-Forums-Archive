---
title: "Back up question"
date: 2007-09-30
forum: General Help
---

### Post by benhagerty on 2007-09-30
Ok, I need to reinstall ubuntu but I don't want to loose all my documents, is there a way I can back them up and when I do a fresh install access them? Would I have to make a partition? If so how :)

---

### Post by Happy_Man on 2007-09-30
See the link about creating a separate /home partition in my sig. That way, all your files and settings are externally stored, in case you want to reinstall again. 

Just make sure that when you install again, you: 

a) tell the installer to mount it as /home <-- very important

b) DON'T FORMAT IT. That's bad.

---

### Post by vanadium on 2007-09-30
Alternatively, all your personal documents live under /home/$USER where $USER is your username. Copy the relevant files to an external backup medium and you are all set. To copy all your settings along, you also need to copy the hidden folders under your /home. However, because you need t reinstall, it might not be a good idea to copy these along because you are not sure some of these are causing the trouble you have.

---

