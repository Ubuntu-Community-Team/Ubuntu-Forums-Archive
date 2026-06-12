---
title: "System monitor on ubuntu 14.04 has 3 tabs.  System monitor on 12.04 has 4 tabs."
date: 2015-07-17
forum: General Help
---

### Post by Tom_Carr on 2015-07-17
12.04 has 4 tabs - System, Pocesses, Resources, File Systmes

14.04 monitor, 3.8.2.1 no longer has the System Tab.  

How do I get info on the CPU and memory on the system?

---

### Post by v3.xx on 2015-07-17
I run 3.8.2.1-2 in Mate 14o4 and have 4 tabs.

---

### Post by plucky on 2015-07-17
> **Tom_Carr said:**
> 12.04 has 4 tabs - System, Pocesses, Resources, File Systmes

14.04 monitor, 3.8.2.1 no longer has the System Tab.  

How do I get info on the CPU and memory on the system?

Maybe 

**System Settings > Details**

Good Luck

---

### Post by deadflowr on 2015-07-17
> **v3.xx said:**
> I run 3.8.2.1-2 in Mate 14o4 and have 4 tabs.
Mate is mate and gnome is gnome.
Not the same thing.
> **plucky said:**
> Maybe 

**System Settings > Details**

Good Luck
^^^That.
Gnome dropped the system detail tab like in the very next version of system monitor used after the version used in 12.04.
The details section of system settings is the best place to look for now.
You can get more robust info using the lshw command(using sudo for even more robust info) or installing a package, like hardware lister.

---

### Post by v3.xx on 2015-07-17
> **deadflowr said:**
> Mate is mate and gnome is gnome.
Not the same thing.

Yes it is and why I stated so plus the version.  And I think I will continue to try since linux is linux.

---

### Post by Tom_Carr on 2015-07-18
**System Settings > Details works.  Thanks.**

---

