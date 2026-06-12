---
title: "rdesktop segmentation fault"
date: 2007-04-20
forum: General Help
---

### Post by dbouwer on 2007-04-20
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/rdesktop/+bug/107970](https://bugs.launchpad.net/ubuntu/+source/rdesktop/+bug/107970) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I am getting the Segmentation fault (core dumped) for rdesktop since I updated with update-manager this morning. (20April2007)

Anybody else have the same problem? 

Anybody know what was updated?


Opera also have update dependency problems.

---

### Post by Pcniatic on 2007-04-20
I have the same problem, but i did a fresh install.
There is a bug filled on launchpad ([https://bugs.launchpad.net/bugs/104332)](https://bugs.launchpad.net/bugs/104332)), related to this bug.
I solved temporaly installing the package from debian repository:

Deb file: [http://mirror.positive-internet.com/...5.0-2_i386.deb]("http://mirror.positive-internet.com/debian/pool/main/r/rdesktop/rdesktop_1.5.0-2_i386.deb")

Good luck

---

### Post by dbouwer on 2007-04-23
Installing 5.0-2 messes with software update, an complains about libc6 and libssl...I reverted to 1.4 for now, untill a fix is available...

---

