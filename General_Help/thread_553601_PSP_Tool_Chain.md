---
title: "PSP Tool Chain"
date: 2007-09-18
forum: General Help
---

### Post by Newuser1111 on 2007-09-18
When I try to run toolchain.sh it gives this error:

ls: /usr/lib/libncurses.*: No such file or directory
ERROR: Install ncurses before continuing.
../depends/check-ncurses.sh: Failed.

This is PSP Tool Chain:
[http://ps2dev.org/psp/Tools/Toolchain/psptoolchain-20070626.tar.bz2]("http://ps2dev.org/psp/Tools/Toolchain/psptoolchain-20070626.tar.bz2")

I'm sorry if this is the wrong place to put this.

---

### Post by Maestro23 on 2007-09-18
> **Newuser1111 said:**
> When I try to run toolchain.sh it gives this error:

ls: /usr/lib/libncurses.*: No such file or directory
ERROR: Install ncurses before continuing.
../depends/check-ncurses.sh: Failed.

This is PSP Tool Chain:
[http://ps2dev.org/psp/Tools/Toolchain/psptoolchain-20070626.tar.bz2]("http://ps2dev.org/psp/Tools/Toolchain/psptoolchain-20070626.tar.bz2")

I'm sorry if this is the wrong place to put this.

First you need to install build-essential.

> 
sudo apt-get update
sudo apt-get install build-essential

Then you need to make sure you have the software installed that it asked for.  You can check using Synpatic (GUI).  Open it up and search for each one.  If it's not installed, then you must install it.

After you have all the req's, then proceed with the instructions.

---

### Post by Newuser1111 on 2007-09-18
Now this is what sudo apt-get install build-essential did:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.

---

### Post by Newuser1111 on 2007-09-18
Now I have ncuses but now what do I do here:

ERROR: Set $PSPDEV before continuing.
../depends/check-pspdev.sh: Failed.

---

### Post by Newuser1111 on 2007-09-18
Help?

---

### Post by Newuser1111 on 2007-09-18
I'm really sorry for posting again but now the error is:

ERROR: Add /usr/local/pspdev/bin to your path before continuing.
../depends/check-pspdev.sh: Failed.

---

