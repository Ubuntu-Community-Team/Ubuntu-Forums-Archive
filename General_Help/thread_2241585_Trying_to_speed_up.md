---
title: "Trying to speed up"
date: 2014-08-27
forum: General Help
---

### Post by grandad67 on 2014-08-27
My newish install of 14.4 seems 'startup slow'. I changed to gnome, then found cleanup help from this forum. Autoclean has shown a problem(see below) and I wonder what I should do to put it right and how much the problem affects my computer.


$ sudo apt-get autoclean

 [sudo] password for cjf:  
 E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
 E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
any help will be appreciated.......................sarum

---

### Post by slickymaster on 2014-08-27
> **grandad67 said:**
> My newish install of 14.4 seems 'startup slow'. I changed to gnome, then found cleanup help from this forum. Autoclean has shown a problem(see below) and I wonder what I should do to put it right and how much the problem affects my computer.


$ sudo apt-get autoclean

 [sudo] password for cjf:  
 [COLOR=#ff0000]E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
 E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?[/COLOR]
any help will be appreciated.......................sarum

This means that something else is installing or removing software and has locked the apt database while it performs the actions. The likely suspects are generally:
[LIST]
[*]Software Center
[*]Update Manager
[*]apt-get or aptitude command line utilities.
[/LIST]
You can force the lock off by removing the file, but it's not recommended without first closing the program that's holding the lock safely, since you could cause corruption or interrupt an installation (bad).

You can use```
sudo lsof /var/lib/dpkg/lock
```at the command line to find the process that owns the lock file and then kill it by running```
sudo kill -9 <PID> # get <PID> from the previous lsof output
```

If for some reason you aren't able to find the process and/or kill it, just delete the lock file with the following command:```
sudo rm /var/lib/apt/lists/lock
```
Afterwards run```
sudo apt-get update && sudo apt-get upgrade
```and post back here the output you get from this last command, [using code tags]("http://ubuntuforums.org/showthread.php?t=2171721&p=12776168&viewfull=1#post12776168") for the effect.

---

### Post by grandad67 on 2014-08-28
Thanks for your help. I actually ran your last suggestion first - update........upgrade and that mended it. Thanks again..........sarum

---

### Post by slickymaster on 2014-08-28
You're welcome. Happy *buntuing.

---

