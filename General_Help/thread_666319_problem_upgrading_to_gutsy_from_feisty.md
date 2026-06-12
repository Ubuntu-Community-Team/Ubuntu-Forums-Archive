---
title: "problem upgrading to gutsy from feisty"
date: 2008-01-13
forum: General Help
---

### Post by amacheurworks on 2008-01-13
I was upgrading from Feisty to Gutsy using the upgrade manager, and during the 'Modifying the Software Channels' bit I got the following error:

Could not calculate the upgrade

An unresolvable problem occurred while calculating the upgrade.

Please report this bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bug report.

The last part of my apt.log file is:

Installing libc6-i686 as dep of ubuntu-minimal
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Starting
Starting 2
Investigating libc6-i686
Package libc6-i686 has broken dep on libc6
  Considering libc6 10930 as a solution to libc6-i686 7
  Holding Back libc6-i686 rather than change libc6
Investigating ubuntu-minimal
Package ubuntu-minimal has broken dep on libc6-i686
  Considering libc6-i686 7 as a solution to ubuntu-minimal 10003
    Reinst Failed early because of libc6
  Considering libc6-i686 7 as a solution to ubuntu-minimal 10003
  Considering libc6-i686 7 as a solution to ubuntu-minimal 10003
Done

My thinking:
I have libc6 installed, but not libc6-686, but uninstalling one for the other means a bunch of my programs will be uninstalled, which is quite a hassle, and I would like to avoid.

Any suggestions?

---

### Post by zvacet on 2008-01-13
```
sudo apt-get install libc6-i686
```

```
sudo apt-get update
```

Try to upgrade again.

---

### Post by N_nykrog on 2008-01-14
I have the exact same problem, with the same apt.log ending(except mine is "Considering  libc6 11221 as a solution to libc6-i686 7, instead of 10930)


When trying to run the first code, I am told that:
The following packages have unmet dependencies:
_ libc6-i686: pre-dependencies: libc6 (= 2.5-0ubuntu14) but 2.7-5 is expected to be installed_
E: Damaged packages

Tragically, I'm using a danish version of Ubuntu, so my output is written to me in danish. I've found the name for the error, but the lined-under text might not be the exact same as normal...

I've tried to run apt-get -f install, as it seemed to be the solution so similar problems, but it did not work.

Any ideas? I would really like to get going with Gutsy

---

### Post by wolfen69 on 2008-01-14
if you are not afraid to do so, a fresh install of gutsy would be best. otherwise, good luck.

---

