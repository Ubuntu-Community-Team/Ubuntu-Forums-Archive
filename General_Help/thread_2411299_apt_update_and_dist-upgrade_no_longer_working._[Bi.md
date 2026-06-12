---
title: "apt update and dist-upgrade no longer working. [Bionic 18.04]"
date: 2019-01-28
forum: General Help
---

### Post by Ziad_Arafat on 2019-01-28
This is on kubuntu but the repos involved are not distro specific it's just Bionic repos. 

This is my output on both commands. Notice lots of 404s and Warnings. Then notice when I run upgrade there are no upgrades and this has been the case for several weeks now. There is no way on this green earth that there have been no updates for the thousands of packages I have installed for that long. I usually get updates almost daily so I suspect its related to the 404 errors. I also cannot update with muon package manager it just says failed to download due to 404 errors. What is a sure-fire way to fix this? I do have a repo in there for non-x86 packages because I do some raspberry pi development and I work with nvidia jetson. 

```
Get:1 http://security.ubuntu.com/ubuntu bionic-security InRelease [88.7 kB]
Hit:2 http://us.archive.ubuntu.com/ubuntu bionic InRelease                                                                                                                                                                        
Get:3 http://us.archive.ubuntu.com/ubuntu bionic-updates InRelease [88.7 kB]                                                                                                                                                      
Hit:4 https://packages.microsoft.com/ubuntu/18.04/prod bionic InRelease                                                                                                               
Hit:5 http://ppa.launchpad.net/dhor/myway/ubuntu bionic InRelease                                                                                                 
Ign:6 http://ports.ubuntu.com/ubuntu-ports main InRelease                                                  
Hit:7 http://ports.ubuntu.com/ubuntu-ports bionic InRelease                                                                            
Get:8 http://us.archive.ubuntu.com/ubuntu bionic-backports InRelease [74.6 kB]                                                         
Err:9 http://ports.ubuntu.com/ubuntu-ports main Release                                                    
  404  Not Found [IP: 91.189.88.150 80]
Hit:10 http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu bionic InRelease
Ign:11 http://us.archive.ubuntu.com/ubuntu bionic/main arm64 Packages     
Ign:12 http://us.archive.ubuntu.com/ubuntu bionic/restricted arm64 Packages    
Ign:13 http://us.archive.ubuntu.com/ubuntu bionic/universe arm64 Packages      
Ign:14 http://us.archive.ubuntu.com/ubuntu bionic/multiverse arm64 Packages    
Ign:11 http://us.archive.ubuntu.com/ubuntu bionic/main arm64 Packages                                
Ign:12 http://us.archive.ubuntu.com/ubuntu bionic/restricted arm64 Packages                          
Ign:13 http://us.archive.ubuntu.com/ubuntu bionic/universe arm64 Packages                            
Ign:15 http://security.ubuntu.com/ubuntu bionic-security/main arm64 Packages                         
Get:16 http://security.ubuntu.com/ubuntu bionic-security/main amd64 Packages [243 kB]                
Get:17 http://security.ubuntu.com/ubuntu bionic-security/main i386 Packages [186 kB]
Get:18 http://security.ubuntu.com/ubuntu bionic-security/main Translation-en [92.3 kB]
Get:19 http://security.ubuntu.com/ubuntu bionic-security/main amd64 DEP-11 Metadata [204 B]
Get:20 http://security.ubuntu.com/ubuntu bionic-security/universe i386 Packages [112 kB]
Get:21 http://security.ubuntu.com/ubuntu bionic-security/universe amd64 Packages [114 kB]         
Get:22 http://security.ubuntu.com/ubuntu bionic-security/universe arm64 Packages [114 kB]                              
Get:22 http://security.ubuntu.com/ubuntu bionic-security/universe arm64 Packages [114 kB]                                                                                                                                                     
Get:22 http://security.ubuntu.com/ubuntu bionic-security/universe arm64 Packages [114 kB]                                                                                                                                                     
Get:22 http://security.ubuntu.com/ubuntu bionic-security/universe arm64 Packages [114 kB]                                                                                                                                                     
Get:22 http://security.ubuntu.com/ubuntu bionic-security/universe arm64 Packages [114 kB]                                                                                                                                                     
Get:22 http://security.ubuntu.com/ubuntu bionic-security/universe arm64 Packages [114 kB]                                                                                                                                                     
Get:22 http://security.ubuntu.com/ubuntu bionic-security/universe arm64 Packages [114 kB]                                                                                                                                                     
Get:22 http://security.ubuntu.com/ubuntu bionic-security/universe arm64 Packages [114 kB]                                                                                                                                                     
Get:22 http://security.ubuntu.com/ubuntu bionic-security/universe arm64 Packages [114 kB]                                                                                                                                                     
Get:22 http://security.ubuntu.com/ubuntu bionic-security/universe arm64 Packages [114 kB]                                                                                                                                                     
Get:22 http://security.ubuntu.com/ubuntu bionic-security/universe arm64 Packages [114 kB]                                                                                                                                                     
Get:22 http://security.ubuntu.com/ubuntu bionic-security/universe arm64 Packages [114 kB]                                                                                                                                                     
Get:22 http://security.ubuntu.com/ubuntu bionic-security/universe arm64 Packages [114 kB]                                                                                                                                                     
Ign:14 http://us.archive.ubuntu.com/ubuntu bionic/multiverse arm64 Packages                                                                                                                                                                   
Ign:11 http://us.archive.ubuntu.com/ubuntu bionic/main arm64 Packages                                                                                                                                                                         
Ign:12 http://us.archive.ubuntu.com/ubuntu bionic/restricted arm64 Packages                                                                                                                                                                   
Ign:22 http://security.ubuntu.com/ubuntu bionic-security/universe arm64 Packages                                                                                                                                                              
Ign:36 http://security.ubuntu.com/ubuntu bionic-security/multiverse arm64 Packages                                                                                                                                                            
Hit:37 http://ppa.launchpad.net/noobslab/apps/ubuntu bionic InRelease                                                                                                                                                                         
Ign:13 http://us.archive.ubuntu.com/ubuntu bionic/universe arm64 Packages                                                                                                                                                                     
Ign:14 http://us.archive.ubuntu.com/ubuntu bionic/multiverse arm64 Packages                                                                                                                                                                   
Err:11 http://us.archive.ubuntu.com/ubuntu bionic/main arm64 Packages                                                                                                                                                                         
  404  Not Found [IP: 91.189.91.23 80]
Ign:15 http://security.ubuntu.com/ubuntu bionic-security/main arm64 Packages                             
Ign:12 http://us.archive.ubuntu.com/ubuntu bionic/restricted arm64 Packages                       
Ign:13 http://us.archive.ubuntu.com/ubuntu bionic/universe arm64 Packages                         
Ign:14 http://us.archive.ubuntu.com/ubuntu bionic/multiverse arm64 Packages                       
Ign:22 http://security.ubuntu.com/ubuntu bionic-security/universe arm64 Packages    
Ign:36 http://security.ubuntu.com/ubuntu bionic-security/multiverse arm64 Packages  
Get:38 http://us.archive.ubuntu.com/ubuntu bionic-updates/main i386 Packages [426 kB]
Get:39 http://us.archive.ubuntu.com/ubuntu bionic-updates/main arm64 Packages [403 kB]
Get:39 http://us.archive.ubuntu.com/ubuntu bionic-updates/main arm64 Packages [403 kB]
Get:39 http://us.archive.ubuntu.com/ubuntu bionic-updates/main arm64 Packages [403 kB]
Get:39 http://us.archive.ubuntu.com/ubuntu bionic-updates/main arm64 Packages [403 kB]
Get:39 http://us.archive.ubuntu.com/ubuntu bionic-updates/main arm64 Packages [403 kB]        
Get:39 http://us.archive.ubuntu.com/ubuntu bionic-updates/main arm64 Packages [403 kB]
Get:39 http://us.archive.ubuntu.com/ubuntu bionic-updates/main arm64 Packages [403 kB]
Ign:15 http://security.ubuntu.com/ubuntu bionic-security/main arm64 Packages
Get:39 http://us.archive.ubuntu.com/ubuntu bionic-updates/main arm64 Packages [403 kB]
Get:39 http://us.archive.ubuntu.com/ubuntu bionic-updates/main arm64 Packages [403 kB]
Get:39 http://us.archive.ubuntu.com/ubuntu bionic-updates/main arm64 Packages [403 kB]        
Get:39 http://us.archive.ubuntu.com/ubuntu bionic-updates/main arm64 Packages [403 kB]        
Get:39 http://us.archive.ubuntu.com/ubuntu bionic-updates/main arm64 Packages [403 kB]
Get:39 http://us.archive.ubuntu.com/ubuntu bionic-updates/main arm64 Packages [403 kB]
Get:39 http://us.archive.ubuntu.com/ubuntu bionic-updates/main arm64 Packages [403 kB]        
Get:39 http://us.archive.ubuntu.com/ubuntu bionic-updates/main arm64 Packages [403 kB]
Get:39 http://us.archive.ubuntu.com/ubuntu bionic-updates/main arm64 Packages [403 kB]
Ign:22 http://security.ubuntu.com/ubuntu bionic-security/universe arm64 Packages                  
Ign:36 http://security.ubuntu.com/ubuntu bionic-security/multiverse arm64 Packages                 
Err:15 http://security.ubuntu.com/ubuntu bionic-security/main arm64 Packages                             
  404  Not Found [IP: 91.189.91.26 80]
Ign:39 http://us.archive.ubuntu.com/ubuntu bionic-updates/main arm64 Packages                            
Ign:56 http://us.archive.ubuntu.com/ubuntu bionic-updates/restricted arm64 Packages                      
Ign:57 http://us.archive.ubuntu.com/ubuntu bionic-updates/universe arm64 Packages  
Ign:58 http://us.archive.ubuntu.com/ubuntu bionic-updates/multiverse arm64 Packages
Get:59 http://us.archive.ubuntu.com/ubuntu bionic-backports/universe amd64 Packages [3,472 B]
Get:60 http://us.archive.ubuntu.com/ubuntu bionic-backports/universe i386 Packages [3,472 B]
Get:61 http://us.archive.ubuntu.com/ubuntu bionic-backports/universe arm64 Packages [3,468 B]
Ign:22 http://security.ubuntu.com/ubuntu bionic-security/universe arm64 Packages                           
Ign:61 http://us.archive.ubuntu.com/ubuntu bionic-backports/universe arm64 Packages
Ign:39 http://us.archive.ubuntu.com/ubuntu bionic-updates/main arm64 Packages   
Ign:56 http://us.archive.ubuntu.com/ubuntu bionic-updates/restricted arm64 Packages
Ign:57 http://us.archive.ubuntu.com/ubuntu bionic-updates/universe arm64 Packages
Ign:36 http://security.ubuntu.com/ubuntu bionic-security/multiverse arm64 Packages
Ign:58 http://us.archive.ubuntu.com/ubuntu bionic-updates/multiverse arm64 Packages
Ign:61 http://us.archive.ubuntu.com/ubuntu bionic-backports/universe arm64 Packages
Ign:39 http://us.archive.ubuntu.com/ubuntu bionic-updates/main arm64 Packages
Ign:56 http://us.archive.ubuntu.com/ubuntu bionic-updates/restricted arm64 Packages
Ign:57 http://us.archive.ubuntu.com/ubuntu bionic-updates/universe arm64 Packages
Ign:58 http://us.archive.ubuntu.com/ubuntu bionic-updates/multiverse arm64 Packages
Ign:61 http://us.archive.ubuntu.com/ubuntu bionic-backports/universe arm64 Packages
Err:39 http://us.archive.ubuntu.com/ubuntu bionic-updates/main arm64 Packages
  404  Not Found [IP: 91.189.91.23 80]
Ign:56 http://us.archive.ubuntu.com/ubuntu bionic-updates/restricted arm64 Packages
Ign:57 http://us.archive.ubuntu.com/ubuntu bionic-updates/universe arm64 Packages
Ign:58 http://us.archive.ubuntu.com/ubuntu bionic-updates/multiverse arm64 Packages
Err:61 http://us.archive.ubuntu.com/ubuntu bionic-backports/universe arm64 Packages
  404  Not Found [IP: 91.189.91.23 80]
Reading package lists... Done
W: Target Packages (main/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list:10
W: Target Packages (main/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list:10
W: Target Packages (main/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list:10
W: Target Translations (main/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list:10
W: Target Translations (main/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list:10
W: Target DEP-11 (main/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list:10
W: Target DEP-11 (main/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list:10
W: Target DEP-11-icons-small (main/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list:10
W: Target DEP-11-icons (main/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list:10
W: Target DEP-11-icons-hidpi (main/dep11/icons-64x64@2.tar) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list:10
W: Target DEP-11-icons-large (main/dep11/icons-128x128.tar) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list:10
W: Target CNF (main/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list:10
W: Target CNF (main/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list:10
W: Target Packages (universe/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:10 and /etc/apt/sources.list:22
W: Target Packages (universe/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:10 and /etc/apt/sources.list:22
W: Target Packages (universe/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:10 and /etc/apt/sources.list:22
W: Target Translations (universe/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:10 and /etc/apt/sources.list:22
W: Target Translations (universe/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:10 and /etc/apt/sources.list:22
W: Target DEP-11 (universe/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:10 and /etc/apt/sources.list:22
W: Target DEP-11 (universe/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:10 and /etc/apt/sources.list:22
W: Target DEP-11-icons-small (universe/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:10 and /etc/apt/sources.list:22
W: Target DEP-11-icons (universe/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:10 and /etc/apt/sources.list:22
W: Target DEP-11-icons-hidpi (universe/dep11/icons-64x64@2.tar) is configured multiple times in /etc/apt/sources.list:10 and /etc/apt/sources.list:22
W: Target DEP-11-icons-large (universe/dep11/icons-128x128.tar) is configured multiple times in /etc/apt/sources.list:10 and /etc/apt/sources.list:22
W: Target CNF (universe/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list:10 and /etc/apt/sources.list:22
W: Target CNF (universe/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:10 and /etc/apt/sources.list:22
E: The repository 'http://ports.ubuntu.com/ubuntu-ports main Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: Target Packages (main/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list:10
W: Target Packages (main/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list:10
W: Target Packages (main/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list:10
W: Target Translations (main/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list:10
W: Target Translations (main/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list:10
W: Target DEP-11 (main/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list:10
W: Target DEP-11 (main/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list:10
W: Target DEP-11-icons-small (main/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list:10
W: Target DEP-11-icons (main/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list:10
W: Target DEP-11-icons-hidpi (main/dep11/icons-64x64@2.tar) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list:10
W: Target DEP-11-icons-large (main/dep11/icons-128x128.tar) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list:10
W: Target CNF (main/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list:10
W: Target CNF (main/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list:10
W: Target Packages (universe/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:10 and /etc/apt/sources.list:22
W: Target Packages (universe/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:10 and /etc/apt/sources.list:22
W: Target Packages (universe/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:10 and /etc/apt/sources.list:22
W: Target Translations (universe/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:10 and /etc/apt/sources.list:22
W: Target Translations (universe/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:10 and /etc/apt/sources.list:22
W: Target DEP-11 (universe/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:10 and /etc/apt/sources.list:22
W: Target DEP-11 (universe/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:10 and /etc/apt/sources.list:22
W: Target DEP-11-icons-small (universe/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:10 and /etc/apt/sources.list:22
W: Target DEP-11-icons (universe/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:10 and /etc/apt/sources.list:22
W: Target DEP-11-icons-hidpi (universe/dep11/icons-64x64@2.tar) is configured multiple times in /etc/apt/sources.list:10 and /etc/apt/sources.list:22
W: Target DEP-11-icons-large (universe/dep11/icons-128x128.tar) is configured multiple times in /etc/apt/sources.list:10 and /etc/apt/sources.list:22
W: Target CNF (universe/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list:10 and /etc/apt/sources.list:22
W: Target CNF (universe/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:10 and /etc/apt/sources.list:22


```


Here is my sources.list file
```
# deb cdrom:[Kubuntu 18.04 LTS _Bionic Beaver_ - Release amd64 (20180426)]/ bionic main multiverse restricted universe

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ bionic main restricted
deb [arch=arm64] http://ports.ubuntu.com/ubuntu-ports main restricted
# deb-src http://us.archive.ubuntu.com/ubuntu/ bionic main restricted

deb [arch=arm64] http://ports.ubuntu.com/ubuntu-ports bionic main universe
deb [arch=amd64,i386] http://us.archive.ubuntu.com/ubuntu/ bionic main universe



## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ bionic-updates main restricted
# deb-src http://us.archive.ubuntu.com/ubuntu/ bionic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ bionic universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ bionic universe
deb http://us.archive.ubuntu.com/ubuntu/ bionic-updates universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ bionic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ bionic multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ bionic multiverse
deb http://us.archive.ubuntu.com/ubuntu/ bionic-updates multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ bionic-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ bionic-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ bionic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu bionic partner
# deb-src http://archive.canonical.com/ubuntu bionic partner


```

I also have these in my sources.list.d

```

dhor-ubuntu-myway-bionic.list       graphics-drivers-ubuntu-ppa-bionic.list       microsoft-prod.list       noobslab-ubuntu-apps-bionic.list
dhor-ubuntu-myway-bionic.list.save  graphics-drivers-ubuntu-ppa-bionic.list.save  microsoft-prod.list.save  noobslab-ubuntu-apps-bionic.list.save

```

EDIT: Here are my full specs if needed: 

```
System:    Host: ziad-Desktop Kernel: 4.15.0-43-generic x86_64 bits: 64 gcc: 7.3.0
           Desktop: KDE Plasma 5.12.7 (Qt 5.9.5) Distro: Ubuntu 18.04.1 LTS                                                                                                                                                                   
Machine:   Device: desktop System: Hewlett-Packard product: HP Z400 Workstation serial: N/A                                                                                                                                                   
           Mobo: Hewlett-Packard model: 0B4Ch v: D serial: N/A                                                                                                                                                                                
           BIOS: Hewlett-Packard v: 786G3 v03.54 date: 11/02/2011                                                                                                                                                                             
CPU:       6 core Intel Xeon X5650 (-MT-MCP-) arch: Nehalem rev.2 cache: 12288 KB                                                                                                                                                             
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 32000                                                                                                                                                                  
           clock speeds: max: 2661 MHz 1: 1616 MHz 2: 1663 MHz 3: 1643 MHz 4: 1656 MHz 5: 1621 MHz 6: 1727 MHz                                                                                                                                
           7: 1672 MHz 8: 1650 MHz 9: 1643 MHz 10: 1724 MHz 11: 1637 MHz 12: 1604 MHz                                                                                                                                                         
Graphics:  Card: NVIDIA GP106 [GeForce GTX 1060 6GB] bus-ID: 0f:00.0                                                                                                                                                                          
           Display Server: x11 (X.Org 1.19.6 ) drivers: nvidia (unloaded: modesetting,fbdev,vesa,nouveau)                                                                                                                                     
           Resolution: 1920x1080@60.00hz                                                                                                                                                                                                      
           OpenGL: renderer: GeForce GTX 1060 6GB/PCIe/SSE2 version: 4.6.0 NVIDIA 415.27 Direct Render: Yes                                                                                                                                   
Audio:     Card-1 NVIDIA GP106 High Definition Audio Controller driver: snd_hda_intel bus-ID: 0f:00.1                                                                                                                                         
           Card-2 Intel 82801JI (ICH10 Family) HD Audio Controller driver: snd_hda_intel bus-ID: 00:1b.0                                                                                                                                      
           Sound: Advanced Linux Sound Architecture v: k4.15.0-43-generic                                                                                                                                                                     
Network:   Card: Broadcom Limited NetXtreme BCM5764M Gigabit Ethernet PCIe driver: tg3 v: 3.137 bus-ID: 01:00.0                                                                                                                               
           IF: enp1s0 state: up speed: 100 Mbps duplex: half mac: <filter>                                                                                                                                                                    
Drives:    HDD Total Size: 2500.5GB (16.0% used)                                                                                                                                                                                              
           ID-1: /dev/sda model: Hitachi_HUA72202 size: 2000.4GB temp: 32C                                                                                                                                                                    
           ID-2: /dev/sdb model: Samsung_SSD_860 size: 500.1GB temp: 0C                                                                                                                                                                       
Partition: ID-1: / size: 458G used: 372G (86%) fs: ext4 dev: /dev/sdb1                                                                                                                                                                        
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present                                                                                                                                                                        
Sensors:   System Temperatures: cpu: 17.0C mobo: N/A gpu: 0.0:48C                                                                                                                                                                             
           Fan Speeds (in rpm): cpu: N/A                                                                                                                                                                                                      
Info:      Processes: 311 Uptime: 32 min Memory: 2655.2/24086.5MB Init: systemd runlevel: 5 Gcc sys: 7.3.0                                                                                                                                    
           Client: Shell (bash 4.4.191) inxi: 2.3.56  
 
```

---

### Post by Ziad_Arafat on 2019-01-29
Upon inspection it could be that it's automatically upgrading in the background however it still doesn't help with the ridiculous amount of warnings I am gettings.

---

### Post by deadflowr on 2019-01-29
The Warnings are because (line #10)
```
deb [arch=amd64,i386] http://us.archive.ubuntu.com/ubuntu/ bionic main universe
```
is already reflected in the line up top (line #5)
```
deb http://us.archive.ubuntu.com/ubuntu/ bionic main restricted
```
and in this line (line #22)
```
deb http://us.archive.ubuntu.com/ubuntu/ bionic universe
```
You only want one entry so,
probably better to keep line #10 as that has the [arch=amd64,i386] entry which should help prevent it from trying to grab the arm64 packages from there.

Also I have no idea how you have any security repo errors as you do not have the security repos enabled anywhere in the main sources.list file.
Are they set in one of those files in the sources.list.d directory?

I'm sure there is more to do, but those are two things that struck me off the bat.

---

### Post by Ziad_Arafat on 2019-02-05
Ok pointing out the security repo errors gave me an idea. I have now "discovered" that kubuntu's software center "discover" was the culprit all along. For anyone facing this issue and has discover installed. Go into discover and disable every single repo in the settings then rebuild your sources.list file and re-add all your PPAs. All issues fixed and debugged the sources.list file. (needless to say. Lots of updates were needed) [IMG]https://i.imgur.com/iSVLKkF.png[/IMG]

---

