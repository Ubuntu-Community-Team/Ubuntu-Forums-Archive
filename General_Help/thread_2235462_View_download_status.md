---
title: "View download status"
date: 2014-07-21
forum: General Help
---

### Post by keith14 on 2014-07-21
Hi, this pc floats ubuntu 13.1 and I requested updates. How do I see the download rate?

---

### Post by keith14 on 2014-07-21
Hi, the update failed. I get message package system is broken. This took about 1 hour to show itself. I tried the help given:
apt-get install -f E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you

---

### Post by slickymaster on 2014-07-21
The solution is to read the error message: **are you root?**. Before running any administrative task like installing, removing, changing system wide preferences, etc. you need to be **root**. This is specially true for apt-get. Use sudo to run a command with root privileges.

From the [community documentation]("https://help.ubuntu.com/community/UsingTheTerminal"):

> **sudo: Executing Commands with Elevated Privileges**
Most of the following commands will need to be prefaced with the sudo command. This elevates privileges to the root-user administrative level temporarily, which is necessary when working with directories or files not owned by your user account. When using sudo you will be prompted for your password. Only users with sudo (administrative) privileges will be able to use this command. You should never use normal sudo to start graphical applications as Root (Please see RootSudo for more information on using sudo correctly.)

---

### Post by grahammechanical on 2014-07-21
We can see the download rate in System Monitor. It will show both receiving and sending in bytes per second.

You are only giving a part of that message. Are trying to update or install something and using more than one method? Do you have Software Centre open and at the same time running Update Manager? Or trying to install or update through the terminal whilst having Update Manager or Synaptic Package manager open?

When an update/install utility is open it "locks" certain files to stop other utilities from interfering. 

Reboot to clear things and start again.

---

