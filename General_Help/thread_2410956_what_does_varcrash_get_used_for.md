---
title: "what does /var/crash get used for?"
date: 2019-01-22
forum: General Help
---

### Post by Skaperen on 2019-01-22
does anyone know what the directory **[SIZE=2][FONT=courier new]/var/crash[/FONT][/SIZE]** gets used for?

---

### Post by Doug S on 2019-01-22
> **Skaperen said:**
> does anyone know what the directory **[SIZE=2][FONT=courier new]/var/crash[/FONT][/SIZE]** gets used for?In the event of a system crash, some kernel and memory dump information will be put there. The information might be useful in a bug report and/or self investigation.

---

### Post by Skaperen on 2019-01-23
i have gotten a number of pop-ups saying that a system error has occurred when my system is booting up or when users are logging in (several in sequence at the console done by a script).  this often happens at the first bootup after an upgrade (i do this about every week or two).  when an upgrade triggers this, it generally does it at every boot until another upgrade a week later.  the message pop-ups are very uninformative so i've looked around for filesystem objects being updated at boot time or user login time.  that looking around has led me to **[FONT=courier new]/var/crash[/FONT]**, but the files in there are uninformative and/or unreadable.

a few days ago, i was repeatedly getting these pop-ups, again.  but, this time i removed the entire tree, re-created an empty directory, and rebooted.  i have gotten no pop-ups since then and all is working well.

---

