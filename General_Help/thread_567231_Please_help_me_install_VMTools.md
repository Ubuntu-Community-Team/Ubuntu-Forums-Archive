---
title: "Please help me install VMTools"
date: 2007-10-04
forum: General Help
---

### Post by wynchgo on 2007-10-04
I'm using the trial version of VMware Workstation 6 and I'm trying to install the VMTools.  I see a vmware-tools-distrib folder on the desktop and I opened it up and double clicked on the install.pl file but nothing happens.  Can someone PLEASE be so kind to post explicit instructions on installing this?  I'm a complete noob when it comes to Linux.

Thanks in advance.
wy

---

### Post by TalioGladius on 2007-10-04
using the console, change directories to the vmware-tools-distrib folder, such as

cd /home/yourname/vmware-tools-distrib

Then invoke this command.

sudo ./vmware-install.pl

(you'll have to verify the file name by doing an ls command)

it will walk you through the install, you should be able to accept all defaults.

---

### Post by jocko on 2007-10-04
Before you follow TalioGladius' instructions, you may need to install a few packages in order to get it working.
I'm pretty sure you'll need the packages "build-essential" and "linux-headers-generic".
Either find them in synaptic or copy this and paste in a terminal:
```
sudo apt-get install build-essential linux-headers-generic
```

---

### Post by wynchgo on 2007-10-04
Ok I ran the command Jocko suggested first (packages installed fine) and then tried to install them again and it still didn't work per Talio's instructions.  I'm getting an error now.  See the attached pics.  It's saying there's no such directory when it's obvious on the desktop.

Wy

---

### Post by distroman on 2007-10-04
```
sudo Desktop/vmware-tools-distrib/vmware-install.pl
```

---

### Post by wynchgo on 2007-10-04
> **distroman said:**
> ```
sudo Desktop/vmware-tools-distrib/vmware-install.pl
```
Thanks for the reply distroman.  I think I'm almost there.  Now it's telling me to remove 3 files.  See pic below and how should I remove them?

Wy

---

