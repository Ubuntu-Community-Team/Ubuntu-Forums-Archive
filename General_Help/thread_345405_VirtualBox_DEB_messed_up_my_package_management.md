---
title: "VirtualBox DEB messed up my package management"
date: 2007-01-24
forum: General Help
---

### Post by Typhon on 2007-01-24
Today I tried to install [VirtualBox DEB package](http://www.virtualbox.org/wiki/Downloads) for Ubuntu 6.10. I got this error:

> Selecting previously deselected package virtualbox.
(Reading database ...
dpkg: serious warning: files list file for package `virtualbox' missing, assuming package has no files curr                                                 ently installed.
104562 files and directories currently installed.)
Preparing to replace virtualbox 1.3.2-20070114_Ubuntu_edgy (using VirtualBox_1.3.2_Ubuntu_Edgy_x86.deb) ...
Unpacking replacement virtualbox ...
Setting up virtualbox (1.3.2-20070114_Ubuntu_edgy) ...
-e
Creating group 'vboxusers'. VM users must be member of that group!

No precompiled module for this kernel found -- trying to build one
Messages displayed during module compilation will be logged to /var/log/vbox-install.log
Compilation of kernel module failed, aborting installation
dpkg: error processing virtualbox (--install):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 virtualbox


Later I tried to install some other packages via apt-get but it always gave me this error:

> virtualboxpackage has to be reinstalled, but I can't find its archive.

Running *sudo dpkg --configure -a* command doesn't help and reinstalling doesn't help either. 

sudo dpkg --purge virtualbox returns:
> (Reading database ... 105057 files and directories currently installed.)
Removing virtualbox ...
(Kernel module not found)...fail!
invoke-rc.d: initscript virtualbox, action "stop" failed.
dpkg: error processing virtualbox (--purge):
 subprocess pre-removal script returned error exit status 1
-e
Creating group 'vboxusers'. VM users must be member of that group!

No precompiled module for this kernel found -- trying to build one
Messages displayed during module compilation will be logged to /var/log/vbox-install.log
Compilation of kernel module failed, aborting installation
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 virtualbox


Then I manually removed all files related to VirtualBox from my system, but the problem still persists. What should I do? Please help.  :-\ I use Kubuntu 6.10.

---

### Post by gwpritch on 2007-01-24
Have you tried deleting your original download and obtaining a fresh copy of the archive.
Perhaps the original was corrupted. Also ensure you downloaded the version for edgy.

---

### Post by Typhon on 2007-01-24
Yes, I tried that as well. The DEB package was is for Edgy. Is there any way to completely remove all traces of VirtualBox installation so that APT will stop reporting problems?

---

### Post by Typhon on 2007-01-24
**SOLUTION:**
I just found a solution! It's a very dirty one, but it works! :-D

[list][*]Delete from the system all files related to VirtualBox
[*]Find all entries in /var directory, in config. text files, containing search string "virtualbox"
[*]Delete these entries with KWrite/Kate
[*]Voila! It works again! ;-)[/list]

I've learnt a lot in this "experiment".

---

