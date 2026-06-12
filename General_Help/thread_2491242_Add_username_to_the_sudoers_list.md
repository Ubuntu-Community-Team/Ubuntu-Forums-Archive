---
title: "Add username to the sudoers list"
date: 2023-10-01
forum: General Help
---

### Post by enry78 on 2023-10-01
Hello everybody

I have a big problem with my new installation of Ubuntu Server LTS:
I don't know the root password (it was not provided during the installation) and at the same time I cannot add the username to the sudoers list..
I have read already something about it, but at least people coud solve this problem as superuser (su - or sudo -i or..).
Could somebody help me out? I just would like to update my system (sudo apt-get install update..) but apparently the thing is not working as I would..
Any help would be much appreciated. Thanks in advance.

Enrico

---

### Post by MAFoElffen on 2023-10-01
Welcome to Ubuntu Forums and the adventure of Linux.

The user you created during the installation is user UUID 1000, Group GUID 1000. That is the first Administrator type account. That user is already in the Sudoers group, by default. Ubuntu does not set a password to the root user, instead an admin account uses sudo to elevate permissions, to create other users and to manage the system. So for now, you have nothing to do to do that. It is done by default already.

If you were to create another account, and say you wanted that additional account to also be an Admin account, then using elevated permission, you would use sudo to make that user a member of the sudoers group.

The man pages your should probably get familiar with for commands to start out with are
```

sudo
apt 
adduser
moduser
mkdir
pwd

```
This is a good book to read online to learn Linux Commands: [https://www.linuxcommand.org/tlcl.php](https://www.linuxcommand.org/tlcl.php)

What is your goal with Ubuntu Server?

---

