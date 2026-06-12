---
title: "maya 7 ?"
date: 2006-07-11
forum: General Help
---

### Post by mech7 on 2006-07-11
[http://www.ubuntuforums.org/showthread.php?t=66859](http://www.ubuntuforums.org/showthread.php?t=66859)

I read here this tutorial.. but it goes wrong on the very first step..

[QUOTE]~$ apt-get install csh alien
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
chris@acerChris:~$
[QUOTE]

DOes anybody know what else i can try ?

---

### Post by halfvolle melk on 2006-07-11
For apt you need to have root-privileges. So try 'sudo apt-get ...' and it should work. Or, if you have synaptic open, it will produce a similar error.

---

### Post by mech7 on 2006-07-11
ah thanks just figured it out myself :D could have known ](*,)

---

### Post by mech7 on 2006-07-15
And what does this mean?

[QUOTE]chris@chris-laptop:/etc/pam.d$ sudo apt-get install csh alien
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package csh
[QUOTE]

?

---

### Post by testube_babies on 2006-07-15
Do you have extra repositories enabled?

[http://ubuntuguide.org/wiki/Dapper#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Dapper#How_to_add_extra_repositories)

---

