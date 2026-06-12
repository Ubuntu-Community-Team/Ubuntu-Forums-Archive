---
title: "Problem With Firefox &amp; Opera"
date: 2007-01-07
forum: General Help
---

### Post by mayankgarg1 on 2007-01-07
Dear Team
I have ubuntu dapper installed on my PC.My Users other than root can not browse the internet in Firefox and Opera.
They have to use sudo command to start firefox and opera.But after that these softwares uses only root's settings like homepage,download storage location , preferenses etc.
I have tried to change the permission of Firefox Binary but it also not helped.
Please help me so that my normal user can also browse internet without using sudo command and save there preferenses and other settings.

---

### Post by ingo on 2007-01-07
Certainly strange behaviour that smacks of a specialised install. This has to be done on purpose and has something to with groups - a normal install would give everyone the right to browse the net.

---

### Post by mayankgarg1 on 2007-01-11
How can I revert the groups and their permissions to default level which were present at the time of installtation of dapper.

---

### Post by ingo on 2007-01-13
to find out which groups you belong to enter
> groups
Do the same for each user incl. root and compare. The obvious one to look out for (if it is missing, that is) is dialout. To add a user to a group simply edit /etc/group.

HTH

---

