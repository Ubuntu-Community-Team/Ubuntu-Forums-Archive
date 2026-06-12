---
title: "This things can't be authenticated, what should I do?"
date: 2007-05-03
forum: General Help
---

### Post by misfito on 2007-05-03
I tried to update my system thru the update notification and it says:

> Warning
you are about to install software taht can't de authenticated! Doing this could allow malicious individual to manage or take control of your system.

aMSN
tile
tcl8.5
tk8.5
pmount

What should I do...trust them??

What are they for...I know aMSN but not the others....

---

### Post by meman63 on 2007-05-03
Simple.Means that you have enabled some repos in /etc/apt/sources.list that are officially recognized by Ubuntu...ie:Third party applications that are out of control of the Ubuntu developers.

Take your chances if you dare.  ;-o

Chances are you will be OK,but you need to do checksum to make sure it is a package that has been signed by it's originator.

Regards,
           Monica

---

### Post by misfito on 2007-05-04
> **meman63 said:**
> Simple.Means that you have enabled some repos in /etc/apt/sources.list that are officially recognized by Ubuntu...ie:Third party applications that are out of control of the Ubuntu developers.

Take your chances if you dare.  ;-o

Chances are you will be OK,but you need to do checksum to make sure it is a package that has been signed by it's originator.

Regards,
           Monica

How do i do a checksum? sorry for my ignorance.:(

---

