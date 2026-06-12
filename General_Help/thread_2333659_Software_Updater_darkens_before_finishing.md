---
title: "Software Updater darkens before finishing"
date: 2016-08-11
forum: General Help
---

### Post by linux26 on 2016-08-11
Tried upgrade from 14.04 to 16.04 with software updater. Install did not complete. Desk top shows I'm 14.04 yet I get Sorry,Ubuntu 16.04 has experienced an internal error when re-booting. Now when I try the Software Updater it goes through the motions but then stops and darkens before anything happens. Feel I have 14.04 and partial 16.04 packages so I am getting issues.

---

### Post by grahammechanical on 2016-08-11
When an application window darkens it is because the application is busy. In this case Software Updater may be busy because of some conflict with the software repositories. Open a terminal and run

```
sudo apt-get update
sudo apt-get upgrade
```

and post the output in this thread enclosed with quote tags.

Regards.

---

### Post by linux26 on 2016-08-11
Software Updater still goes dark before finishing updates.

---

### Post by ajgreeny on 2016-08-12
So please tell us; what was the solution?

The forum's main reason for existence is to help all users solve problems.  A post simply stating "Solved" is not helpful for others who may be searching for answers to the same problem.

---

