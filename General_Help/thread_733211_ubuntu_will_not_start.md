---
title: "ubuntu will not start"
date: 2008-03-23
forum: General Help
---

### Post by 1467 on 2008-03-23
OK I started the new up dates and move it to a new workspace and forgot a about it and started to play tremulous and when the update started to install the install bar poped up  and then it frosh so i on plunged it and now when i start up Ubuntu it loads to the first line and stops I let it sit for an hour but still no progress

---

### Post by overdrank on 2008-03-23
> **1467 said:**
> OK I started the new up dates and move it to a new workspace and forgot a about it and started to play tremulous and when the update started to install the install bar poped up  and then it frosh so i on plunged it and now when i start up Ubuntu it loads to the first line and stops I let it sit for an hour but still no progress


HI and if you have access to the command prompt then you may try the command
```
sudo dpkg --configure -a
or
sudo apt-get install -f
```
You can try to boot into recovery mode.

---

### Post by 1467 on 2008-03-23
ok i got 

error 27 command not recognized  

for both and I know I spelled it right

---

### Post by 1467 on 2008-03-23
in recovery mode it says no boot image

---

### Post by 1467 on 2008-03-23
is it possible to get my files off and reinstall with out losing my windows partison

---

### Post by overdrank on 2008-03-23
> **1467 said:**
> is it possible to get my files off and reinstall with out losing my windows partison

You may use the live cd to rescue your data.

---

