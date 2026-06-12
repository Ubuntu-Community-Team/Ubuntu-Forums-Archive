---
title: "Problem running apt autoremove"
date: 2021-11-23
forum: General Help
---

### Post by satimis on 2021-11-23
Hi all,

Problem running "sudo apt autoremove"

$ sudo apt update```

Hit:1 http://dl.google.com/linux/chrome/deb stable InRelease
Hit:2 http://ppa.launchpad.net/openshot.developers/ppa/ubuntu focal InRelease  
Get:3 http://security.ubuntu.com/ubuntu focal-security InRelease [114 kB]      
Hit:4 http://hk.archive.ubuntu.com/ubuntu focal InRelease                      
Get:5 http://hk.archive.ubuntu.com/ubuntu focal-updates InRelease [114 kB]
Get:6 http://hk.archive.ubuntu.com/ubuntu focal-backports InRelease [101 kB]
Fetched 328 kB in 2s (175 kB/s)   
Reading package lists... Done
Building dependency tree       
Reading state information... Done
All packages are up to date.

```

All packages are up-to-date

$ sudo apt autoremove```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up virtualbox-ext-pack (6.1.26-2~ubuntu1.20.04.1) ...
virtualbox-ext-pack: downloading: https://download.virtualbox.org/virtualbox/6.1.26/Oracle_VM_VirtualBox_Extension_Pack-6.1.26.vbox-extpack
The file will be downloaded into /usr/share/virtualbox-ext-pack
License accepted.
0%...
Progress state: NS_ERROR_FAILURE
VBoxManage: error: Failed to install "/usr/share/virtualbox-ext-pack/Oracle_VM_VirtualBox_Extension_Pack-6.1.26.vbox-extpack"
VBoxManage: error: VBoxExtPackRegister returned VERR_VERSION_MISMATCH, pReg=0000000000000000 ErrInfo='Helper version mismatch - expected 0x3 got 0x30000'
VBoxManage: error: Details: code NS_ERROR_FAILURE (0x80004005), component ExtPackManagerWrap, interface IExtPackManager
VBoxManage: error: Context: "RTEXITCODE handleExtPack(HandlerArg*)" at line 1424 of file VBoxManageMisc.cpp
Installation error: License key incorrect or unknown problem during installation.
dpkg: error processing package virtualbox-ext-pack (--configure):
 installed virtualbox-ext-pack package post-installation script subprocess returned error exit status 1
Errors were encountered while processing:
 virtualbox-ext-pack
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Please advise how to fix the problem.  Thanks

Regards

---

### Post by KBar on 2021-11-23
There is nothing to remove on your system. **autoremove** only removes packages that were installed automatically. 

```
apt-mark showauto
```

will show you a list of automatically installed packages.

```
apt-mark showauto | grep 'virtualbox-ext-pack'
```

to see if it was installed automatically.

If you want to get rid of *virtualbox-ext-pack*, try using **apt purge**:

```
apt purge virtualbox-ext-pack
```

**apt**(8)
```
autoremove (apt-get(8))
           autoremove is used to remove packages that were automatically installed to satisfy dependencies for other packages and are now
           no longer needed as dependencies changed or the package(s) needing them were removed in the meantime.

           You should check that the list does not include applications you have grown to like even though they were once installed just as
           a dependency of another package. You can mark such a package as manually installed by using apt-mark(8). Packages which you have
           installed explicitly via install are also never proposed for automatic removal.

```

**apt-mark**(8)

---

### Post by satimis on 2021-11-23
> **kbar said:**
> There is nothing to remove on your system. **autoremove** only removes packages that were installed automatically. 

```
apt-mark showauto
```

will show you a list of automatically installed packages.

```
apt-mark showauto | grep 'virtualbox-ext-pack'
```

to see if it was installed automatically.

If you want to get rid of *virtualbox-ext-pack*, try using **apt purge**:

```
apt purge virtualbox-ext-pack
```

**apt**(8)
```
autoremove (apt-get(8))
           autoremove is used to remove packages that were automatically installed to satisfy dependencies for other packages and are now
           no longer needed as dependencies changed or the package(s) needing them were removed in the meantime.

           You should check that the list does not include applications you have grown to like even though they were once installed just as
           a dependency of another package. You can mark such a package as manually installed by using apt-mark(8). Packages which you have
           installed explicitly via install are also never proposed for automatic removal.

```

**apt-mark**(8)
$ apt-mark showauto | more```

accountsservice
acl
acpid
adduser
adium-theme-ubuntu
adwaita-icon-theme
alsa-topology-conf
alsa-ucm-conf
amd64-microcode
apg
apparmor
apport
apport-symptoms
appstream
apt
apt-config-icons
apt-utils
aptdaemon
aptdaemon-data
aptitude-common
apturl
apturl-common
aspell
aspell-en
autoconf
.....
```
There are many

$ apt-mark showauto | grep 'virtualbox-ext-pack'
no output

---

### Post by KBar on 2021-11-23
Thanks. What's the output of the following?

```
dpkg -l virtualbox-ext-pack
```

Also:

```
apt-mark showmanual | grep 'virtualbox-ext-pack' 
```

---

### Post by satimis on 2021-11-23
> **kbar said:**
> Thanks. What's the output of the following?

```
dpkg -l virtualbox-ext-pack
```

Also:

```
apt-mark showmanual | grep 'virtualbox-ext-pack' 
```

$ dpkg -l virtualbox-ext-pack```

Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                Version                  Architecture Description
+++-===================-========================-============-=================>
iF  virtualbox-ext-pack 6.1.26-2~ubuntu1.20.04.1 all          extra capabilitie>
lines 1-6/6 (END)

```

$ apt-mark showmanual | grep 'virtualbox-ext-pack'```

virtualbox-ext-pack

```

I'm running VitualBox here.  'virtualbox-ext-pack' was installed on the package download on their website

Thanks

---

### Post by KBar on 2021-11-23
As apt-mark suggests, the package was installed automatically. That is why apt autoremove refuses to delete it. There is nothing to fix here.

dpkg shows that the package *virtualbox-ext-pack* is currently selected for installation (the letter "i" in the first column) and that it's half-configured (the letter "F" in the second column). If you want to remove this package, run the aforementioned **purge** command.

**dpkg**(1), **dpkg-query**(1)

---

### Post by satimis on 2021-11-23
> **kbar said:**
> As apt-mark suggests, the package was installed automatically. That is why apt autoremove refuses to delete it. There is nothing to fix here.

dpkg shows that the package *virtualbox-ext-pack* is currently selected for installation (the letter "i" in the first column) and that it's half-configured (the letter "F" in the second column). If you want to remove this package, run the aforementioned **purge** command.

**dpkg**(1), **dpkg-query**(1)
There are 2 virtualbox-ext-pack here one from Ubuntu Repo and another download on VirtualBox website.  I need the latter as I install VirtuaBox on the ISO download on their website.

If running 
$ sudo apt purge virtualbox-ext-pack

Whether it'll delete the package on Ubuntu Repo?

Thanks

Regards

---

### Post by KBar on 2021-11-23
Is this the link that you downloaded the Oracle VM VirtualBox Extension Pack from?

[https://download.virtualbox.org/virtualbox/6.1.30/Oracle_VM_VirtualBox_Extension_Pack-6.1.30.vbox-extpack](https://download.virtualbox.org/virtualbox/6.1.30/Oracle_VM_VirtualBox_Extension_Pack-6.1.30.vbox-extpack)

---

### Post by satimis on 2021-11-23
> **kbar said:**
> Is this the link that you downloaded the Oracle VM VirtualBox Extension Pack from?

[https://download.virtualbox.org/virtualbox/6.1.30/Oracle_VM_VirtualBox_Extension_Pack-6.1.30.vbox-extpack](https://download.virtualbox.org/virtualbox/6.1.30/Oracle_VM_VirtualBox_Extension_Pack-6.1.30.vbox-extpack)
Sorry, I couldn't recall exactly.

The 1st time I downloaded it together with VirtualBox ISO

This Ubuntu PC has been running at least 3 years.  The ext_pack has been updated many times eversince building this Ubuntu PC and installing VirtualBox.  

Each time if there was new ext_pack to update.  When I stared VirtualBox Manage, it would ask me to update the new ext_pack.  I accepted it then it would install it automatically and delete the old version.  The complete process was fully automatic.

Regard

---

### Post by KBar on 2021-11-23
**apt** should not interfere with that at all. You can safely purge *virtualbox-ext-pack*.

Start your *Oracle VM VirtualBox Manager*, select **File**, then **Preferences** (Ctrl+G), click on the Extensions tab and check its version. Report back.

---

### Post by KBar on 2021-11-23
> **satimis said:**
> This Ubuntu PC has been running at least 3 years.  The ext_pack has been updated many times eversince building this Ubuntu PC and installing VirtualBox.

I don't see any reason to touch anything if it's been running for that long. If it ain't broke, don't fix it. 

As I have already explained, there is nothing to fix here. apt autoremove is working as intended.

---

### Post by satimis on 2021-11-23
> **kbar said:**
> **apt** should not interfere with that at all. You can safely purge *virtualbox-ext-pack*.

Start your *Oracle VM VirtualBox Manager*, select **File**, then **Preferences** (Ctrl+G), click on the Extensions tab and check its version. Report back.
Performed following steps

1)
$ sudo apt purge virtualbox-ext-pack```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  virtualbox-ext-pack*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 142 kB disk space will be freed.
Do you want to continue? [Y/n] Y 
(Reading database ... 223773 files and directories currently installed.)
Removing virtualbox-ext-pack (6.1.26-2~ubuntu1.20.04.1) ...
0%...10%...20%...30%...40%...50%...60%...70%...80%...90%...100%
Successfully uninstalled "Oracle VM VirtualBox Extension Pack".
Successfully performed extension pack cleanup
(Reading database ... 223768 files and directories currently installed.)
Purging configuration files for virtualbox-ext-pack (6.1.26-2~ubuntu1.20.04.1) ...

```

2)
Start VirtualBox Manager
-> File -> Preferences
Extension
it is empty there (pls refer to screenshot)

Thanks

Regards

---

### Post by satimis on 2021-11-23
Hi kbar,

The version of my VirtualBox
VirtualBox Graphical User Interface
Version 6.1.28 r147628 (Qt5.12.8)

I download
Oracle_VM_VirtualBox_Extension_Pack-6.1.28-147628.vbox-extpack
from Oracle website

Install it according to your advice and reboot PC.

$ sudo apt update
```

Hit:1 http://dl.google.com/linux/chrome/deb stable InRelease
Get:2 http://security.ubuntu.com/ubuntu focal-security InRelease [114 kB]      
Hit:3 http://ppa.launchpad.net/openshot.developers/ppa/ubuntu focal InRelease  
Hit:4 http://hk.archive.ubuntu.com/ubuntu focal InRelease                      
Get:5 http://hk.archive.ubuntu.com/ubuntu focal-updates InRelease [114 kB]
Get:6 http://hk.archive.ubuntu.com/ubuntu focal-backports InRelease [101 kB]
Fetched 328 kB in 2s (182 kB/s)    
Reading package lists... Done
Building dependency tree       
Reading state information... Done
All packages are up to date.
```

$ sudo apt autoremove```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

Now this time my problem gone.

Thanks again for your advice.

Regards

---

