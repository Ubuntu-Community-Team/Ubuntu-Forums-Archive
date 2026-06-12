---
title: "Hibernate shortcut"
date: 2005-10-28
forum: General Help
---

### Post by jakev383 on 2005-10-28
I have mapped a keyboard shortcut to hibernate my laptop.  Right now, the mapping is 'gksudo /etc/acpi/hibernate.sh'
What I would like to know is how to enable this to run without having to type the root password?  Like it does when selected from the LogOff menu.
Thanks in advance!

---

### Post by jakev383 on 2005-11-02
-bump-
Anyone?

---

### Post by calt129 on 2005-11-06
How about editing e.g. /etc/acpi/events/powerbtn.sh and changing the script the event refers to? In my case, I press the power button and my lappie hibernates.

---

