---
title: "[SOLVED] find/delete extra files program/script?"
date: 2008-06-25
forum: General Help
---

### Post by moore.bryan on 2008-06-25
so... i've uninstalled many programs, often with "sudo aptitude remove --purge", but there are still a number of files associated with those removed programs on my system. is there a program or script to "search and destroy" those left-overs?

---

### Post by unutbu on 2008-06-25
[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)

---

### Post by moore.bryan on 2008-06-26
excellent; thanks, that thread works great. i'm surprised, though, all the separate steps in that method haven't been reproduced in synaptic, a separate program, or in a single script.

---

### Post by moore.bryan on 2008-06-26
strange... when i try to remove five certain packages with the residual configuration removal tool in synaptic, i get this:
```
E: jadetex: subprocess post-removal script returned error exit status 127
E: linux-ubuntu-modules-2.6.22-11-generic: subprocess post-removal script returned error exit status 1
E: linux-ubuntu-modules-2.6.22-13-generic: subprocess post-removal script returned error exit status 1
E: linux-ubuntu-modules-2.6.24-12-generic: subprocess post-removal script returned error exit status 1
E: linux-ubuntu-modules-2.6.24-15-generic: subprocess post-removal script returned error exit status 1

```

---

### Post by unutbu on 2008-06-26
What output do you get when you run
```

sudo apt-get purge jadetex
```
from the terminal command line?

---

### Post by moore.bryan on 2008-06-26
```
moore@thinkpad:~$ sudo apt-get purge jadetex
Reading package lists... Done
Building dependency tree        
Reading state information... Done
Package jadetex is not installed, so not removed
```

---

### Post by unutbu on 2008-06-26
It looks like jadetex has been successfully removed:
> Package jadetex is not installed, so not removed

What output do you get when you type

```
sudo apt-get remove linux-ubuntu-modules-2.6.22-11-generic
```

---

### Post by moore.bryan on 2008-06-26
the same bit about it not being installed, but it is still listed in synaptic under "not installed (residual config)." any ideas what gives?

---

### Post by moore.bryan on 2008-06-26
```
moore@thinkpad:~$ sudo dpkg --purge jadetex
(Reading database ... 197189 files and directories currently installed.)
Removing jadetex ...
Purging configuration files for jadetex ...
/var/lib/dpkg/info/jadetex.postrm: 71: update-texmf: not found
dpkg: error processing jadetex (--purge):
 subprocess post-removal script returned error exit status 127
Errors were encountered while processing:
 jadetex
```
this sounds silly, but could reinstalling the packages and then completely removing them via synaptic solve this little conundrum?

---

### Post by unutbu on 2008-06-26
> this sounds silly, but could reinstalling the packages and then completely removing them via synaptic solve this little conundrum?
Actually, that sounds rather clever to me.

---

### Post by moore.bryan on 2008-06-26
i guess clever/silly is in the eye of the beholder... the gerry-rigged solution worked masterfully for jadetex; however, each of the linux modules is returning a simple ```
Package linux-ubuntu-modules-2.6.24-15-generic has no available version, but exists in the database.
This typically means that the package was mentioned in a dependency and never uploaded, has been obsoleted or is not available with the contents of sources.list
```

---

### Post by moore.bryan on 2008-06-26
and when i try "sudo dpkg --purge linux-ubuntu-modules-2.6.24-15-generic" is get this:
```
moore@thinkpad:~$ sudo dpkg --purge linux-ubuntu-modules-2.6.24-15-generic
[sudo] password for moore: 
(Reading database ... 197197 files and directories currently installed.)
Removing linux-ubuntu-modules-2.6.24-15-generic ...
Purging configuration files for linux-ubuntu-modules-2.6.24-15-generic ...
FATAL: Could not open '/boot/System.map-2.6.24-15-generic': No such file or directory
update-initramfs: Generating /boot/initrd.img-2.6.24-15-generic
Cannot find /lib/modules/2.6.24-15-generic
update-initramfs: failed for /boot/initrd.img-2.6.24-15-generic
dpkg: error processing linux-ubuntu-modules-2.6.24-15-generic (--purge):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-ubuntu-modules-2.6.24-15-generic
```

---

### Post by unutbu on 2008-06-26
[http://ubuntuforums.org/showthread.php?t=826777](http://ubuntuforums.org/showthread.php?t=826777)

---

### Post by moore.bryan on 2008-06-26
brilliant!

---

