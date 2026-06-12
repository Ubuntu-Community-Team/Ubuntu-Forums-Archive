---
title: "How to fix no link to ppa ?"
date: 2022-04-23
forum: General Help
---

### Post by satimis on 2022-04-23
**[COLOR="#FF0000"]Ubuntu 22.04 desktop[/COLOR]**

How to fix no link to ppa ?

$ sudo add-apt-repository ppa:alexlarsson/flatpak```

PPA publishes dbgsym, you may need to include 'main/debug' component
Repository: 'deb https://ppa.launchpadcontent.net/alexlarsson/flatpak/ubuntu/ jammy main'
Description:
 Linux application sandboxing and distribution framework
More info: https://launchpad.net/~alexlarsson/+archive/ubuntu/flatpak
Adding repository.
Press [ENTER] to continue or Ctrl-c to cancel.
Found existing deb entry in /etc/apt/sources.list.d/alexlarsson-ubuntu-flatpak-jammy.list
Adding deb entry to /etc/apt/sources.list.d/alexlarsson-ubuntu-flatpak-jammy.list
Found existing deb-src entry in /etc/apt/sources.list.d/alexlarsson-ubuntu-flatpak-jammy.list
Adding disabled deb-src entry to /etc/apt/sources.list.d/alexlarsson-ubuntu-flatpak-jammy.list
Adding key to /etc/apt/trusted.gpg.d/alexlarsson-ubuntu-flatpak.gpg with fingerprint 690951F1A4DE0F905496E8C6C793BFA2FA577F07
Hit:1 http://archive.canonical.com/ubuntu focal InRelease                                                       
Ign:2 https://ppa.launchpadcontent.net/alexlarsson/flatpak/ubuntu jammy InRelease                               
Err:3 https://ppa.launchpadcontent.net/alexlarsson/flatpak/ubuntu jammy Release
  404  Not Found [IP: 91.189.95.85 443]
Hit:4 http://archive.ubuntu.com/ubuntu focal InRelease   
Hit:5 http://archive.ubuntu.com/ubuntu focal-updates InRelease
Hit:6 http://archive.ubuntu.com/ubuntu focal-security InRelease
Hit:7 http://archive.ubuntu.com/ubuntu focal-backports InRelease
Reading package lists... Done
E: The repository 'https://ppa.launchpadcontent.net/alexlarsson/flatpak/ubuntu jammy Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
```

$ sudo add-apt-repository ppa:tomtomtom/woeusb```

Repository: 'deb https://ppa.launchpadcontent.net/tomtomtom/woeusb/ubuntu/ jammy main'
Description:
WoeUSB is a simple tool that enable you to create your own usb stick windows installer from an iso image or a real DVD. It is a fork of Congelli501's WinUSB.
More info: https://launchpad.net/~tomtomtom/+archive/ubuntu/woeusb
Adding repository.
Press [ENTER] to continue or Ctrl-c to cancel.
Adding deb entry to /etc/apt/sources.list.d/tomtomtom-ubuntu-woeusb-jammy.list
Adding disabled deb-src entry to /etc/apt/sources.list.d/tomtomtom-ubuntu-woeusb-jammy.list
Adding key to /etc/apt/trusted.gpg.d/tomtomtom-ubuntu-woeusb.gpg with fingerprint CEC312CC5ED8215A6E0EFC49B90E9186F0E836FB
Hit:1 http://archive.ubuntu.com/ubuntu focal InRelease
Hit:2 http://archive.canonical.com/ubuntu focal InRelease
Hit:3 http://archive.ubuntu.com/ubuntu focal-updates InRelease
Hit:4 http://archive.ubuntu.com/ubuntu focal-security InRelease
Hit:5 http://archive.ubuntu.com/ubuntu focal-backports InRelease
Ign:6 https://ppa.launchpadcontent.net/alexlarsson/flatpak/ubuntu jammy InRelease
Get:7 https://ppa.launchpadcontent.net/tomtomtom/woeusb/ubuntu jammy InRelease [18.0 kB]
Err:8 https://ppa.launchpadcontent.net/alexlarsson/flatpak/ubuntu jammy Release
  404  Not Found [IP: 91.189.95.85 443]
Get:9 https://ppa.launchpadcontent.net/tomtomtom/woeusb/ubuntu jammy/main amd64 Packages [608 B]
Get:10 https://ppa.launchpadcontent.net/tomtomtom/woeusb/ubuntu jammy/main Translation-en [208 B]
Reading package lists... Done                             
E: The repository 'https://ppa.launchpadcontent.net/alexlarsson/flatpak/ubuntu jammy Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.

```

Thanks

Regards

---

### Post by #&amp;thj^% on 2022-04-23
they have not updated to jammy yet
20.04 to 16.04 only so far

---

### Post by &amp;KyT$0P# on 2022-04-23
> **satimis said:**
> $ sudo add-apt-repository ppa:alexlarsson/flatpak

This PPA is dead.  There is a replacement pointed to in the [flatpak setup instructions]("https://www.flatpak.org/setup/Ubuntu"), but that one has not yet been updated for 22.04 because it currently provides flatpak version 1.12.7, which is already in 22.04 standard repositories.

---

### Post by satimis on 2022-04-23
> **halogen2 said:**
> This PPA is dead.  There is a replacement pointed to in the [flatpak setup instructions]("https://www.flatpak.org/setup/Ubuntu"), but that one has not yet been updated for 22.04 because it currently provides flatpak version 1.12.7, which is already in 22.04 standard repositories.
Flatpak on Ubuntu 22.04 repo doesn't work.  I also tried it before posting

$ sudo apt install flatpak
or
$ sudo apt install flatpak -y```

Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libgdk-pixbuf-2.0-0 : Breaks: libgdk-pixbuf2.0-0 (< 2.40.0+dfsg-6~) but 2.40.0+dfsg-3ubuntu0.2 is to be installed
 libgdk-pixbuf2.0-0 : Depends: libgdk-pixbuf2.0-common (= 2.40.0+dfsg-3ubuntu0.2) but 2.42.8+dfsg-1 is to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.

```

Regards

---

### Post by &amp;KyT$0P# on 2022-04-23
That's not right.  Could you please post the output of
```
apt-cache policy libgdk-pixbuf-2.0-0
```

---

### Post by satimis on 2022-04-23
> **halogen2 said:**
> That's not right.  Could you please post the output of
```
apt-cache policy libgdk-pixbuf-2.0-0
```
$ apt-cache policy libgdk-pixbuf-2.0-0```

libgdk-pixbuf-2.0-0:
  Installed: 2.42.8+dfsg-1
  Candidate: 2.42.8+dfsg-1
  Version table:
 *** 2.42.8+dfsg-1 100
        100 /var/lib/dpkg/status

```
Regards

---

### Post by ajgreeny on 2022-04-24
Did you run ***sudo apt update*** before trying those two apt install commands?

---

### Post by satimis on 2022-04-24
> **ajgreeny said:**
> Did you run ***sudo apt update*** before trying those two apt install commands?
Yes, I did,

I have tried several times to install those 2 applications with the same result.

Regards

---

### Post by Dennis N on 2022-04-24
For what it's worth, my newly-installed Ubuntu 22.04 has libgdk-pixbuf-2.0-0, but does not have the 2nd package, libgdk-pixbuf2.0-0. Why do you have it? You might investigate what needs the 2nd one, or just remove it and see if there are any adverse effects. Your call.

Evidence:
```
dmn@Tyana-vm:~$ apt-cache policy libgdk-pixbuf-2.0-0
libgdk-pixbuf-2.0-0:
  Installed: 2.42.8+dfsg-1
  Candidate: 2.42.8+dfsg-1
  Version table:
 *** 2.42.8+dfsg-1 500
        500 http://mirror.arizona.edu/ubuntu jammy/main amd64 Packages
        100 /var/lib/dpkg/status

dmn@Tyana-vm:~$ apt-cache policy libgdk-pixbuf2.0-0
libgdk-pixbuf2.0-0:
  Installed: (none)
  Candidate: 2.40.2-2build4
  Version table:
     2.40.2-2build4 500
        500 http://mirror.arizona.edu/ubuntu jammy/universe amd64 Packages
 
```

---

### Post by satimis on 2022-04-24
> **Dennis N said:**
> For what it's worth, my newly-installed Ubuntu 22.04 has libgdk-pixbuf-2.0-0, but does not have the 2nd package, libgdk-pixbuf2.0-0. Why do you have it? You might investigate what needs the 2nd one, or just remove it and see if there are any adverse effects. Your call.

Evidence:
```
dmn@Tyana-vm:~$ apt-cache policy libgdk-pixbuf-2.0-0
libgdk-pixbuf-2.0-0:
  Installed: 2.42.8+dfsg-1
  Candidate: 2.42.8+dfsg-1
  Version table:
 *** 2.42.8+dfsg-1 500
        500 http://mirror.arizona.edu/ubuntu jammy/main amd64 Packages
        100 /var/lib/dpkg/status

dmn@Tyana-vm:~$ apt-cache policy libgdk-pixbuf2.0-0
libgdk-pixbuf2.0-0:
  Installed: (none)
  Candidate: 2.40.2-2build4
  Version table:
     2.40.2-2build4 500
        500 http://mirror.arizona.edu/ubuntu jammy/universe amd64 Packages
 
```
$ apt-cache policy libgdk-pixbuf-2.0-0```

libgdk-pixbuf-2.0-0:
  Installed: 2.42.8+dfsg-1
  Candidate: 2.42.8+dfsg-1
  Version table:
 *** 2.42.8+dfsg-1 100
        100 /var/lib/dpkg/status

```

$ sudo apt remove libgdk-pixbuf-2.0-0```

.....
.....
Removing gnome-terminal (3.44.0-1ubuntu1) ...
Removing libgdk-pixbuf-2.0-0:amd64 (2.42.8+dfsg-1) ...
Setting up xterm (353-1ubuntu1.20.04.2) ...
update-alternatives: using /usr/bin/xterm to provide /usr/bin/x-terminal-emulator (x-terminal-emulator) in auto mode
update-alternatives: using /usr/bin/lxterm to provide /usr/bin/x-terminal-emulator (x-terminal-emulator) in auto mode
Processing triggers for desktop-file-utils (0.26-1ubuntu3) ...
Processing triggers for hicolor-icon-theme (0.17-2) ...
Processing triggers for gnome-menus (3.36.0-1ubuntu3) ...
Processing triggers for libglib2.0-0:amd64 (2.72.1-1) ...
Processing triggers for libc-bin (2.35-0ubuntu3) ...
Processing triggers for man-db (2.10.2-1) ...
Processing triggers for libreoffice-common (1:7.3.2-0ubuntu2) ...
Processing triggers for dbus (1.12.20-2ubuntu4) ...
Processing triggers for shared-mime-info (2.1-2) ...
Processing triggers for mailcap (3.70+nmu1ubuntu1) ...

```

$ apt-cache policy libgdk-pixbuf-2.0-0```

libgdk-pixbuf-2.0-0:
  Installed: (none)
  Candidate: (none)
  Version table:
     2.42.8+dfsg-1 -1
        100 /var/lib/dpkg/status

```

$ sudo apt install flatpak
and
$ sudo apt install flatpak -y

```

Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libgdk-pixbuf2.0-0 : Depends: libgdk-pixbuf2.0-common (= 2.40.0+dfsg-3ubuntu0.2) but 2.42.8+dfsg-1 is to be installed
                      Recommends: libgdk-pixbuf2.0-bin
E: Unable to correct problems, you have held broken packages.
```

Regards

---

### Post by Dennis N on 2022-04-24
```
sudo apt remove libgdk-pixbuf-2.0-0
```
The command you show you used (above) removes the wrong one. I suggested removing the 2nd package mentioned, which is libgdk-pixbuf2.0-0.
It also made another problem or sorts. The output says it is removing gnome-terminal which is not good:
```
Removing gnome-terminal (3.44.0-1ubuntu1) ...
Removing libgdk-pixbuf-2.0-0:amd64 (2.42.8+dfsg-1) ...
Setting up xterm (353-1ubuntu1.20.04.2) .. 

```You should reinstall these 2 removed packages. 
**libgdk-pixbuf2.0-0** is the one I don't have my system, and is the one I thought might be safe to remove - but always check what if anything is going to get removed with it.

---

### Post by satimis on 2022-04-24
> **Dennis N said:**
> ```
sudo apt remove libgdk-pixbuf-2.0-0
```
The command you show you used (above) removes the wrong one. I suggested removing the 2nd package mentioned, which is libgdk-pixbuf2.0-0.
It also made another problem or sorts. The output says it is removing gnome-terminal which is not good:
```
Removing gnome-terminal (3.44.0-1ubuntu1) ...
Removing libgdk-pixbuf-2.0-0:amd64 (2.42.8+dfsg-1) ...
Setting up xterm (353-1ubuntu1.20.04.2) .. 

```You should reinstall these 2 removed packages. 
**libgdk-pixbuf2.0-0** is the one I don't have my system, and is the one I thought might be safe to remove - but always check what if anything is going to get removed with it.
Ob, Sorry.

I couldn't start GUI of this VM but popup command prompt

Login but I couldn't install;
gnome-terminal
libgdk-pixbuf-2.0-0

Clone a new VM on the original ubuntu22.04 VM 

$ apt-cache policy libgdk-pixbuf-2.0-0```

libgdk-pixbuf-2.0-0:
  Installed: 2.42.8+dfsg-1
  Candidate: 2.42.8+dfsg-1
  Version table:
 *** 2.42.8+dfsg-1 100
        100 /var/lib/dpkg/status
        
```
        
$ sudo apt remove libgdk-pixbuf2.0-0```

Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Package 'libgdk-pixbuf2.0-0' is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```
        
$ apt-cache policy libgdk-pixbuf2.0-0```

libgdk-pixbuf2.0-0:
  Installed: (none)
  Candidate: 2.40.0+dfsg-3ubuntu0.2
  Version table:
     2.40.0+dfsg-3ubuntu0.2 500
        500 http://archive.ubuntu.com/ubuntu focal-updates/main amd64 Packages
        500 http://archive.ubuntu.com/ubuntu focal-security/main amd64 Packages
     2.40.0+dfsg-3 500
        500 http://archive.ubuntu.com/ubuntu focal/main amd64 Packages

```     

Regards

---

### Post by Dennis N on 2022-04-24
Well, this is good. The (presumed) offending package is now not installed. I would imagine everything will now work, such as installing flatpak support.

---

### Post by satimis on 2022-04-24
> **Dennis N said:**
> Well, this is good. The (presumed) offending package is now not installed. I would imagine everything will now work, such as installing flatpak support.
Problem still remains.

$ sudo add-apt-repository ppa:alexlarsson/flatpak```

PPA publishes dbgsym, you may need to include 'main/debug' component
Repository: 'deb https://ppa.launchpadcontent.net/alexlarsson/flatpak/ubuntu/ jammy main'
Description:
 Linux application sandboxing and distribution framework
More info: https://launchpad.net/~alexlarsson/+archive/ubuntu/flatpak
Adding repository.
Press [ENTER] to continue or Ctrl-c to cancel.
Adding deb entry to /etc/apt/sources.list.d/alexlarsson-ubuntu-flatpak-jammy.list
Adding disabled deb-src entry to /etc/apt/sources.list.d/alexlarsson-ubuntu-flatpak-jammy.list
Adding key to /etc/apt/trusted.gpg.d/alexlarsson-ubuntu-flatpak.gpg with fingerprint 690951F1A4DE0F905496E8C6C793BFA2FA577F07
Hit:1 http://archive.ubuntu.com/ubuntu focal InRelease
Get:2 http://archive.ubuntu.com/ubuntu focal-updates InRelease [114 kB]
Hit:3 http://archive.canonical.com/ubuntu focal InRelease
Get:4 http://archive.ubuntu.com/ubuntu focal-security InRelease [114 kB]    
Get:5 http://archive.ubuntu.com/ubuntu focal-backports InRelease [108 kB]                 
Ign:6 https://ppa.launchpadcontent.net/alexlarsson/flatpak/ubuntu jammy InRelease        
Err:7 https://ppa.launchpadcontent.net/alexlarsson/flatpak/ubuntu jammy Release
  404  Not Found [IP: 91.189.95.85 443]
Reading package lists... Done
E: The repository 'https://ppa.launchpadcontent.net/alexlarsson/flatpak/ubuntu jammy Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.

```

$ sudo add-apt-repository ppa:tomtomtom/woeusb```

Repository: 'deb https://ppa.launchpadcontent.net/tomtomtom/woeusb/ubuntu/ jammy main'
Description:
WoeUSB is a simple tool that enable you to create your own usb stick windows installer from an iso image or a real DVD. It is a fork of Congelli501's WinUSB.
More info: https://launchpad.net/~tomtomtom/+archive/ubuntu/woeusb
Adding repository.
Press [ENTER] to continue or Ctrl-c to cancel.
Adding deb entry to /etc/apt/sources.list.d/tomtomtom-ubuntu-woeusb-jammy.list
Adding disabled deb-src entry to /etc/apt/sources.list.d/tomtomtom-ubuntu-woeusb-jammy.list
Adding key to /etc/apt/trusted.gpg.d/tomtomtom-ubuntu-woeusb.gpg with fingerprint CEC312CC5ED8215A6E0EFC49B90E9186F0E836FB
Hit:1 http://archive.ubuntu.com/ubuntu focal InRelease
Hit:2 http://archive.canonical.com/ubuntu focal InRelease
Get:3 http://archive.ubuntu.com/ubuntu focal-updates InRelease [114 kB]
Get:4 http://archive.ubuntu.com/ubuntu focal-security InRelease [114 kB]
Get:5 http://archive.ubuntu.com/ubuntu focal-backports InRelease [108 kB]
Ign:6 https://ppa.launchpadcontent.net/alexlarsson/flatpak/ubuntu jammy InRelease
Get:7 https://ppa.launchpadcontent.net/tomtomtom/woeusb/ubuntu jammy InRelease [18.0 kB]        
Err:8 https://ppa.launchpadcontent.net/alexlarsson/flatpak/ubuntu jammy Release                 
  404  Not Found [IP: 91.189.95.85 443]
Get:9 https://ppa.launchpadcontent.net/tomtomtom/woeusb/ubuntu jammy/main amd64 Packages [608 B]
Get:10 https://ppa.launchpadcontent.net/tomtomtom/woeusb/ubuntu jammy/main Translation-en [208 B]
Reading package lists... Done                                                                   
E: The repository 'https://ppa.launchpadcontent.net/alexlarsson/flatpak/ubuntu jammy Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.

```

$ sudo apt install flatpak```

Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libgdk-pixbuf-2.0-0 : Breaks: libgdk-pixbuf2.0-0 (< 2.40.0+dfsg-6~) but 2.40.0+dfsg-3ubuntu0.2 is to be installed
 libgdk-pixbuf2.0-0 : Depends: libgdk-pixbuf2.0-common (= 2.40.0+dfsg-3ubuntu0.2) but 2.42.8+dfsg-1 is to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.

```

---

### Post by Dennis N on 2022-04-24
Sometime after post #12, you did something to reinstall libgdk-pixbuf2.0-0. You have some focal (20.04) repositories enabled. These may have been enabled when adding the tomtomtom PPA?

You might have installed some package from the tomtomtom PPA that installs libgdk-pixbuf2.0-0 as a dependency taking it from the focal repositories, and you get a conflicting package with Ubuntu 2204 packages. If so, you can't use this PPA now. It's faulty. Note also these PPA packages are old, dating to Nov 2021.

Also, AlexLarsson's PPA is not maintained (as someone previously mentioned). It has nothing to offer. Use apt to install the flatpak package - it's the latest version.

I think a fresh install may be best to clean all this up. Or (not recommended) you could try and remove the offending package, and see if that helps. Also remove the focal repositories from the sources. You may still have some other focal packages that remain installed which may cause problems eventually and they could be hard to find and remove.  

I stopped using PPAs some time ago. If I want something more recent, I go with Flatpak.

---

### Post by satimis on 2022-04-24
> **Dennis N said:**
> Sometime after post #12, you did something to reinstall libgdk-pixbuf2.0-0. You have some focal (20.04) repositories enabled. These may have been enabled when adding the tomtomtom PPA?

You might have installed some package from the tomtomtom PPA that installs libgdk-pixbuf2.0-0 as a dependency taking it from the focal repositories, and you get a conflicting package with Ubuntu 2204 packages. If so, you can't use this PPA now. It's faulty. Note also these PPA packages are old, dating to Nov 2021.

Also, AlexLarsson's PPA is not maintained (as someone previously mentioned). It has nothing to offer. Use apt to install the flatpak package - it's the latest version.

I think a fresh install may be best to clean all this up. Or (not recommended) you could try and remove the offending package, and see if that helps. Also remove the focal repositories from the sources. You may still have some other focal packages that remain installed which may cause problems eventually and they could be hard to find and remove.  
This VM, in this test, was cloned on a "Fresh Installed" Ubuntu 22.04 VM which after installation I never did any on it.  Then for any test I only did it on its cloned VM.

> 
I stopped using PPAs some time ago. If I want something more recent, I go with Flatpak.
Unfortunately I couldn't install Flatpak on Ubuntu 22.04.

$ apt policy flatpak```

flatpak:
  Installed: (none)
  Candidate: 1.6.5-0ubuntu0.4
  Version table:
     1.6.5-0ubuntu0.4 500
        500 http://archive.ubuntu.com/ubuntu focal-updates/universe amd64 Packages
        500 http://archive.ubuntu.com/ubuntu focal-security/universe amd64 Packages
     1.6.3-1 500
        500 http://archive.ubuntu.com/ubuntu focal/universe amd64 Packages

```

Regards

---

### Post by Dennis N on 2022-04-25
You have some repositories that are set to focal (20.04) instead of jammy (22.04). We can see this from post #16, where you posted: 
> Unfortunately I couldn't install Flatpak on Ubuntu 22.04.
```
$ apt policy flatpak
Code:

flatpak:
  Installed: (none)
  Candidate: 1.6.5-0ubuntu0.4
  Version table:
     1.6.5-0ubuntu0.4 500
        500 http://archive.ubuntu.com/ubuntu focal-updates/universe amd64 Packages
        500 http://archive.ubuntu.com/ubuntu focal-security/universe amd64 Packages
     1.6.3-1 500
        500 http://archive.ubuntu.com/ubuntu focal/universe amd64 Packages

```
Regards 


On 22.04, you should get this version offered:
```
dmn@Tyana-vm:~$ apt policy flatpak
flatpak:
  Installed: 1.12.7-1
  Candidate: 1.12.7-1
  Version table:
 *** 1.12.7-1 500
        500 http://mirror.arizona.edu/ubuntu jammy/universe amd64 Packages
        100 /var/lib/dpkg/status

```
The similar thing is seen in post #12 where libgdk-pixbuf2.0-0 is sourced to a focal repository. You get an old version when this is installed, causing a conflict.

Also in post #12 I notice something weird (to me at least):
```
libgdk-pixbuf-2.0-0:
  Installed: 2.42.8+dfsg-1
  Candidate: 2.42.8+dfsg-1
  Version table:
 *** 2.42.8+dfsg-1 100
        100 /var/lib/dpkg/status

```
There is no repository given for the source of this, but instead a folder on your local machine. I've never seen this before.

You also said:
> This VM, in this test, was cloned on a "Fresh Installed" Ubuntu 22.04 VM which after installation I never did any on it
This makes it a mystery to me how your 22.04 could contain 20.04 repos. Maybe you did some activity on the original before cloning and forgot?

---

### Post by satimis on 2022-04-25
> **Dennis N said:**
>  - snip -
You also said:

This makes it a mystery to me how your 22.04 could contain 20.04 repos. Maybe you did some activity on the original before cloning and forgot?
No.

This is my usual operation maintained for > 10 years.

I'm running both Oracle VirtualBox as well as KVM/QEMU here.  Also I'm running Ubuntu/Fedora/Debian/Gentoo/LinuxMint/Win10/Win11 etc here.

1. In respect of Linux OS (Gentoo is btw Linux and BSD), first I'll download the latest ISO, eg Ubuntu22.04 desktop ISO
2. After verifying sha256sum of Ubuntu22.04 desktop ISO, I'll create an Ubuntu22.04 VM of VirtualBox
3. After having full config Ubuntu22.04 desktop VM, including update and upgrade of software as well as adding Guest Addition, I won't touch this original VM
4. I'll clone new VMs on these original VMs and all tests will be performed on the cloned VMs
5. For new tests to be performed on Ubuntu22.04 desktop, I'll clone a new Ubuntu22.04 desktop VM.
6. For further tests to be performed on the Ubuntu22.04 VM mentioned on pt. 5 above I'll clone another new VM on it.
7. If anything wrong on the further tests I just delete the new VM.  Its original VM remains untouched.

I found this arrangement is very efficient to me.

Just received a reply from github.com saying that their PPAs do not currently support Ubuntu 22.04.

I'll download another new Ubuntu 22.04 desktop ISO next week (May 2022) and try again.

Just found Ubuntu 22.04 VM supporting 16-core AMD CPU.  This is very interesting to me.  I'm considering purchase an AMD 7000x CPU for my new PC.

---

### Post by Dennis N on 2022-04-25
I have used the "clone and update" procedure on my VMs since 20.04, moving to each short term release. I decided to do a new install for 22.04 to get a better feel for the changes free of any past customizations. I hope you can discover what caused your repository problem as it is almost certainly the cause of all the difficulty. Let us know if you do. There is a cause - after a new install has been completed, Ubuntu does not add and switch on old repositories by itself. I wonder if your adding the PPA could possibly add Ubuntu 20.04 repositories when installing one of its .deb files and the owner assumed it would all be ok. His jammy release files are dated Nov 2021, long before it's finalization and release. I don't know the answer.

Another question: If you had the jammy repos, then why is the jammy version of flatpak not available? Only an old version is shown as a candidate.

---

### Post by satimis on 2022-04-26
Hi all,

Today

-> Activities -> Software update
It works

Remark:
There was no software update and upgrade after the installation of Ubuntu 22.04 desktop VM until today.

After finish, reboot Ubuntu 22.04 desktop VM.

Install applications from software center or the web
-> Activities -> Software Center
to start the Software Center
(pls refers to screenshot)

Now I can install Flatpak on repo

$ apt policy flatpak```

flatpak:
  Installed: 1.12.7-1
  Candidate: 1.12.7-1
  Version table:
 *** 1.12.7-1 500
        500 [http://hk.archive.ubuntu.com/ubuntu](http://hk.archive.ubuntu.com/ubuntu) jammy/universe amd64 Packages
        100 /var/lib/dpkg/status

```
      
But I couldn't install Openshot running Flatpak
$ flatpak info org.openshot.OpenShot```

error: org.openshot.OpenShot/*unspecified*/*unspecified* not installed

```

Neither I find Openshot on Ubuntu 22.04 repo
$ apt-cache policy openshot```

openshot:
  Installed: (none)
  Candidate: (none)
  Version table:

```

$ sudo apt install openshot-qt:
install Openshot

$ apt-cache policy openshot-qt```

openshot-qt:
  Installed: 2.5.1+dfsg1-2
  Candidate: 2.5.1+dfsg1-2
  Version table:
 *** 2.5.1+dfsg1-2 500
        500 http://hk.archive.ubuntu.com/ubuntu jammy/universe amd64 Packages
        500 http://hk.archive.ubuntu.com/ubuntu jammy/universe i386 Packages
        100 /var/lib/dpkg/status

```
But I couldn't start Openshot.  It is found on ->Activities

---

### Post by Dennis N on 2022-04-26
**flatpak info org.openshot.OpenShot** 
**info** only works with installed flatpaks.

If you want information on uninstalled flatpak packages, use **remote-info** with the name of the remote (flathub). 'remote' is flatpak's term for repository.
**flatpak remote-info flathub org.openshot.OpenShot**

---

### Post by Dennis N on 2022-04-26
> But I couldn't start Openshot. It is found on ->Activities 
What happens exactly when you start it? Did you try starting from the terminal? The terminal often offers helpful error messages.

I would give it a look, but I don't want to install the repository (.deb) version on this new Ubuntu 22.04 virtual machine. It installs too many _individual_ packages (164), and is too big (1.2G).
```
dmn@Tyana-vm:~$ sudo apt install openshot-qt
[omitting detailed list of packages]
0 upgraded, **164 newly installed**, 0 to remove and 0 not upgraded.
Need to get 310 MB of archives.
After this operation, **1,260 MB of additional disk space will be used**.
Do you want to continue? [Y/n] n
Abort

```
Also, installing the Flatpak instead would not match your package version - version 2.6.1 versus 2.5.1+dfsg1-2
Sorry.

---

### Post by satimis on 2022-04-27
> **Dennis N said:**
> What happens exactly when you start it? Did you try starting from the terminal? The terminal often offers helpful error messages.

Clicking Openshot icon without response.  Its icon can be added on Favorites

On Terminal
=======
$ sudo /usr/bin/openshot-qt 
Or
$ /usr/bin/openshot-qt ```

....
....
ZmqLogger::Connection - Error binding to tcp://*:5556. Switching to an available port.
         app:INFO Setting font to Cantarell
ZmqLogger::Connection - Error binding to tcp://*:5556. Switching to an available port.
         app:INFO Setting custom dark theme
logger_libopenshot:INFO Connecting to libopenshot with debug port: 5556
QMainWindow::addDockWidget: invalid 'area' argument
     ui_util:INFO Initializing UI for MainWindow
  exceptions:ERROR Unhandled Exception
Traceback (most recent call last):
  File "/usr/bin/openshot-qt", line 33, in <module>
    sys.exit(load_entry_point('openshot-qt==2.5.1', 'gui_scripts', 'openshot-qt')())
  File "/usr/lib/python3/dist-packages/openshot_qt/launch.py", line 97, in main
    app = OpenShotApp(argv)
  File "/usr/lib/python3/dist-packages/openshot_qt/classes/app.py", line 219, in __init__
    self.window = MainWindow(mode)
  File "/usr/lib/python3/dist-packages/openshot_qt/windows/main_window.py", line 2521, in __init__
    self.timeline = TimelineWebView(self)
  File "/usr/lib/python3/dist-packages/openshot_qt/windows/views/timeline_webview.py", line 3000, in __init__
    self.cache_renderer.setInterval(0.5 * 1000)
TypeError: setInterval(self, int): argument 1 has unexpected type 'float'
     version:INFO Found current version: {"error_rate_unstable": 0.05, "error_rate_stable": 0.16, "trans_rate_unstable": 0.001, "openshot_version": "2.6.1", "trans_rate_stable": 0.01}ages/openshot_qt/windows/main_window.py", line 2521, in __init__
    self.timeline = TimelineWebView(self)
  File "/usr/lib/python3/dist-packages/openshot_qt/windows/views/timeline_webview.py", line 3000, in __init__
    self.cache_renderer.setInterval(0.5 * 1000)
TypeError: setInterval(self, int): argument 1 has unexpected type 'float'
     version:INFO Found current version: {"error_rate_unstable": 0.05, "error_rate_stable": 0.16, "trans_rate_unstable": 0.001, "openshot_version": "2.6.1", "trans_rate_stable": 0.01}

(hanging here)

```

$ flatpak install flathub org.openshot.OpenShot```


Note that the directories 

'/var/lib/flatpak/exports/share'
'/home/satimis/.local/share/flatpak/exports/share'

are not in the search path set by the XDG_DATA_DIRS environment variable, so
applications installed by Flatpak may not appear on your desktop until the
session is restarted.

Looking for matches…
error: No remote refs found similar to ‘flathub’

```

Regards

---

### Post by Dennis N on 2022-04-27
```
Looking for matches&#8230;
error: No remote refs found similar to &#8216;flathub&#8217;
```

Check that the flathub remote has been enabled with the command below. You should get the same output. If there is no output, then it isn't enabled yet. 
```
[dmn@Sydney ~]$ flatpak remotes
Name    Options
flathub system

```
If it isn't enabled, enable the flathub repository with the following terminal command:
```
flatpak remote-add --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo
```
Restart your computer, then try the install command again.

The error messages shown are too complex for me to understand. Sorry. Something is clearly wrong, however.

---

### Post by satimis on 2022-04-27
> **Dennis N said:**
> ```
Looking for matches&#8230;
error: No remote refs found similar to &#8216;flathub&#8217;
```

Check that the flathub remote has been enabled with the command below. You should get the same output. If there is no output, then it isn't enabled yet. 
```
[dmn@Sydney ~]$ flatpak remotes
Name    Options
flathub system

```
If it isn't enabled, enable the flathub repository with the following terminal command:
```
flatpak remote-add --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo
```
Restart your computer, then try the install command again.

The error messages shown are too complex for me to understand. Sorry. Something is clearly wrong, however.
Performed following steps on Terminal;

$ flatpak remotes
No output

$ flatpak remote-add --if-not-exists flathub [https://flathub.org/repo/flathub.flatpakrepo](https://flathub.org/repo/flathub.flatpakrepo)
Login
No complaint

Still couldn't start openshot-qt on Terminal with the same error.  Reboot is without effect.

Do I need to delete openshot-qt first before running flatpak to install openshot?

I suppose it would be better waiting for another week, download a new Ubuntu 22.04 desktop ISO and try again ?

Regards

---

### Post by deadflowr on 2022-04-27
> Do I need to delete openshot-qt first before running flatpak to install openshot?
No,you do not NEED to delete it, flatpak does not care about anything on the system that is not about flatpaks.
However, you might WANT to delete it because of duplication confusion.
Having two versions, one from (presumably) apt and one from flatpak, can/will result in having two versions show in the menu with the same name.

---

### Post by satimis on 2022-04-27
> **deadflowr said:**
> No,you do not NEED to delete it, flatpak does not care about anything on the system that is not about flatpaks.
However, you might WANT to delete it because of duplication confusion.
Having two versions, one from (presumably) apt and one from flatpak, can/will result in having two versions show in the menu with the same name.
Thanks for your advice.

Performed following steps

On Terminal;
$ flatpak install flathub org.openshot.OpenShot
Installation went through without complaint

$ flatpak run org.openshot.OpenShot
Openshot video editor starts

Again on Terminal run;
$ sudo apt remove --autoremove openshot-qt

Done

Regards

---

### Post by Dennis N on 2022-04-27
```
$ flatpak remote-add --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo
Login
No complaint

Still couldn't start openshot-qt on Terminal with the same error. Reboot is without effect.

```
After adding the remote, you still have to install Openshot. If you just repeat the same command in the terminal (openshot-qt) as before, you are starting the .deb version again, and of course you would get the same errors.

Normally you start a Flatpak application from it's icon, not the terminal. If you wanted to start from the terminal for some reason, there is a special Flatpak command to do it. 

But, in the end, it sounds like you finally succeeded! Congrats.

---

### Post by satimis on 2022-04-28
> **Dennis N said:**
> ```
$ flatpak remote-add --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo
Login
No complaint

Still couldn't start openshot-qt on Terminal with the same error. Reboot is without effect.

```
After adding the remote, you still have to install Openshot. If you just repeat the same command in the terminal (openshot-qt) as before, you are starting the .deb version again, and of course you would get the same errors.

Normally you start a Flatpak application from it's icon, not the terminal. If you wanted to start from the terminal for some reason, there is a special Flatpak command to do it. 

But, in the end, it sounds like you finally succeeded! Congrats.
Thanks for your advice.

I can start Openshot by clicking its icon without problem, not on Terminal.  Also I have already uninstalled openshot-qt.

On Terminal running;
$ sudo apt update ```

.....
404  Not Found [IP: 91.189.95.85 443]
Get:15 http://hk.archive.ubuntu.com/ubuntu jammy-updates/main Translation-en [13.0 kB]
Get:16 http://hk.archive.ubuntu.com/ubuntu jammy-updates/main amd64 DEP-11 Metadata [6,640 B]
Get:17 http://hk.archive.ubuntu.com/ubuntu jammy-updates/main amd64 c-n-f Metadata [800 B]
Get:18 http://hk.archive.ubuntu.com/ubuntu jammy-updates/restricted amd64 Packages [50.4 kB]
Get:19 http://hk.archive.ubuntu.com/ubuntu jammy-updates/restricted Translation-en [8,232 B]
Get:20 http://hk.archive.ubuntu.com/ubuntu jammy-updates/universe amd64 Packages [13.6 kB]
Get:21 http://hk.archive.ubuntu.com/ubuntu jammy-updates/universe i386 Packages [10.6 kB]
Get:22 http://hk.archive.ubuntu.com/ubuntu jammy-updates/universe amd64 DEP-11 Metadata [19.2 kB]
Reading package lists... Done                                     
E: The repository 'https://ppa.launchpadcontent.net/openshot.developers/ppa/ubuntu jammy Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.

```

Disregarding this warning and running;

$ sudo apt upgrade```

Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  snapd
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 21.5 MB of archives.
After this operation, 13.3 kB of additional disk space will be used.
Do you want to continue? [Y/n] 

```

Type Y to continue```

....
Fetched 21.5 MB in 4s (5,005 kB/s)
(Reading database ... 206552 files and directories currently installed.)
Preparing to unpack .../snapd_2.55.3+22.04ubuntu1_amd64.deb ...
Warning: Stopping snapd.service, but it can still be activated by:
  snapd.socket
Unpacking snapd (2.55.3+22.04ubuntu1) over (2.55.3+22.04) ...
Setting up snapd (2.55.3+22.04ubuntu1) ...
snapd.failure.service is a disabled or a static unit not running, not starting it.
snapd.snap-repair.service is a disabled or a static unit not running, not starting it.
Processing triggers for gnome-menus (3.36.0-1ubuntu3) ...
Processing triggers for man-db (2.10.2-1) ...
Processing triggers for dbus (1.12.20-2ubuntu4) ...
Processing triggers for mailcap (3.70+nmu1ubuntu1) ...
Processing triggers for desktop-file-utils (0.26-1ubuntu3) ...

```

Upgrade works without problem.

Reboot and try again;
$ sudo apt update```

Hit:1 http://hk.archive.ubuntu.com/ubuntu jammy InRelease
Hit:2 http://hk.archive.ubuntu.com/ubuntu jammy-updates InRelease
Hit:3 http://hk.archive.ubuntu.com/ubuntu jammy-backports InRelease            
Ign:4 https://ppa.launchpadcontent.net/openshot.developers/ppa/ubuntu jammy InRelease
Err:5 https://ppa.launchpadcontent.net/openshot.developers/ppa/ubuntu jammy Release
  404  Not Found [IP: 91.189.95.85 443]
Hit:6 http://security.ubuntu.com/ubuntu jammy-security InRelease
Reading package lists... Done
E: The repository 'https://ppa.launchpadcontent.net/openshot.developers/ppa/ubuntu jammy Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.

```

The warning still popup

Again;
$ sudo apt upgrade```

Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

The original Ubuntu 22.04 desktop VM doesn't have this problem, without warning.  It looks quite funny to me.

Next week I'll download another Ubuntu 22.04 desktop ISO and try again on both VM and bare-metal SSD

Regards

[B][COLOR="#FF0000"]Edit
===[/COLOR][/B]
Notepad-plus-plus is a very nice notepad

Run following command on Terminal to install it```

flatpak install com.notepadqq.Notepadqq

flatpak run com.notepadqq.Notepadqq

```

---

### Post by Dennis N on 2022-04-28
```
E: The repository 'https://ppa.launchpadcontent.net/openshot.developers/ppa/ubuntu jammy Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
```
Since you are using Openshot Flatpak, you don't need the Openshot PPA. Disable or remove it using "Software & Upadates" Tool > Other Software Tab, and unckeck this PPA to disable, or just remove it with the "Remove" button at the bottom. Then the error will go away.

---

### Post by satimis on 2022-04-28
> **Dennis N said:**
> ```
E: The repository 'https://ppa.launchpadcontent.net/openshot.developers/ppa/ubuntu jammy Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
```
Since you are using Openshot Flatpak, you don't need the Openshot PPA. Disable or remove it using "Software & Upadates" Tool > Other Software Tab, and unckeck this PPA to disable, or just remove it with the "Remove" button at the bottom. Then the error will go away.
There are 2 ppa.  Pls refers to screenshot

Uncheck both -> Close

The warning gone.  Thanks

Regards

---

