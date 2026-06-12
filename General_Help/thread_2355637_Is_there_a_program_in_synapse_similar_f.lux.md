---
title: "Is there a program in synapse similar f.lux"
date: 2017-03-14
forum: General Help
---

### Post by Camilia on 2017-03-14
Researching computer glasses came across a website for f.lux. It helps with blue light that can harm eyes. Was wondering if there is a similar program in synapse?

---

### Post by vasa1 on 2017-03-14
> **Camilia said:**
> Researching computer glasses came across a website for f.lux. It helps with blue light that can harm eyes. Was wondering if there is a similar program in **synapse**?Do you mean "Synaptic Package Manager"?

F.lux seems to be available via ppa: [https://launchpad.net/~nathan-renniewaldock/+archive/ubuntu/flux](https://launchpad.net/~nathan-renniewaldock/+archive/ubuntu/flux).

Once you install the ppa, you should be able to install f.lux using Synaptic Package Manager.

---

### Post by Camilia on 2017-03-14
> **vasa1 said:**
> Do you mean "Synaptic Package Manager"?

F.lux seems to be available via ppa: [https://launchpad.net/~nathan-renniewaldock/+archive/ubuntu/flux](https://launchpad.net/~nathan-renniewaldock/+archive/ubuntu/flux).

Once you install the ppa, you should be able to install f.lux using Synaptic Package Manager.
Yes I meant Synaptic Package Manager. Is ppa at the link you provided? How do I figure which 1 will work with my PC? I have ubuntu  16.04.

I went to the link and got totally confused. 

Went to ubuntu software and found redshift. It adjusts the color temperature of your screen according to your surroundings.

---

### Post by vasa1 on 2017-03-14
Yes.

I don't use it myself. What do you mean by "which 1"?

---

### Post by howefield on 2017-03-15
> **Camilia said:**
>  How do I figure which 1 will work with my PC? I have ubuntu  16.04.

Using these commands should put the correct repository (xenial) information into your system automatically.

```
sudo add-apt-repository ppa:nathan-renniewaldock/flux
```
```
sudo apt-get update
```

and then to install it, use

```
sudo apt install fluxgui
```

Then search the dash for fluxgui

[ATTACH=CONFIG]274153[/ATTACH]

The output in terminal will look something like this...

```
sudo add-apt-repository ppa:nathan-renniewaldock/flux
[sudo] password for hugh: 
 GUI for f.lux
https://justgetflux.com/

Bugs/feature requests should be directed to: https://github.com/xflux-gui/xflux-gui
I do not develop this, only provide a PPA.
 More info: https://launchpad.net/~nathan-renniewaldock/+archive/ubuntu/flux
Press [ENTER] to continue or ctrl-c to cancel adding it

gpg: keybox '/tmp/tmp52pf95oy/pubring.gpg' created
gpg: /tmp/tmp52pf95oy/trustdb.gpg: trustdb created
gpg: key 4CDB129629A4B41A: public key "Launchpad PPA for Nathan Rennie-Waldock" imported
gpg: Total number processed: 1
gpg:               imported: 1
OK
```

```
sudo apt update
Get:1 http://ppa.launchpad.net/nathan-renniewaldock/flux/ubuntu zesty InRelease [17.5 kB]
Hit:2 http://security.ubuntu.com/ubuntu zesty-security InRelease                                                                           
Get:3 http://gb.archive.ubuntu.com/ubuntu zesty InRelease [256 kB]                             
Hit:4 http://archive.canonical.com/ubuntu zesty InRelease                          
Hit:5 http://gb.archive.ubuntu.com/ubuntu zesty-updates InRelease                  
Hit:6 http://gb.archive.ubuntu.com/ubuntu zesty-backports InRelease     
Get:7 http://ppa.launchpad.net/nathan-renniewaldock/flux/ubuntu zesty/main amd64 Packages [540 B]
Get:8 http://ppa.launchpad.net/nathan-renniewaldock/flux/ubuntu zesty/main i386 Packages [540 B]
Get:9 http://ppa.launchpad.net/nathan-renniewaldock/flux/ubuntu zesty/main Translation-en [276 B]
Get:10 http://gb.archive.ubuntu.com/ubuntu zesty/main i386 Packages [1,216 kB]
Get:11 http://gb.archive.ubuntu.com/ubuntu zesty/main amd64 Packages [1,220 kB]
Get:12 http://gb.archive.ubuntu.com/ubuntu zesty/main Translation-en [584 kB]
Get:13 http://gb.archive.ubuntu.com/ubuntu zesty/main amd64 DEP-11 Metadata [531 kB]
Get:14 http://gb.archive.ubuntu.com/ubuntu zesty/universe i386 Packages [8,038 kB]
Get:15 http://gb.archive.ubuntu.com/ubuntu zesty/universe amd64 Packages [8,068 kB]
Get:16 http://gb.archive.ubuntu.com/ubuntu zesty/universe Translation-en [4,678 kB]                                                        
Get:17 http://gb.archive.ubuntu.com/ubuntu zesty/universe amd64 DEP-11 Metadata [2,707 kB]                                                 
Get:18 http://gb.archive.ubuntu.com/ubuntu zesty/multiverse i386 Packages [151 kB]                                                         
Get:19 http://gb.archive.ubuntu.com/ubuntu zesty/multiverse amd64 Packages [158 kB]                                                        
Get:20 http://gb.archive.ubuntu.com/ubuntu zesty/multiverse amd64 DEP-11 Metadata [44.4 kB]                                                
Fetched 27.7 MB in 10s (2,682 kB/s)                                                                                                        
Reading package lists... Done
Building dependency tree       
Reading state information... Done
18 packages can be upgraded. Run 'apt list --upgradable' to see them.
```

```
sudo apt install fluxgui
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  libglade2-0 python-gconf python-glade2 python-pexpect python-ptyprocess python-xdg
Suggested packages:
  python-gnome2-doc python-gtk2-doc python-pexpect-doc
The following NEW packages will be installed
  fluxgui libglade2-0 python-gconf python-glade2 python-pexpect python-ptyprocess python-xdg
0 to upgrade, 7 to newly install, 0 to remove and 18 not to upgrade.
Need to get 178 kB of archives.
After this operation, 935 kB of additional disk space will be used.
Do you want to continue? [Y/n] 
Get:1 http://gb.archive.ubuntu.com/ubuntu zesty/main amd64 libglade2-0 amd64 1:2.6.4-2 [44.6 kB]
Get:2 http://ppa.launchpad.net/nathan-renniewaldock/flux/ubuntu zesty/main amd64 fluxgui all 1.1.10~pre~20170224-gb71f794-1~zesty [15.9 kB]
Get:3 http://gb.archive.ubuntu.com/ubuntu zesty/main amd64 python-glade2 amd64 2.24.0-5.1ubuntu1 [9,012 B]
Get:4 http://gb.archive.ubuntu.com/ubuntu zesty/universe amd64 python-gconf amd64 2.28.1+dfsg-1.2 [22.5 kB]
Get:5 http://gb.archive.ubuntu.com/ubuntu zesty/universe amd64 python-xdg all 0.25-4 [31.4 kB]
Get:6 http://gb.archive.ubuntu.com/ubuntu zesty/universe amd64 python-ptyprocess all 0.5.1-1 [12.6 kB]
Get:7 http://gb.archive.ubuntu.com/ubuntu zesty/universe amd64 python-pexpect all 4.2.1-1 [41.7 kB]
Fetched 178 kB in 0s (430 kB/s)           
Selecting previously unselected package libglade2-0:amd64.
(Reading database ... 182650 files and directories currently installed.)
Preparing to unpack .../0-libglade2-0_1%3a2.6.4-2_amd64.deb ...
Unpacking libglade2-0:amd64 (1:2.6.4-2) ...
Selecting previously unselected package python-glade2.
Preparing to unpack .../1-python-glade2_2.24.0-5.1ubuntu1_amd64.deb ...
Unpacking python-glade2 (2.24.0-5.1ubuntu1) ...
Selecting previously unselected package python-gconf.
Preparing to unpack .../2-python-gconf_2.28.1+dfsg-1.2_amd64.deb ...
Unpacking python-gconf (2.28.1+dfsg-1.2) ...
Selecting previously unselected package python-xdg.
Preparing to unpack .../3-python-xdg_0.25-4_all.deb ...
Unpacking python-xdg (0.25-4) ...
Selecting previously unselected package python-ptyprocess.
Preparing to unpack .../4-python-ptyprocess_0.5.1-1_all.deb ...
Unpacking python-ptyprocess (0.5.1-1) ...
Selecting previously unselected package python-pexpect.
Preparing to unpack .../5-python-pexpect_4.2.1-1_all.deb ...
Unpacking python-pexpect (4.2.1-1) ...
Selecting previously unselected package fluxgui.
Preparing to unpack .../6-fluxgui_1.1.10~pre~20170224-gb71f794-1~zesty_all.deb ...
Unpacking fluxgui (1.1.10~pre~20170224-gb71f794-1~zesty) ...
Setting up python-gconf (2.28.1+dfsg-1.2) ...
Processing triggers for mime-support (3.60ubuntu1) ...
Processing triggers for desktop-file-utils (0.23-1ubuntu2) ...
Processing triggers for sgml-base (1.29) ...
Processing triggers for bamfdaemon (0.5.3+16.10.20160929-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Setting up libglade2-0:amd64 (1:2.6.4-2) ...
Setting up python-ptyprocess (0.5.1-1) ...
Setting up python-glade2 (2.24.0-5.1ubuntu1) ...
Processing triggers for gnome-menus (3.13.3-6ubuntu5) ...
Processing triggers for hicolor-icon-theme (0.15-1) ...
Setting up python-xdg (0.25-4) ...
Setting up python-pexpect (4.2.1-1) ...
Setting up fluxgui (1.1.10~pre~20170224-gb71f794-1~zesty) ...

Downloading xflux...
--2017-03-15 10:06:17--  https://justgetflux.com/linux/xflux64.tgz
Resolving justgetflux.com (justgetflux.com)... 216.176.200.22
Connecting to justgetflux.com (justgetflux.com)|216.176.200.22|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 339845 (332K) [application/octet-stream]
Saving to: &#8216;xflux64.tgz&#8217;

xflux64.tgz                        100%[================================================================>] 331.88K   614KB/s    in 0.5s    

2017-03-15 10:06:19 (614 KB/s) - &#8216;xflux64.tgz&#8217; saved [339845/339845]

Download done.

Adding 'diversion of /usr/bin/xflux to /usr/bin/xflux.distrib by fluxgui'
Processing triggers for libc-bin (2.24-7ubuntu2) ...
```

Obviously, it would be much easier to try out redshift which is already in the Ubuntu repositories :)

---

### Post by lysander6662 on 2017-03-15
Depending on your hardware you may find Redshift doesn't work properly with your system. By all means give it a go. If not, then howefield's advice is the way forward.

---

### Post by Camilia on 2017-03-15
> **howefield said:**
> Using these commands should put the correct repository (xenial) information into your system automatically.

```
sudo add-apt-repository ppa:nathan-renniewaldock/flux
```
```
sudo apt-get update
```

and then to install it, use

```
sudo apt install fluxgui
```

Then search the dash for fluxgui

Thank you for the codes. I got it installed. The color hue is more appeasing to my eyes now than when I was using Redshift

---

### Post by howefield on 2017-03-15
> **Camilia said:**
> Thank you for the codes. I got it installed. The color hue is more appeasing to my eyes now than when I was using Redshift

Cool, glad you got it installed and working and thanks for marking the thread as solved.

---

