---
title: "dpk --configure -a"
date: 2008-06-11
forum: General Help
---

### Post by zadabe2002 on 2008-06-11
I recently installed 8.04 on my laptop.  Have received a few updates but now I have a problem and I don't think the updates are in effect.  I keep getting the message "you must manually run 'dpkg --configure -a' to correct the problem.  I have tried to run this in terminal but it gives me a message to install 'dhelp'.  When I try to install dhelp , it tells me again that I need to manually run 'dpkg --configure -a'.  How do I do this?  I was just wanting to run Java for some internet programs and I can't until I get the configuration right.  Any help will be greatly appreciated.

---

### Post by DBrocks on 2008-06-11
try

```
sudo apt-get update
```

---

### Post by wolfen69 on 2008-06-11
*sudo* dpkg --configure -a

---

