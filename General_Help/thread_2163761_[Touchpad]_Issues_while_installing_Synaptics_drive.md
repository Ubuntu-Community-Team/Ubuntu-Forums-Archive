---
title: "[Touchpad] Issues while installing Synaptics drivers"
date: 2013-07-19
forum: General Help
---

### Post by localh0st on 2013-07-19
I've uninstalled Synaptics drivers (xserver-xorg-input-synaptics). Now I'm trying to install them again, but I still get the problems with dependencies/repository. 
Here is explonation:
```

[LIST=1]
[*][COLOR=#000000]root @ abyss home/localh0st :/ # apt-get install xserver-xorg-input-synaptics
Reading package lists ... ready
Building dependency tree
Reading state information ... ready
Failed to install some packages. This could mean
that you have requested an impossible situation or used unstable
that some required packages have not yet been created or been moved
Incoming directory ("Incoming").
The following information may help to resolve the situation:
 
The following packages have unmet dependencies:
  xserver-xorg-input-synaptics: Depends: xorg-input-abi-18
E: Unable to correct problems, stopped broken packages.
 
root @ abyss home/localh0st :/ # apt-get install xorg-input-abi-18
Reading package lists ... ready
Building dependency tree
Reading state information ... ready
Xorg-input-abi-18 is a virtual package provided by:
   xserver-xorg-core 2:1.13.3-0ubuntu6 [Not candidate version]
 
 
root @ abyss home/localh0st :/ # apt-cache policy xserver-xorg-core
xserver-xorg-core:
   Installed: 3:1.12.4 + git20121105-makson1 ~ PPA2
   Candidate: 3:1.12.4 + git20121105-makson1 ~ PPA2
   Table version:
  *** 3:1.12.4 + git20121105-makson1 ~ PPA2 0
         100 / var / lib / dpkg / status
      2:1.13.3-0ubuntu6 0
         500 http://pl.archive.ubuntu.com/ubuntu/ raring / main amd64 Packages
 
 
root @ abyss home/localh0st :/ # apt-cache policy xserver-xorg-input-synaptics
xserver-xorg-input-synaptics:
   Installed: (none)
   Candidate: 1.6.2-1ubuntu6
   Table version:
      1.6.2-1ubuntu6 0
         Five hundred http://pl.archive.ubuntu.com/ubuntu/ raring / main amd64 Packages
 
 
root @ abyss home/localh0st :/ # apt-cache policy xorg-input-abi-18
xorg-input-abi-18:
   Installed: (none)
   Candidate: (none)
   Table version:
[/COLOR]
[/LIST]

```

Does anybody know how can I fix it? 
I've got problems on 12.10, I've upgraded distro do 13.04 but it won't install. 
Repositories in sources.list are up to date.

---

