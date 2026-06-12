---
title: "Fix broken packages"
date: 2006-10-17
forum: General Help
---

### Post by Alex99 on 2006-10-17
Hi,
I'm trying to install a new version of OpenOffice (2.0.4). For this I'm using an automated script.
However, when at some point I have to remove openoffice.org-core and the related packages, there's a problem. Synaptic gives me the message:

Could not apply changes!
Fix broken packages first.

Edit>Fix Broken Passages doesn't do anything, also the filter for broken packages doesn't show what packages aren't right.

When trying to reinstall the old -core package, the message is:
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.

I also tried the following commands in the terminal, but it didn't help:

sudo aptitude upgrade
sudo aptitude update
sudo apt-get install --fix-missing
sudo apt-get install -f
sudo dpkg --configure -a

Any suggestions?

---

### Post by Alex99 on 2006-10-17
Any ideas...?

---

### Post by RAMDrive on 2006-10-18
Same problem here...

---

### Post by aktiwers on 2006-10-18
I know its long.. but read this topic I created some time ago.. there are really a lot of good suggestions and programs that might fix your problem.

[http://www.ubuntuforums.org/showthread.php?t=252762](http://www.ubuntuforums.org/showthread.php?t=252762)

---

### Post by Alex99 on 2006-10-18
Thank you for your replies - the problem is solved. I used the command 

sudo aptitude remove -f  openoffice.org-core

and tried various options I was offered. The only remaining question is, why is checkinstall held back from upgrade?

---

