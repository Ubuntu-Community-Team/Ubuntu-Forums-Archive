---
title: "Apt-Get via Terminal Not Working Due to Lock"
date: 2015-06-01
forum: General Help
---

### Post by Whammy on 2015-06-01
All,

I am having an issue trying to run the apt-get update/upgrade process via terminal. Ubuntu Software Updater works; however not apt-get via terminal

Running apt-get update/upgrade
> sudo apt-get update && sudo apt-get upgrade
...
...
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid-backports/multiverse i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid-backports/main Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid-backports/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid-backports/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid-backports/universe Translation-en
Fetched 700 kB in 5s (123 kB/s)
Reading package lists... Done
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?


In searching through various threads on UF, I found a few different threads suggesting different methods to solve the problem.  One thread suggesting I run the lsof command to see what process may be causing the problem

> $ sudo lsof /var/lib/dpkg/lock
lsof: WARNING: can't stat() fuse.gvfsd-fuse file system /run/user/1000/gvfs
      Output information may be incomplete.


I am not sure what this means unfortunately and am looking for some advice.

I also tried searching through the processes to see if apt was running via another command and I could not see anything.
> $ ps -e | grep -e apt -e adept | grep -v grep
$


$ sudo ps -A | grep apt
$




Both commands above yield null results.   With that said, I am unable to update Ubuntu 15.04 via the software updater app, unfortunately I cannot do it through terminal.   Any information/help would be greatly appreciated.  Thanks!

---

### Post by Dennis N on 2015-06-01
This is possibly due to another package manager or tool already running and claiming that resource, such as Ubuntu Software Center, Software Updater or Synaptic Package Manager.

---

### Post by grahammechanical on 2015-06-01
What is the answer to the question: "are you root?"

did you run those commands with sudo?

```
sudo apt-get update
sudo apt-get upgrade
```

Whenever we run a command that requires us to be administrator or root if we do not put sudo in front of the command we will get asked: "are you root?"

Regards.

---

### Post by Whammy on 2015-06-01
Thank you!  I found out I was missing my second sudo in the update command.

---

