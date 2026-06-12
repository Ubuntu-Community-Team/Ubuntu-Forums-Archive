---
title: "[SOLVED] I broke something... please help!"
date: 2007-12-28
forum: General Help
---

### Post by fizikz on 2007-12-28
I think the main problem right now is with dkms. I tried installing the .deb from here:

[http://linux.dell.com/dkms/]("http://linux.dell.com/dkms/")

however, when I was originally installing it, I had the option to keep a certain configuration file (I don't remember the filename) or replace it with the one from the .deb. I chose to keep the one already installed, and subsequently the installation failed. If I run the deb again, it doesn't ask me that question anymore, and just fails. Now when I try to install some things from Synaptic package manager, it fails because of a problem with dkms.

Here is the error I get when trying to install the dkms .deb file:


```
#  dpkg -i dkms_2.0.17.5-0ubuntu1_all.deb
Selecting previously deselected package dkms.
(Reading database ... 156996 files and directories currently installed.)
Unpacking dkms (from dkms_2.0.17.5-0ubuntu1_all.deb) ...
Setting up dkms (2.0.17.5-0ubuntu1) ...
invoke-rc.d: initscript dkms_autoinstaller, action "start" failed.
dpkg: error processing dkms (--install):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 dkms
```

Help would be greatly appreciated!

---

### Post by Craigus on 2007-12-28
dkms shows in synaptic on my system - what happens if you try to install the package via synaptic ?

---

### Post by RPDiep on 2007-12-28
Perhaps a stupid question, but did you try removing the deb again and see what happens?

Code: dpkg -r dkms_2.0.17.5-0ubuntu1_all.deb

---

### Post by fizikz on 2007-12-28
Thank you, thank you, thank you, Craigus!!! It was a simple solution but it worked. dkms showed up in Synaptic package manager as installed, so I chose to uninstall it completely (there was no option for reinstallation). After this, searching for dkms in the package manager yielded no results. Then I installed the downloaded .deb (for dkms) and the installation succeeded. Now it shows up again in Synaptic.

Here is the before and after terminal output on the state of the dkms installation:

Before:
```
$ dpkg -l dkms
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-files/Unpacked/Failed-config/Half-installed
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
pn  dkms           <none>         (no description available)

```

Installation after removal of dkms package from Synaptic package manager:
```
$ sudo dpkg -i dkms_2.0.17.5-0ubuntu1_all.deb
Password:
Selecting previously deselected package dkms.
(Reading database ... 156977 files and directories currently installed.)
Unpacking dkms (from dkms_2.0.17.5-0ubuntu1_all.deb) ...
Setting up dkms (2.0.17.5-0ubuntu1) ...


```

After (apparently) successful installation of dkms:
```
$ dpkg -l dkms
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-files/Unpacked/Failed-config/Half-installed
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  dkms           2.0.17.5-0ubun Dynamic Kernel Module Support Framework

```

It was a simple solution; I can't believe it didn't occur to me to try that. 

Thank you all!

PS. RPDiep, I had previously tried that and it didn't work, but thanks for the suggestion.

---

