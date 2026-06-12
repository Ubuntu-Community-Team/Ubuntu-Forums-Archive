---
title: "Selling a laptop, need to remove myself as administrator."
date: 2016-09-18
forum: General Help
---

### Post by coldraven on 2016-09-18
As the title says I'm selling a laptop to someone called John. I added John as a new user and gave him admin rights. Logged in as John I cannot delete myself. Is this possible or should I do a fresh install? There is no personal data on the laptop to worry about any security issues.

---

### Post by sudodus on 2016-09-18
I would prefer to create a fresh installation.

But it should work to remove a user with ***users-admin***. Install the package **gnome-system-tools** to get it :-)

---

### Post by coldraven on 2016-09-18
> **sudodus said:**
> I would prefer to create a fresh installation.

But it should work to remove a user with ***users-admin***. Install the package **gnome-system-tools** to get it :-)
Thanks, I'll go for a fresh install. I don't want any hiccups or requests for support.

---

### Post by Bucky Ball on 2016-09-18
I'd go the fresh install, certainly. 

@sudodus: Just wondering, though; if you remove an admin user while in root, are you left with the user root only until root adds another admin user (i.e. John)?

---

### Post by sudodus on 2016-09-18
> **Bucky Ball said:**
> I'd go the fresh install, certainly. 

@sudodus: Just wondering, though; if you remove an admin user while in root, are you left with the user root only until root adds another admin user (i.e. John)?

@BB: I have not tested what you ask about, I don't know, and I should not guess here ;-)

---

### Post by mcduck on 2016-09-19
Better yet, make it a fresh OEM install so the new owner can create his own user and everything else... [http://askubuntu.com/questions/36671/how-do-i-pre-install-ubuntu-for-someone-oem-install]("http://askubuntu.com/questions/36671/how-do-i-pre-install-ubuntu-for-someone-oem-install")

---

