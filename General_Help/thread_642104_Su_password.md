---
title: "Su password?"
date: 2007-12-16
forum: General Help
---

### Post by kenan6346 on 2007-12-16
I know what my sudo password is, but I don't know what the su password is. I would have assumed it was the same as the sudo password; I've used the OS before and this was the case.

Is there a way I can find the su password, or do I just have to use sudo from now on?

---

### Post by Peter76 on 2007-12-16
Just use sudo if you want to do something as root... If you want a root shell use sudo -s. If you want to become root through su, you first have to set the root password: sudo passwd root. ( But I and probably a lot of people here wouldn't reccomend to do so )

---

### Post by Sef on 2007-12-16
Read [Root/Sudo]("https://help.ubuntu.com/community/RootSudo").

---

### Post by kenan6346 on 2007-12-16
Cheers, I set my root password to be different to my account password, and I'll just use sudo or "sudo -s" to become root.

---

