---
title: "group change without reboot"
date: 2007-11-06
forum: General Help
---

### Post by arzafen on 2007-11-06
Hi, 
I have a problem with the activation of the group changes. To be more clear, let's say I added one user to a group called dummy and to test I gave read permission to a folder for this group. (or I change the group ownership of this folder to dummy and give read access for this group) if this user tries to access this folder, it gives permission denied error. Apparently, this group change is not activated. If I reboot the machine,then this user is able to access this folder. The problem is I am working on a server for which it is not feasible to reboot at each single group change. 
Is it possible to update the group information without rebooting the machine?
Thanks in advance

---

### Post by arzafen on 2007-11-07
any idea?

---

### Post by taurus on 2007-11-07
Just tell that user to log out and back in again so the new group is included in the GID--group ID.

---

