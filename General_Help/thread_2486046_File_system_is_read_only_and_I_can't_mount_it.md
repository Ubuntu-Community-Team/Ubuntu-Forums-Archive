---
title: "File system is read only and I can't mount it"
date: 2023-04-18
forum: General Help
---

### Post by saeedmabrouk211 on 2023-04-18
File system is read only and I can't mount it by normal booting or recovery mode . It enters emergency mode and don't start

---

### Post by TheFu on 2023-04-18
What do the system logs show?  You'll need to boot either into Recovery mode (use the Grub Advanced choice at boot) or you can boot into a "Try Ubuntu" environment from any Ubuntu Flavor and look around that way.

All sorts of problems can happen. Without some logs, it would be too hard to start guessing all the possible problems and you'd probably miss something subtle or fail to check THE ONE that mattered out of the 150+ possible issues.

---

### Post by yancek on 2023-04-19
Since you are posting at an Ubuntu forum, does that mean you have some version of Ubuntu installed and are using a Linux filesystem on which you have the problem?  If so, what filesystem?  Is this a new install or has it been working and you just recently received this error?  If that is the case, have you made any recent changes to software/hardware?  If you can access the logs (generally under /var/logs) as suggested above that would be a good starting point.

---

