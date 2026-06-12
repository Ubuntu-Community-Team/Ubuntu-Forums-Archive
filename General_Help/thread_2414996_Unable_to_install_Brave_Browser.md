---
title: "Unable to install Brave Browser"
date: 2019-03-18
forum: General Help
---

### Post by richyg on 2019-03-18
Linux noob here. Following instructions from [the official page]("https://brave-browser.readthedocs.io/en/latest/installing-brave.html#linux") ends in an error at the last command.

See log below:
```
richard@richard-pc:~$ curl -s https://brave-browser-apt-release.s3.brave.com/brave-core.asc | sudo apt-key --keyring /etc/apt/trusted.gpg.d/brave-browser-release.gpg add
[sudo] password for richard: 
Command 'curl' not found, but can be installed with:

sudo apt install curl

gpg: no valid OpenPGP data found.
richard@richard-pc:~$ sudo apt install curl
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed
  curl
0 to upgrade, 1 to newly install, 0 to remove and 41 not to upgrade.
Need to get 166 kB of archives.
After this operation, 403 kB of additional disk space will be used.
Get:1 http://archive.ubuntu.com/ubuntu cosmic-updates/main i386 curl i386 7.61.0-1ubuntu2.3 [166 kB]
Fetched 166 kB in 0s (541 kB/s)
Selecting previously unselected package curl.
(Reading database ... 283179 files and directories currently installed.)
Preparing to unpack .../curl_7.61.0-1ubuntu2.3_i386.deb ...
Unpacking curl (7.61.0-1ubuntu2.3) ...
Setting up curl (7.61.0-1ubuntu2.3) ...
Processing triggers for man-db (2.8.4-2) ...
richard@richard-pc:~$ curl -s https://brave-browser-apt-release.s3.brave.com/brave-core.asc | sudo apt-key --keyring /etc/apt/trusted.gpg.d/brave-browser-release.gpg add
OK
richard@richard-pc:~$ source /etc/os-release
richard@richard-pc:~$ echo "deb [arch=amd64] https://brave-browser-apt-release.s3.brave.com/ $UBUNTU_CODENAME main" | sudo tee /etc/apt/sources.list.d/brave-browser-release-${UBUNTU_CODENAME}.list
deb [arch=amd64] https://brave-browser-apt-release.s3.brave.com/ cosmic main
richard@richard-pc:~$ sudo apt update
Hit:1 http://archive.ubuntu.com/ubuntu cosmic InRelease
Get:2 http://archive.ubuntu.com/ubuntu cosmic-updates InRelease [88.7 kB]                                                                   
Get:3 http://security.ubuntu.com/ubuntu cosmic-security InRelease [88.7 kB]                                                                 
Get:4 http://archive.ubuntu.com/ubuntu cosmic-backports InRelease [74.6 kB]                                                                 
Get:5 https://brave-browser-apt-release.s3.brave.com cosmic InRelease [2,825 B]                                                             
Get:6 http://archive.ubuntu.com/ubuntu cosmic-updates/main i386 Packages [213 kB]
Get:7 http://archive.ubuntu.com/ubuntu cosmic-updates/main Translation-en [99.1 kB]
Get:8 http://archive.ubuntu.com/ubuntu cosmic-updates/main i386 DEP-11 Metadata [133 kB]  
Get:9 http://archive.ubuntu.com/ubuntu cosmic-updates/main DEP-11 48x48 Icons [33.0 kB]          
Get:10 http://archive.ubuntu.com/ubuntu cosmic-updates/main DEP-11 64x64 Icons [51.8 kB] 
Get:11 http://archive.ubuntu.com/ubuntu cosmic-updates/main DEP-11 128x128 Icons [136 kB] 
Get:12 http://archive.ubuntu.com/ubuntu cosmic-updates/universe i386 Packages [234 kB]     
Get:13 http://archive.ubuntu.com/ubuntu cosmic-updates/universe Translation-en [82.1 kB]
Get:14 http://archive.ubuntu.com/ubuntu cosmic-updates/universe i386 DEP-11 Metadata [57.8 kB]
Get:15 http://archive.ubuntu.com/ubuntu cosmic-updates/universe DEP-11 48x48 Icons [32.4 kB]       
Get:16 http://archive.ubuntu.com/ubuntu cosmic-updates/universe DEP-11 64x64 Icons [59.5 kB]       
Get:17 http://archive.ubuntu.com/ubuntu cosmic-updates/universe DEP-11 128x128 Icons [117 kB]  
Get:18 http://archive.ubuntu.com/ubuntu cosmic-updates/multiverse i386 DEP-11 Metadata [2,464 B] 
Get:19 http://archive.ubuntu.com/ubuntu cosmic-backports/universe i386 DEP-11 Metadata [7,356 B]
Get:20 http://security.ubuntu.com/ubuntu cosmic-security/main i386 Packages [115 kB]           
Get:21 http://security.ubuntu.com/ubuntu cosmic-security/main Translation-en [55.5 kB]
Get:22 http://security.ubuntu.com/ubuntu cosmic-security/main i386 DEP-11 Metadata [204 B]
Get:23 http://security.ubuntu.com/ubuntu cosmic-security/universe i386 Packages [61.2 kB]
Get:24 http://security.ubuntu.com/ubuntu cosmic-security/universe Translation-en [36.7 kB]
Get:25 http://security.ubuntu.com/ubuntu cosmic-security/universe i386 DEP-11 Metadata [11.6 kB]
Get:26 http://security.ubuntu.com/ubuntu cosmic-security/universe DEP-11 48x48 Icons [7,098 B]
Get:27 http://security.ubuntu.com/ubuntu cosmic-security/universe DEP-11 64x64 Icons [17.6 kB]
Get:28 http://security.ubuntu.com/ubuntu cosmic-security/universe DEP-11 128x128 Icons [22.3 kB]
Get:29 http://security.ubuntu.com/ubuntu cosmic-security/multiverse i386 DEP-11 Metadata [2,464 B]
Get:30 https://brave-browser-apt-release.s3.brave.com cosmic/main amd64 Packages [4,901 B]       
Fetched 1,847 kB in 3s (533 kB/s)      
Reading package lists... Done
Building dependency tree       
Reading state information... Done
71 packages can be upgraded. Run 'apt list --upgradable' to see them.
richard@richard-pc:~$ sudo apt install brave-browser brave-keyring
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package brave-browser
```

Hopefully someone can advise further. Thanks in advance.

---

### Post by #&amp;thj^% on 2019-03-18
I would first get your system upgraded (Current)>>(71 packages can be upgraded.)
```
sudo apt upgrade
```
Reboot if required and next try this:
```
sudo apt install brave-keyring brave
```
Sorry i totally missed the fact that your using a 32 bit install>>>>so,  Brave web browser for Linux is only available for 64-bit architecture operating systems, so there is no 32-bit version available for your operating system.

---

