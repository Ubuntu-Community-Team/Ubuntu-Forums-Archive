---
title: "help packages"
date: 2022-08-03
forum: General Help
---

### Post by mikaelrask on 2022-08-03
hey after a upgrade today i got held packages
sudo apt update && sudo apt upgrade -f
[sudo] password for mikael: 
Hit:1 [http://se.archive.ubuntu.com/ubuntu](http://se.archive.ubuntu.com/ubuntu) jammy InRelease
Hit:2 [http://se.archive.ubuntu.com/ubuntu](http://se.archive.ubuntu.com/ubuntu) jammy-updates InRelease                                          
Hit:3 [http://se.archive.ubuntu.com/ubuntu](http://se.archive.ubuntu.com/ubuntu) jammy-backports InRelease                                        
Hit:4 [https://repo.steampowered.com/steam](https://repo.steampowered.com/steam) stable InRelease                                                
Get:5 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jammy-security InRelease [110 kB]  
Get:6 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jammy-security/main amd64 DEP-11 Metadata [11,4 kB]
Get:7 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jammy-security/universe amd64 DEP-11 Metadata [608 B]
Fetched 122 kB in 1s (135 kB/s)           
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
3 packages can be upgraded. Run 'apt list --upgradable' to see them.
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  python3-distupgrade ubuntu-release-upgrader-core ubuntu-release-upgrader-qt
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.

is it a bug or do i need to do something to get this fixed

i'm on kubuntu 22,04 clean installed about a week ago, thanks in advance


[FONT=monospace][FONT=monospace][COLOR=#000000]apt list --upgradable[/COLOR]
[/FONT][COLOR=#18b218]python3-distupgrade[/COLOR][COLOR=#000000]/jammy-updates,jammy-updates 1:22.04.12 all [upgradable from: 1:22.04.11] [/COLOR]
[COLOR=#18b218]ubuntu-release-upgrader-core[/COLOR][COLOR=#000000]/jammy-updates,jammy-updates 1:22.04.12 all [upgradable from: 1:22.04.11] [/COLOR]
[COLOR=#18b218]ubuntu-release-upgrader-qt[/COLOR][COLOR=#000000]/jammy-updates,jammy-updates 1:22.04.12 all [upgradable from: 1:22.04.11][/COLOR]
[/FONT]

---

### Post by ActionParsnip on 2022-08-03
If a package has dependant packages that have not been published yet then the packages relying on these later versions will be "kept back". Nothing is wrong here.

If package A is at version 1.0 and package B is at version 2.0 on your system and installed OK....then package A is released at version 1.1 but needs package B at version 2.1 and this currently isn't available then the update to package A will b kept back. After some time. an update to package B is pushed to 2.1. The deps for package A version 1.1 is now met and both packages will be installed.

HTH

---

### Post by deadflowr on 2022-08-03
> is it a bug or do i need to do something to get this fixed

Neither a bug nor something wrong with whatever you are doing.
It's intentional.
It's part of Ubuntu phased-updates mechanism which has been adopted by the apt package manager.
(Earlier releases has phased-updates only apply to updating through the update-manager, but now they are done using apt commands as well.)

A sort of on-going thread about it here: [https://ubuntuforums.org/showthread.php?t=2477612]("https://ubuntuforums.org/showthread.php?t=2477612")

---

### Post by mikaelrask on 2022-08-04
hey okey then i get it :D thanks for the information.

---

### Post by mIk3_08 on 2022-08-04
On how to mark this thread as solve,
Please Click the "[COLOR=#ff0000]**Solve thread**[/COLOR]" link below. Regards and cheers.

---

