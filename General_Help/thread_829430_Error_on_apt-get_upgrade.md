---
title: "Error on apt-get upgrade"
date: 2008-06-14
forum: General Help
---

### Post by SyntaXe on 2008-06-14
Hello folks!
I got big probs on my apt upgrade, could someone help me out, since the apt-get install command dont even work... :S

Thanks!

```
syntaxe@osiris:~$ sudo apt-get upgrade
[sudo] password for syntaxe: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up python-pexpect (2.1-1build1) ...
pycentral: pycentral pkginstall: not overwriting local files
pycentral pkginstall: not overwriting local files
dpkg: error processing python-pexpect (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 python-pexpect
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by x1a4 on 2008-06-14
Hi,

python-pexpect is neither installed nor removed correctly.  Purge it (remove completely), and if you need it, install it.  If other packages depend on it, try reinstalling it.  

Purge: ```
apt-get --purge python-pexpect
```

EDIT: If you can't purge using apt-get try using dpkg directly
```
dpkg -P python-pexpect
```

Aside: Once you've fixed this, stop using apt-get.  Use aptitude instead.  Aptitude has better dependency handling, and is better able to resolve issues like this.  Aptitude also removes packages better then apt-get.

---

### Post by SyntaXe on 2008-06-14
Thanks!
It looks like I got python-pexpect from a update for a script, so its needed.
But still, the script works, but I keep getting the error.
And if I remove it, the script stops working. But still, getting things done. But the error is still annoying me :S

Example:

```

syntaxe@osiris:~$ sudo aptitude install xtron
[sudo] password for syntaxe: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
The following NEW packages will be installed:
  xtron 
The following partially installed packages will be configured:
  python-pexpect 
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/20.6kB of archives. After unpacking 266kB will be used.
Writing extended state information... Done
Selecting previously deselected package xtron.
(Reading database ... 124020 files and directories currently installed.)
Unpacking xtron (from .../xtron_1.1a-13_i386.deb) ...
Setting up python-pexpect (2.1-1build1) ...
pycentral: pycentral pkginstall: not overwriting local files
pycentral pkginstall: not overwriting local files
dpkg: error processing python-pexpect (--configure):
 subprocess post-installation script returned error exit status 1
Setting up xtron (1.1a-13) ...

Errors were encountered while processing:
 python-pexpect
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up python-pexpect (2.1-1build1) ...
pycentral: pycentral pkginstall: not overwriting local files
pycentral pkginstall: not overwriting local files
dpkg: error processing python-pexpect (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 python-pexpect
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done 

```

---

