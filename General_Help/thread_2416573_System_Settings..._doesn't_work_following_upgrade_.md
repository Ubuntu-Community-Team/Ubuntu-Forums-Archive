---
title: "System Settings... doesn't work following upgrade to 16.04"
date: 2019-04-11
forum: General Help
---

### Post by RegUB on 2019-04-11
After upgrading 14.04 to 16.04 the System Settings option (from the drop down menu in the top right hand corner) no longer does anything. I tried the following -```
~$ sudo apt-get remove unity-control-center
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'unity-control-center' is not installed, so not removed
0 to upgrade, 0 to newly install, 0 to remove and 10 not to upgrade.

~$ sudo apt autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 to upgrade, 0 to newly install, 0 to remove and 10 not to upgrade.

~$ sudo apt-get install unity-control-center
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 unity-control-center : Depends: libcheese-gtk25 (>= 3.18.0) but it is not going to be installed
                        Depends: libcheese8 (>= 3.18.0) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```

I noticed that a lot of libcheese stuff was removed during the installation. But as far as I can tell it is something to do with webcams so I don't see how it's relevant. Any advice welcome!

---

### Post by speartip on 2019-04-12
This is one of the hazards of upgrade via fresh install, particularly when upgrading to an already older version.
See if this does anything:
```
sudo apt update && sudo apt -f install
```

---

### Post by RegUB on 2019-04-17
> **speartip said:**
> This is one of the hazards of upgrade via fresh install, particularly when upgrading to an already older version.
See if this does anything:
```
sudo apt update && sudo apt -f install
```
Sorry, only just got the chance to try this. Output below. I'm not sure what you mean by 'upgrade via fresh install' - I upgraded following a prompt from the Software Updater, which had been regularly reminding me that 16.04 was available. As 14.04 will soon be out of support I decided it was time to click the 'Upgrade' option.```
~$ sudo apt update
Hit:1 http://gb.archive.ubuntu.com/ubuntu xenial InRelease                     
Get:2 http://gb.archive.ubuntu.com/ubuntu xenial-updates InRelease [109 kB]    
Get:3 http://security.ubuntu.com/ubuntu xenial-security InRelease [109 kB]
Ign:4 http://dl.google.com/linux/chrome/deb stable InRelease        
Hit:5 http://dl.google.com/linux/chrome/deb stable Release                     
Get:6 http://gb.archive.ubuntu.com/ubuntu xenial-backports InRelease [107 kB]  
Get:8 http://security.ubuntu.com/ubuntu xenial-security/main amd64 DEP-11 Metadata [67.9 kB]
Get:9 http://security.ubuntu.com/ubuntu xenial-security/main DEP-11 64x64 Icons [67.1 kB]
Get:10 http://gb.archive.ubuntu.com/ubuntu xenial-updates/main Sources [335 kB]
Get:11 http://security.ubuntu.com/ubuntu xenial-security/universe amd64 DEP-11 Metadata [116 kB]
Get:12 http://security.ubuntu.com/ubuntu xenial-security/universe DEP-11 64x64 Icons [173 kB]
Get:13 http://security.ubuntu.com/ubuntu xenial-security/multiverse amd64 DEP-11 Metadata [2,464 B]
Get:14 http://gb.archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages [938 kB]
Get:15 http://gb.archive.ubuntu.com/ubuntu xenial-updates/main i386 Packages [815 kB]
Get:16 http://gb.archive.ubuntu.com/ubuntu xenial-updates/main amd64 DEP-11 Metadata [318 kB]
Get:17 http://gb.archive.ubuntu.com/ubuntu xenial-updates/main DEP-11 64x64 Icons [225 kB]
Get:18 http://gb.archive.ubuntu.com/ubuntu xenial-updates/universe amd64 Packages [746 kB]
Get:19 http://gb.archive.ubuntu.com/ubuntu xenial-updates/universe i386 Packages [683 kB]
Get:20 http://gb.archive.ubuntu.com/ubuntu xenial-updates/universe amd64 DEP-11 Metadata [252 kB]
Get:21 http://gb.archive.ubuntu.com/ubuntu xenial-updates/universe DEP-11 64x64 Icons [350 kB]
Get:22 http://gb.archive.ubuntu.com/ubuntu xenial-updates/multiverse amd64 DEP-11 Metadata [5,968 B]
Get:23 http://gb.archive.ubuntu.com/ubuntu xenial-backports/main amd64 DEP-11 Metadata [3,324 B]
Get:24 http://gb.archive.ubuntu.com/ubuntu xenial-backports/universe amd64 DEP-11 Metadata [5,104 B]
Fetched 5,427 kB in 4s (1,166 kB/s)                                
Reading package lists... Done
Building dependency tree       
Reading state information... Done
13 packages can be upgraded. Run 'apt list --upgradable' to see them.

~$ sudo apt -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 to upgrade, 0 to newly install, 0 to remove and 13 not to upgrade.

~$ apt list --upgradable
Listing... Done
cjs/xenial 2.8.0-1 amd64 [upgradable from: 2.8.0-1~trusty0]
console-setup/xenial-updates,xenial-updates 1.108ubuntu15.5 all [upgradable from: 1.108ubuntu15.4]
console-setup-linux/xenial-updates,xenial-updates 1.108ubuntu15.5 all [upgradable from: 1.108ubuntu15.4]
gir1.2-clutter-1.0/xenial 1.24.2-1 amd64 [upgradable from: 1.16.4-0ubuntu2]
gir1.2-cogl-1.0/xenial 1.22.0-2 amd64 [upgradable from: 1.16.2-1]
gir1.2-coglpango-1.0/xenial 1.22.0-2 amd64 [upgradable from: 1.16.2-1]
gir1.2-totem-1.0/xenial 3.18.1-1ubuntu4 amd64 [upgradable from: 3.10.1-1ubuntu4]
gstreamer1.0-clutter/xenial 2.0.18-1 amd64 [upgradable from: 2.0.8-1build1]
keyboard-configuration/xenial-updates,xenial-updates 1.108ubuntu15.5 all [upgradable from: 1.108ubuntu15.4]
libclutter-1.0-0/xenial 1.24.2-1 amd64 [upgradable from: 1.16.4-0ubuntu2]
libclutter-gst-2.0-0/xenial 2.0.18-1 amd64 [upgradable from: 2.0.8-1build1]
libclutter-gtk-1.0-0/xenial 1.6.6-1 amd64 [upgradable from: 1.4.4-3ubuntu2.2]
libtotem0/xenial 3.18.1-1ubuntu4 amd64 [upgradable from: 3.10.1-1ubuntu4]

```

---

### Post by speartip on 2019-04-17
Hi RegUB...
I meant that a Fresh install is always preferable to an upgrade.
Try running:
```
sudo apt dist-upgrade
```
This will install the 13 packages that are listed.
That might solve your dependency problem.

---

### Post by RegUB on 2019-04-17
> **speartip said:**
> Hi RegUB...
I meant that a Fresh install is always preferable to an upgrade.
Ah, you meant 'upgrade _vs_ fresh install' - yes that makes sense now. I may well end up doing a fresh install, and go straight to 18.04 while I'm at it.
> 
Try running:
```
sudo apt dist-upgrade
```
This will install the 13 packages that are listed.
That might solve your dependency problem.
The above didn't help -
```
~$ sudo apt dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  cjs gir1.2-clutter-1.0 gir1.2-cogl-1.0 gir1.2-coglpango-1.0 gir1.2-totem-1.0
  gstreamer1.0-clutter libclutter-1.0-0 libclutter-gst-2.0-0
  libclutter-gtk-1.0-0 libtotem0
The following packages will be upgraded:
  console-setup console-setup-linux keyboard-configuration
3 to upgrade, 0 to newly install, 0 to remove and 10 not to upgrade.
Need to get 1,759 kB of archives.
After this operation, 3,072 B disk space will be freed.
Do you want to continue? [Y/n] Y
Get:1 http://gb.archive.ubuntu.com/ubuntu xenial-updates/main amd64 console-setup-linux all 1.108ubuntu15.5 [984 kB]
Get:2 http://gb.archive.ubuntu.com/ubuntu xenial-updates/main amd64 console-setup all 1.108ubuntu15.5 [117 kB]
Get:3 http://gb.archive.ubuntu.com/ubuntu xenial-updates/main amd64 keyboard-configuration all 1.108ubuntu15.5 [658 kB]
Fetched 1,759 kB in 1s (1,024 kB/s)             
Preconfiguring packages ...
(Reading database ... 1765734 files and directories currently installed.)
Preparing to unpack .../console-setup-linux_1.108ubuntu15.5_all.deb ...
Unpacking console-setup-linux (1.108ubuntu15.5) over (1.108ubuntu15.4) ...
Preparing to unpack .../console-setup_1.108ubuntu15.5_all.deb ...
Obsolete conffile /etc/init.d/keyboard-setup has been modified by you, renaming to .dpkg-bak
Unpacking console-setup (1.108ubuntu15.5) over (1.108ubuntu15.4) ...
Preparing to unpack .../keyboard-configuration_1.108ubuntu15.5_all.deb ...
Unpacking keyboard-configuration (1.108ubuntu15.5) over (1.108ubuntu15.4) ...
Processing triggers for ureadahead (0.100.0-19) ...
ureadahead will be reprofiled on next reboot
Processing triggers for man-db (2.7.5-1) ...
Processing triggers for systemd (229-4ubuntu21.21) ...
Setting up keyboard-configuration (1.108ubuntu15.5) ...
Your console font configuration will be updated the next time your system
boots. If you want to update it now, run 'setupcon' from a virtual console.
update-rc.d: warning: start and stop actions are no longer supported; falling back to defaults
update-initramfs: deferring update (trigger activated)
Setting up console-setup-linux (1.108ubuntu15.5) ...
Installing new version of config file /etc/console-setup/compose.ISO-8859-1.inc ...
Installing new version of config file /etc/console-setup/compose.ISO-8859-13.inc ...
Installing new version of config file /etc/console-setup/compose.ISO-8859-14.inc ...
Installing new version of config file /etc/console-setup/compose.ISO-8859-15.inc ...
Installing new version of config file /etc/console-setup/compose.ISO-8859-2.inc ...
Installing new version of config file /etc/console-setup/compose.ISO-8859-3.inc ...
Installing new version of config file /etc/console-setup/compose.ISO-8859-4.inc ...
Installing new version of config file /etc/console-setup/compose.ISO-8859-7.inc ...
Installing new version of config file /etc/console-setup/compose.ISO-8859-9.inc ...
Setting up console-setup (1.108ubuntu15.5) ...
Your console font configuration will be updated the next time your system
boots. If you want to update it now, run 'setupcon' from a virtual console.
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools (0.122ubuntu8.14) ...
update-initramfs: Generating /boot/initrd.img-4.4.0-145-generic


```
After this I tried installing unity again but still got the libcheese messages.

---

### Post by speartip on 2019-04-18
If it doesn't cause you too many problems, I would do a fresh install of 18.04. Although remember that Unity is not the default Desktop Environment any more, so you might want to experiment with other DEs.

---

