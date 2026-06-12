---
title: "Strange version of freerdp2-x11 after installation on Ubuntu 20.04.4"
date: 2023-01-28
forum: General Help
---

### Post by zak12 on 2023-01-28
Good day everyone!

I'm user of Ubuntu 20.04.4 and I have strange issue may be you can help me with this. I want to install freerdp2-x11 packet on my laptop, I check apt policy for packet freerdp2-x11:

> zak@zak:~$ apt policy freerdp2-x11
freerdp2-x11:
Installed: (none)
Candidate: 2.2.0+dfsg1-0ubuntu0.20.04.4
Version table:
2.2.0+dfsg1-0ubuntu0.20.04.4 500
500 [http://ru.archive.ubuntu.com/ubuntu](http://ru.archive.ubuntu.com/ubuntu) focal-updates/universe amd64 Packages
500 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security/universe amd64 Packages
2.0.0~git20190204.1.2693389a+dfsg1-2build2 500
500 [http://ru.archive.ubuntu.com/ubuntu](http://ru.archive.ubuntu.com/ubuntu) focal/universe amd64 Packages


I see two version of packet 2.2.0 and 2.0.0, I want to install 2.2.0+dfsg1-0ubuntu0.20.04.4.

> zak@zak:~$ sudo apt install freerdp2-x11=2.2.0+dfsg1-0ubuntu0.20.04.4
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following NEW packages will be installed:
freerdp2-x11
0 upgraded, 1 newly installed, 0 to remove and 5 not upgraded.
Need to get 262 kB of archives.
After this operation, 1&#8239;370 kB of additional disk space will be used.
Get:1 [http://ru.archive.ubuntu.com/ubuntu](http://ru.archive.ubuntu.com/ubuntu) focal-updates/universe amd64 freerdp2-x11 amd64 2.2.0+dfsg1-0ubuntu0.20.04.4 [262 kB]
Fetched 262 kB in 0s (873 kB/s)
Selecting previously unselected package freerdp2-x11.
(Reading database ... 485501 files and directories currently installed.)
Preparing to unpack .../freerdp2-x11_2.2.0+dfsg1-0ubuntu0.20.04.4_amd64.deb ...
Unpacking freerdp2-x11 (2.2.0+dfsg1-0ubuntu0.20.04.4) ...
Setting up freerdp2-x11 (2.2.0+dfsg1-0ubuntu0.20.04.4) ...
Processing triggers for man-db (2.9.1-1) ...

After this I checked version of xfreerdp and it is 2.7.0:

> zak@zak:~$ xfreerdp --version
This is FreeRDP version 2.7.0 (2.7.0)

Please help me understand how I received xfreerdp version 2.7.0 when install 2.2.0+dfsg1-0ubuntu0.20.04.4 packet.

Regards,
Zakhar.

---

### Post by TheFu on 2023-01-29
Might you have 2 versions installed and the newer one is found first in the PATH?

---

### Post by zak12 on 2023-01-30
I suppose no, because after delete of packet:

 > zak@zak:~$ sudo apt remove freerdp2-x11
[sudo] password for zak: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  freerdp2-x11
0 upgraded, 0 newly installed, 1 to remove and 5 not upgraded.
After this operation, 1&#8239;370 kB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 485506 files and directories currently installed.)
Removing freerdp2-x11 (2.2.0+dfsg1-0ubuntu0.20.04.4) ...
Processing triggers for man-db (2.9.1-1) ...

I can not execute this app:

> zak@zak:~$ xfreerdp --version
Command 'xfreerdp' not found, but can be installed with:
sudo apt install freerdp2-x11

---

### Post by Impavidus on 2023-01-30
When the repository offers both the 2.2.0 and the 2.0.0 version, the package manager will automatically select the 2.2.0 version. It picks the latest by default, so no need to ask for a specific version here. This way the system can handle upgrades without removing the old version from the repositories, which can be useful for people who only want security updates, but not the regular updates. Version 2.0.0 is available for the arm64 architecture, but apparently your mirror has it for amd64 too.

Normally, the version of the package should match the version of the packaged software, but this isn't automatically enforced. One could compile version 2.7 and put it in a deb file declaring to have version 2.2. I have encountered versions of software not matching the official repos on some dodgy mirrors. Maybe you can check a different mirror or the main server.

---

### Post by zak12 on 2023-01-30
[[COLOR=#000000]Impavidus[/COLOR]]("https://ubuntuforums.org/member.php?u=1417721"), thank you for helping!

My investigation led me to a custom ppa repository for remmina app and from this repo was install libfreerdp2-2 core library with freerdp 2.7 version. When I remove this software I can correctly installed freerdp2-x11=2.2.0+dfsg1-0ubuntu0.20.04.4 with correct 2.2.0 verison.

---

