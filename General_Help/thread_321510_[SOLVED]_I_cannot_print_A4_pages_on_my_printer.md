---
title: "[SOLVED] I cannot print A4 pages on my printer"
date: 2006-12-19
forum: General Help
---

### Post by siddartha on 2006-12-19
Hello,

I have set in every menu I found so far A4 paper. Yet, my printer keeps telling me on its display tray 1 letter request. What am I doing wrong.

---

### Post by yopnono on 2006-12-19
> **siddartha said:**
> Hello,

I have set in every menu I found so far A4 paper. Yet, my printer keeps telling me on its display tray 1 letter request. What am I doing wrong.

Open the terminal and edit this file remove all entrys and add A4
```
sudo gedit /etc/papersize
```

---

### Post by fragos on 2006-12-19
Truth is, the default install is A4.  Unless /etc/papersize has already been changed it will be A4.

---

### Post by siddartha on 2007-01-28
Yes, that was it. I have no idea why it was default to letter. I would have never set it like that and I'm the only user with admin rights on this station. I wonder why only OpenOffice could change even this option.

---

