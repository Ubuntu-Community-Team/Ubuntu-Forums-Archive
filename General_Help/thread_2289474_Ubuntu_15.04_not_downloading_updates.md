---
title: "Ubuntu 15.04 not downloading updates"
date: 2015-08-04
forum: General Help
---

### Post by Terry_Hodgson on 2015-08-04
High all. Pretty much an Ubuntu novice here. I work on a HP Pavilion Elite with Ubuntu 15.04 running. Lately I have experienced a number of problems. I hope someone on here can provide some good advice.

First, the computer erratically disconnects from my wireless network. Second, it frequently locks up during a re-start. I thought there might be some conflicting dependencies or some similar problem, and that an update might help the problem. When I try to to run the update manager, I get the message that it failed to download the repositories. So I tried to install updates from a terminal and get the following return:

terry@terry-HPE-337c:~$ apt-get install update
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
terry@terry-HPE-337c:~$ 

Any ideas what I need to do to fix the update problem?  I can engage the other problems in other threads, or hopefully a real update will help resolve the other problems. Thanks for the help.

---

### Post by howefield on 2015-08-04
For the wireless disconnect, you could try posting in the [Networking & Wireless]("http://ubuntuforums.org/forumdisplay.php?f=336") forum with the relevant information and for the update error, try prefacing the command with sudo

```
sudo apt-get update
```

---

### Post by dino99 on 2015-08-04
There is no system with a "install & forget" feature  ;)
then "update" is not a 'package name' but a 'command', so you should have typed "sudo apt-get update"

i suppose you have also never cleaned the system, right ? so from a terminal, execute each command below one after the other:
> sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install -f 

---

### Post by Terry_Hodgson on 2015-08-04
I ran all of this in a terminal. It appears that everything executed correctly. Now to see if the printers and everything still work. Thanks for the help.

---

