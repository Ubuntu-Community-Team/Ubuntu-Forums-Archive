---
title: "Wupi wont start"
date: 2007-06-01
forum: General Help
---

### Post by jorgga on 2007-06-01
When i am trying to start wupi i get some errors and one of them is:

"The program 'apt-get' is currently not installed. You can install it by typing: apt-get install apt"
when i type that: apt-get install apt i get msg from Bash
"Bash: apt-get: command not found" and then again:  "The program 'apt-get' is currently not installed. You can install it by typing: apt-get install apt"

what should i do?

](*,)](*,)](*,)](*,)

---

### Post by ago on 2007-06-01
Did you hard-reboot your system by any chance?

---

### Post by jorgga on 2007-06-01
Yup but it wont help

---

### Post by ago on 2007-06-01
What I mean is that by hard-rebooting you might have corrupted the wubi filesystem, which would explain the error above. Wubi is more "sensitive" to hard reboots than a standard installation and in the case of a hard reboot recovery is not always possible.

---

### Post by bitrocker on 2009-05-07
Hi,

I did the samem stupid thing (hard reboot) on wupi. So what can I try to recover my installation?

---

