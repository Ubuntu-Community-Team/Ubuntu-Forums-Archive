---
title: "[SOLVED] Desktop folder changed"
date: 2008-05-25
forum: General Help
---

### Post by eddVRS on 2008-05-25
Hi, I hope someone can help me, please.

My desktop folder has gone, and all it's contents moved up to my Home folder, which is now displaying as my desktop.  :confused:

how can I go about restoring the 'desktop status' back to my actual ~/Desktop folder and not my ~/ folder

Any ideas, help or suggestions would be massively appreciated. If you need anymore information from me, just ask :D 

thanks!!!

---

### Post by nick_h on 2008-05-26
Run:
```
gconf-editor
```
Then look under apps->nautilus->preferences->desktop_is_home_dir and chack that it is not set.

---

### Post by eddVRS on 2008-05-27
Thanks for your response. All sorted now.

I wonder what could have caused it... meh :confused:

Thanks again

---

