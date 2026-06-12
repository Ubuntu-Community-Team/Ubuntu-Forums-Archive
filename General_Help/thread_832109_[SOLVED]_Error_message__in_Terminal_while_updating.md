---
title: "[SOLVED] Error message  in Terminal while updating"
date: 2008-06-17
forum: General Help
---

### Post by dnaga57 on 2008-06-17
From yesterday I get the following in Terminal when I try the command

dnubuntu@dnubuntu-laptop:~$ sudo install updates
install: missing destination file operand after `updates'
Try `install --help' for more information.
dnubuntu@dnubuntu-laptop:~$ sudo update
sudo: update: command not found
dnubuntu@dnubuntu-laptop:~$ sudo install update
install: missing destination file operand after `update'
Try `install --help' for more information.
dnubuntu@dnubuntu-laptop:~$ 

Earlier I used to get updates by this method.
Where have I gone wrong?
Pls advise
:confused:

---

### Post by avtolle on 2008-06-17
Try```
sudo aptitude update && sudo aptitude safe-upgrade
``` from the terminal, and, if it doesn't work, post any error messages you get.

---

### Post by manfer on 2008-06-17
The command install is not for updating the system.

To make an update from console you use:

**prompt:~$** sudo apt-get update

to update the package index.

**prompt:~$** sudo apt-get upgrade

to upgrade the packages that have newer versions.

---

### Post by dnaga57 on 2008-06-17
Thanks. Realised the stupid error
:)

---

