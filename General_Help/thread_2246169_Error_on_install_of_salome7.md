---
title: "Error on install of salome7"
date: 2014-09-28
forum: General Help
---

### Post by Shawn_Hawkins on 2014-09-28
I'm trying to install salome7 and the instructions are; in terminal go to directory and type in 
. /runInstall 
I do this and I get "permission denied" I do the same thing but with sudo;   
sudo . /runInstall 
And I get the same error. I don't understand.

---

### Post by Iowan on 2014-10-07
Verify that runInstall is executable. Often, programs download without the X bit set - a security feature.

---

