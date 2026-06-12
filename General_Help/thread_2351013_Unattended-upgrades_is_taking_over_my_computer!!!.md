---
title: "Unattended-upgrades is taking over my computer!!!"
date: 2017-01-30
forum: General Help
---

### Post by jsc12345 on 2017-01-30
A few days ago I set up the unattended-upgrades package to update Google Chrome, and ever since then I've been getting error messages whenever I try to remove and install packages. For example, here's what I get when trying to update package lists: 
E: Syntax error /etc/apt/apt.conf.d/50unattended-upgrades:9: Malformed tag
Due to the unattended-upgrades part I'm pretty sure it has to do with that package. Could someone point me in the right direction?

---

### Post by mastablasta on 2017-01-30
what is your question? accordign to error there is a Malformed tag in file /etc/apt/apt.conf.d/50unattended-upgrades

it also says: 
E: Syntax error

translation so you wrote something in the wrong way in one line. open the config file and check it through. see what you wrote wrong.

---

### Post by jsc12345 on 2017-01-30
Okay, thanks. I'll check

---

### Post by deadflowr on 2017-01-30
Did you actually solve this?
If yes, what was the fix.
If no, post the malformed file, or at least what you edited in the file.
Also, you can do a check of unattended-upgrades
I usually run it with
```
sudo unattended-upgrades --dry-run -v
```
the dry-run simulates the actual execution, the -v makes it output the results.

---

### Post by jsc12345 on 2017-02-02
It did, thanks

---

### Post by carusoswi on 2017-02-05
and the fix???

---

