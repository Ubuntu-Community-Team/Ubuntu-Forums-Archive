---
title: "Recommend a method of converting Fedora to Ubuntu?"
date: 2007-01-31
forum: General Help
---

### Post by Peepsalot on 2007-01-31
Hi everyone.  I have a laptop with Fedora Core 5 on it, and I would like to switch over to Ubuntu.  Normally this would not be a big deal, but it is my work laptop, and I can't afford any down time.  

I would like to:
1) Backup everything I have currently on the laptop, in case anything goes wrong
2) Install Ubuntu on the same hard drive as Fedora Core (will involve splitting existing partition)
3) Be able to dual boot between both distros, while I get Ubuntu configured just right, in my spare time outside of work.
4) Eventually remove FC5 when I am sure Ubuntu is configured properly.

So I guess my questions are:
What backup method would you recommended?
I have never split an existing partition before, how is this done?
I have set up dual boot between windows and linux, but never between two linux distros.  Is it much different?  Anything special I will need to do for this scenario?
Any other suggestions/tips?

---

### Post by dcstar on 2007-01-31
> **Peepsalot said:**
> Hi everyone.  I have a laptop with Fedora Core 5 on it, and I would like to switch over to Ubuntu.  Normally this would not be a big deal, but it is my work laptop, and I can't afford any down time.  

I would like to:
1) Backup everything I have currently on the laptop, in case anything goes wrong
2) Install Ubuntu on the same hard drive as Fedora Core (will involve splitting existing partition)
3) Be able to dual boot between both distros, while I get Ubuntu configured just right, in my spare time outside of work.
4) Eventually remove FC5 when I am sure Ubuntu is configured properly.

So I guess my questions are:
What backup method would you recommended?
I have never split an existing partition before, how is this done?
I have set up dual boot between windows and linux, but never between two linux distros.  Is it much different?  Anything special I will need to do for this scenario?
Any other suggestions/tips?

[LIST=1]
[*]Use **partimage** to back up each current partition
[*]Use **gparted** (on the Live CD) to shrink your existing Linux partition
[*]Just install Ubuntu in the new space, it will take care of the multi-boot stuff
[*]As long as all the OS's are seperate, you can copy config files from one without affecting the other.
[/LIST]

---

### Post by Peepsalot on 2007-02-02
Thanks dcstar.  Do you know if partimage can be used to backup to DVD spanning multiple discs?

---

### Post by Peepsalot on 2007-02-02
Nevermind, I will just try to backup to another hard drive over samba.  But now I have tried this and ran into another problem.  I realized I am using LVM, and I don't think partimage can handle logical volumes.

---

