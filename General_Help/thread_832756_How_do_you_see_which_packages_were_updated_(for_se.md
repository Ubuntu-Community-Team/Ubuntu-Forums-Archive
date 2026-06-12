---
title: "How do you see which packages were updated (for security) automatically?"
date: 2008-06-18
forum: General Help
---

### Post by jis on 2008-06-18
I can sometimes see that the package manager is working and something is being downloaded, but I can't see which packages.

---

### Post by sdennie on 2008-06-18
Unless you've specifically configured your machine to automatically download and install security updates, it won't do so.  It will periodically update the list of known packages depending on the settings in System->Administration->Software Sources but, it won't download actual packages.

However, to answer the original question, you can always see what packages have been installed on your system by looking at /var/log/dpkg.log.

---

### Post by tech0007 on 2008-06-18
Or System->Administration->System Log. click on dpkg.log.

---

### Post by jis on 2008-06-18
That is not available in the System menu of Xubuntu (8.04).

---

### Post by cariboo on 2008-06-18
If you go to File-->Open you can open dpkg.log

Jim

---

### Post by jis on 2008-06-18
Yes, in e.g. Mousepad.

---

