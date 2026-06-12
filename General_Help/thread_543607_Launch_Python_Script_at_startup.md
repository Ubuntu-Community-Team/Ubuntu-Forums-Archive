---
title: "Launch Python Script at startup"
date: 2007-09-05
forum: General Help
---

### Post by kklingerman on 2007-09-05
Hi,

  I have obtained a python script to notify me when I receive new email in Evolution.  How do I get this script to start everytime I login?  

Based upon a google search, I created a file called".bash-login" and placed "/home/me/my.py" in the file.  This did not seem to work.  

Any ideas?

---

### Post by testube_babies on 2007-09-05
You could add "/home/me/my.py" to your startup programs (System -> Preferences -> Sessions).

If that doesn't work you might have to run it with "python /home/me/my.py"

---

