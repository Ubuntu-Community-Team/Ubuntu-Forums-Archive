---
title: "Messed up sudoers files"
date: 2008-06-17
forum: General Help
---

### Post by dleroy on 2008-06-17
I messed up my sudoers file trying to get my user to work as root.  Now all sudo commands error after the PW entry  telling me I am not in the now have no "sudo" permissions.  How do I fix the sudoers file since I can't do any root function at all ??

:confused::confused:

---

### Post by bodhi.zazen on 2008-06-17
First, always edit sudoers with 

```
sudo visudo
```visudo prevents these kinds of issues, lol

Second, boot to recovery mode and fix it. Easiest way is to restore from back up (smart fellow like you *always backs up*).

---

### Post by iaculallad on 2008-06-17
Maybe, this [link]("http://www.psychocats.net/ubuntu/sudo") could help you fix your messed sudoers file.

---

