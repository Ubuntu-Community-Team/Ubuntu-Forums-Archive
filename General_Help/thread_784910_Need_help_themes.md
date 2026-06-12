---
title: "Need help themes"
date: 2008-05-06
forum: General Help
---

### Post by retro89 on 2008-05-06
Im trying to extract a file to usr/share/themes but it says access denied. How do I fix this?

---

### Post by nhandler on 2008-05-07
You need to use "sudo" in order to do that. Sudo temporarily gives you root privileges, and provides you with complete control over the entire filesystem. You can read more about sudo here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by IHATEDLINK on 2008-05-07
type in terminal

sudo nautilus ( If you are using KDE i think is konqueror) 

Type your password and then click & drag from the file to the directory.

---

### Post by nhandler on 2008-05-18
> **IHATEDLINK said:**
> type in terminal

sudo nautilus ( If you are using KDE i think is konqueror) 

Type your password and then click & drag from the file to the directory.

You should not use sudo for graphical applications (such as nautilus). Read this: [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo) for an explanation. You should use 'gksudo nautilus' instead.

---

