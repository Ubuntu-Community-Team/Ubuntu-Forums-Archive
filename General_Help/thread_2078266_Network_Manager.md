---
title: "Network Manager"
date: 2012-10-30
forum: General Help
---

### Post by Leo Matheus on 2012-10-30
Hi all, Some one know what is the directories/files/libs that the NEtwork Manager use? I need it to change some permissions.

---

### Post by Cheesemill on 2012-10-30
You can install [Synaptic]("apt://synaptic") and use it to list all files installed by a particular package (just right-click on a package and select 'Properties').

Can I ask what you are trying to achieve, usually changing permissions on system files is not a good idea and likely to break your system. There is likely to be a better method to achieve what you are trying to do.

---

### Post by Leo Matheus on 2012-11-01
its for a school lab. I have an acc on every machine for the students and on for the admin. So, i need the students use some programs that need the permission, but they cant have the permission to all of the sistem.

ps:sorry to take too much time to ansewer, i wasn't enable to use my pc lest day

---

### Post by Cheesemill on 2012-11-01
The recommended method to give this sort of access is to give the students a normal non-admin account and then make entries in the sudoers file to only give them sudo rights for certain programs.

[https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)

---

### Post by Leo Matheus on 2012-11-07
yes im doing that, but i need the directories and files  that the Network Manager use.

---

