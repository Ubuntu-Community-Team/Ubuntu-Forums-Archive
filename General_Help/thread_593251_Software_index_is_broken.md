---
title: "Software index is broken"
date: 2007-10-27
forum: General Help
---

### Post by Kalur on 2007-10-27
I get a "Software Index is broken" message box when I try to update Ubuntu. The message box says

'It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.'

Synaptic will not work when I try it and when I run "sudo apt-get install -f" I get the following message.

Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED:
linux-headers-2.6.20-15
0 upgraded, 0 newly installed, 1 to remove and 1 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 58.3MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 140475 files and directories currently installed.)
Removing linux-headers-2.6.20-15 ...
dpkg: error processing linux-headers-2.6.20-15 (--remove):
cannot remove file `/usr/src/linux-headers-2.6.20-15/arch/powerpc/kernel/Makefile': Not a directory
Errors were encountered while processing:
linux-headers-2.6.20-15
E: Sub-process /usr/bin/dpkg returned an error code (1)

Any help would be much appreciated.

---

### Post by Kalur on 2007-10-27
I can't figure out what the error message is trying to tell me.

Did my linux-headers not install correctly?

Did this directory not get loaded as it should: /usr/src/linux-headers-2.6.20-15/arch/powerpc/kernel/Makefile?

Or is /usr/bin/dpkg returned an error code (1) the problem?

---

### Post by Steve1961 on 2007-10-27
Try running:

sudo dpkg --configure -a

---

### Post by Kalur on 2007-10-27
I get no response when I run sudo dpkg --configure -a :(

---

### Post by Steve1961 on 2007-10-27
Try 

sudo dpkg --remove --force-remove-reinstreq linux-headers-2.6.20-15

---

### Post by Kalur on 2007-10-27
No luck when I try sudo dpkg --remove --force-remove-reinstreq linux-headers-2.6.20-15.  Here's what I get:

(Reading database ... 140475 files and directories currently installed.)
Removing linux-headers-2.6.20-15 ...
dpkg: error processing linux-headers-2.6.20-15 (--remove):
 cannot remove file `/usr/src/linux-headers-2.6.20-15/arch/powerpc/kernel/Makefile': Not a directory
Errors were encountered while processing:
 linux-headers-2.6.20-15

---

### Post by Steve1961 on 2007-10-27
Sorry, afraid I'm out of ideas.  Anyone else?

---

### Post by Kalur on 2007-10-27
Thanks for trying Steve :)  Because I'm new to Ubuntu I'm not sure what the error message is trying to tell me.  I think that would be a start...if I can figure it out.  It sounds like I can't remove /usr/src/linux-headers-2.6.20-15/arch/powerpc/kernel/Makefile because it isn't a directory.  Whatever that means...

---

### Post by jayaramk on 2007-10-27
why does'nt synaptic work... it definitely works the synaptic package manager is present at...

system->administration->synaptic package manager

---

### Post by Kalur on 2007-10-27
I get this error message when using synaptic:

E: linux-headers-2.6.20-15: cannot remove file `/usr/src/linux-headers-2.6.20-15/arch/powerpc/kernel/Makefile'

Basically I can't update anything at the moment.

---

### Post by Kalur on 2007-10-28
bump

---

