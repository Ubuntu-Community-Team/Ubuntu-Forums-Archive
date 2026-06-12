---
title: "New to Linux, error has shown up"
date: 2018-10-03
forum: General Help
---

### Post by currybt on 2018-10-03
[B]Hey all,

I am new to Ubuntu and new to Linux overall. Everything has been going well. All of a sudden, today, I noticed a red circle with a white line through it in the upper right portion of my screen. I clicked on it:[/B]

An error occurred, please run package manager from the right-click menu or apt-get in a terminal to see what is wrong. The error message was: 'Error: BrokenCount>0'. This usually means that your installed packages have unmet dependencies.

**I cannot install updates. If I try I get:**

The Package System is Broken
Check if you are using third party repositories. If so disable them, since they are a common source of problems.
Furthermore run the following command in a Terminal: apt-get install -f
Transaction failed: The package system is broken
The following packages have unmet dependencies:

linux-image-generic: Depends: linux-modules-extra-4.15.0-36-generic but it is not installed

**so, I typed into terminal :**

sudo apt-get install -f
***entered password* pressed enter**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  liblinear3 linux-headers-4.15.0-29 linux-headers-4.15.0-29-generic
  linux-image-4.15.0-29-generic linux-modules-4.15.0-29-generic
  linux-modules-extra-4.15.0-29-generic menu nmap
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  linux-modules-extra-4.15.0-36-generic
The following NEW packages will be installed:
  linux-modules-extra-4.15.0-36-generic
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0 B/32.7 MB of archives.
After this operation, 171 MB of additional disk space will be used.
Do you want to continue? [Y/n] 
** Put in Y, pressed enter**
(Reading database ... 198521 files and directories currently installed.)
Preparing to unpack .../linux-modules-extra-4.15.0-36-generic_4.15.0-36.39_amd64.deb ...
Unpacking linux-modules-extra-4.15.0-36-generic (4.15.0-36.39) ...
dpkg: error processing archive /var/cache/apt/archives/linux-modules-extra-4.15.0-36-generic_4.15.0-36.39_amd64.deb (--unpack):
 unable to open '/lib/modules/4.15.0-36-generic/kernel/drivers/net/wireless/ath/ath5k/ath5k.ko.dpkg-new': Operation not permitted
Errors were encountered while processing:
 /var/cache/apt/archives/linux-modules-extra-4.15.0-36-generic_4.15.0-36.39_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


**Now I am at a standstill, any advice?**

---

### Post by TheFu on 2018-10-03
Do you have enough storage?

Run these to see:
```
df -hT
df -i
```

BTW, it would be helpful if you always used "code tags" like I did here when posting commands and output.  Things line up in a way that we are used to seeing.  Otherwise, it is just too hard to read, at least for me.

---

