---
title: "The permission could not be determined?"
date: 2008-06-04
forum: General Help
---

### Post by heatblazer on 2008-06-04
From the day I upgraded 7.10 to 8.04, I keep obtaining this message when I open the "Permissions" tab on the hard drives. Do you have the similar porblem? Here is the shot:

---

### Post by sdennie on 2008-06-04
To me that sounds like you don't have permissions to read the permissions of /dev/sdb1 (confusing, I know).  If you are mounting things with /etc/fstab, the contents of that file may be interesting as well as the output of running "groups" from a terminal.

---

### Post by mctk on 2008-06-22
There's a solution here that's mostly worked for me:

[http://ubuntuforums.org/showthread.php?t=820744&highlight=permissions+determined]("http://ubuntuforums.org/showthread.php?t=820744&highlight=permissions+determined")

---

