---
title: "[SOLVED] Old Kernel removal errors"
date: 2007-12-02
forum: General Help
---

### Post by NeoFax on 2007-12-02
I was trying to clean up some old files from my system as the /boot directory is full.  Whilst doing this, i cannot remove the old kernel module package as ubuntu's post removal calls update-initramfs for some reason.  Here is the exact error:

```
terry@MYTHBOX:/boot$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED:
  linux-ubuntu-modules-2.6.22-13-generic
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 9867kB disk space will be freed.
Do you want to continue [Y/n]?
(Reading database ... 210599 files and directories currently installed.)
Removing linux-ubuntu-modules-2.6.22-13-generic ...
FATAL: Could not open '/boot/System.map-2.6.22-13-generic': No such file or directory
update-initramfs: Generating /boot/initrd.img-2.6.22-13-generic
Cannot find /lib/modules/2.6.22-13-generic
update-initramfs: failed for /boot/initrd.img-2.6.22-13-generic
dpkg: error processing linux-ubuntu-modules-2.6.22-13-generic (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-ubuntu-modules-2.6.22-13-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

:confused:
How exactly can I go about removing this file?  Thanks!

---

### Post by pjalegria on 2007-12-02
same problem...

---

### Post by zvacet on 2007-12-02
```
sudo dpkg --configure -a
```

Why don´t you remove it from synaptic?Find linux-image and decide wich one you want to remove.

---

### Post by pjalegria on 2007-12-03
Ok , it works but now i try to remove residual configuration on Synapitc and i have this error:

E: linux-ubuntu-modules-2.6.22-14-386: subprocesso post-removal script retornou erro do status de saída 1

---

### Post by NeoFax on 2007-12-04
Does not work doing sudo dpkg --configure -a.  Apt still is broke as the linux-image-2.6.22-13 deb file is missing which is needed to remove the modules deb.  I understand the need to call update-initramfs after installing the modules deb, but there has got to be a way to either a) run a command line switch to dpkg to force postrm to not run or b) manually remove the string in the apt database that points to this file even being installed.  Also, it is bad package scripts that caused this to happen.  When I ran sudo apt-get remove linux-image-2.6.22-13 it should have automatically removed all dependent packages along with that package.  So as of right now I cannot upgrade my system which presents a security risk.

UPDATE: Well, I guess I ran my mouth a little too fast and was a tad lazy.  ;^)  Anyhow, here is a link that explains a similar situation and their fix for the problem:
[http://www.linuxquestions.org/questions/debian-26/permantly-removing-a-program-from-apt-get-294533/]("http://www.linuxquestions.org/questions/debian-26/permantly-removing-a-program-from-apt-get-294533/")

So, after commenting out the update-initramfs line in the .postrm file my apt-get now works and the file was removed.  Thsi is why I love the linux community.  Such great comraderie and open documentation!

BTW, Why did the MOTU's remove these packages that were shipped with Gutsy? Shouldn't there have been a message or something stating, "Please remove package X before this date otherwise Y may happen."

---

