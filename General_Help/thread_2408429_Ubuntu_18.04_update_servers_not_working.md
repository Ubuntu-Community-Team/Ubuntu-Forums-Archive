---
title: "Ubuntu 18.04 update servers not working?"
date: 2018-12-18
forum: General Help
---

### Post by Ziad_Arafat on 2018-12-18
I've been having this issue for a while on several Ubuntu bionic systems. It doesn't appear to be the common issue of the sources.list containing old repos from 16.04 because
1. I didn't upgrade it's a fresh install. 
2. My sources.list below doesn't have anything but bionic. 

I have tried a lot of fixes such as completely deleting the sources.list and anything in sources.list.d and repopulating it with something from another user. I tried changing it to different servers like the us.archive server as opposed to the main archive server. It looks like it's just straight up failing to reach the server. Is there a real fix to this? 

Here is the sources.list I have currently but be aware I've tried several iterations of it to no avail. Including generating one from repogen. 

```
#deb cdrom:[Kubuntu 18.04 LTS _Bionic Beaver_ - Release amd64 (20180426)]/ bionic main multiverse restricted universe

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ bionic main restricted
# deb-src http://us.archive.ubuntu.com/ubuntu/ bionic main restricted


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


deb http://security.ubuntu.com/ubuntu bionic-security main restricted
# deb-src http://security.ubuntu.com/ubuntu bionic-security main restricted
deb http://security.ubuntu.com/ubuntu bionic-security universe
# deb-src http://security.ubuntu.com/ubuntu bionic-security universe
deb http://security.ubuntu.com/ubuntu bionic-security multiverse
# deb-src http://security.ubuntu.com/ubuntu bionic-security multiverse
```

Here are the errors I am getting. The first one is with grep Err to easily see which ones have the issue and the second is the full output.

```
[FONT=monospace][COLOR=#FF5454]**Err**[/COLOR][COLOR=#000000]:6 http://us.archive.ubuntu.com/ubuntu bionic/main arm64 Packages[/COLOR]
[COLOR=#FF5454]**Err**[/COLOR][COLOR=#000000]:12 http://us.archive.ubuntu.com/ubuntu bionic-updates/main arm64 Packages[/COLOR]
[COLOR=#FF5454]**Err**[/COLOR][COLOR=#000000]:54 http://us.archive.ubuntu.com/ubuntu bionic-backports/universe arm64 Packages[/COLOR]
[COLOR=#FF5454]**Err**[/COLOR][COLOR=#000000]:39 http://security.ubuntu.com/ubuntu bionic-security/main arm64 Packages[/COLOR]
E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/bionic/main/binary-arm64/Packages  404  No
t Found [IP: 91.189.91.23 80]
E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/bionic-updates/main/binary-arm64/Packages 
 404  Not Found [IP: 91.189.91.23 80]
E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/bionic-backports/universe/binary-arm64/Pac
kages  404  Not Found [IP: 91.189.91.23 80]
E: Failed to fetch http://security.ubuntu.com/ubuntu/dists/bionic-security/main/binary-arm64/Packages  
404  Not Found [IP: 91.189.88.161 80]
E: Some index files failed to download. They have been ignored, or old ones used instead.

[/FONT]
```

```
[FONT=monospace][COLOR=#000000]Hit:1 http://us.archive.ubuntu.com/ubuntu bionic InRelease[/COLOR]
Hit:3 http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu bionic InRelease                    
Get:2 http://us.archive.ubuntu.com/ubuntu bionic-updates InRelease [88.7 kB][COLOR=#B26818]                  [/COLOR][COLOR=#000000] [/COLOR]
Get:4 http://security.ubuntu.com/ubuntu bionic-security InRelease [83.2 kB]
Get:5 http://us.archive.ubuntu.com/ubuntu bionic-backports InRelease [74.6 kB]        
Get:6 http://us.archive.ubuntu.com/ubuntu bionic/main arm64 Packages [975 kB][COLOR=#B26818]                   [/COLOR][COLOR=#000000] [/COLOR]
Get:6 http://us.archive.ubuntu.com/ubuntu bionic/main arm64 Packages [975 kB][COLOR=#B26818]   [/COLOR][COLOR=#000000] [/COLOR]
Get:6 http://us.archive.ubuntu.com/ubuntu bionic/main arm64 Packages [975 kB]          
Get:6 http://us.archive.ubuntu.com/ubuntu bionic/main arm64 Packages [975 kB]         [COLOR=#B26818]                [/COLOR][COLOR=#000000] [/COLOR]
Get:6 http://us.archive.ubuntu.com/ubuntu bionic/main arm64 Packages [975 kB]         [COLOR=#B26818]                [/COLOR][COLOR=#000000] [/COLOR]
Get:6 http://us.archive.ubuntu.com/ubuntu bionic/main arm64 Packages [975 kB]          
Get:6 http://us.archive.ubuntu.com/ubuntu bionic/main arm64 Packages [975 kB]         [COLOR=#B26818]                [/COLOR][COLOR=#000000] [/COLOR]
Get:6 http://us.archive.ubuntu.com/ubuntu bionic/main arm64 Packages [975 kB]          
Get:6 http://us.archive.ubuntu.com/ubuntu bionic/main arm64 Packages [975 kB]          
Get:6 http://us.archive.ubuntu.com/ubuntu bionic/main arm64 Packages [975 kB]          
Get:6 http://us.archive.ubuntu.com/ubuntu bionic/main arm64 Packages [975 kB]          
Get:6 http://us.archive.ubuntu.com/ubuntu bionic/main arm64 Packages [975 kB]          
Get:6 http://us.archive.ubuntu.com/ubuntu bionic/main arm64 Packages [975 kB]          
Get:6 http://us.archive.ubuntu.com/ubuntu bionic/main arm64 Packages [975 kB]          
Get:6 http://us.archive.ubuntu.com/ubuntu bionic/main arm64 Packages [975 kB]         [COLOR=#B26818]                [/COLOR][COLOR=#000000] [/COLOR]
Get:6 http://us.archive.ubuntu.com/ubuntu bionic/main arm64 Packages [975 kB]         [COLOR=#B26818]                [/COLOR][COLOR=#000000] [/COLOR]
Get:6 http://us.archive.ubuntu.com/ubuntu bionic/main arm64 Packages [975 kB][COLOR=#B26818]         [/COLOR][COLOR=#000000] [/COLOR]
Get:6 http://us.archive.ubuntu.com/ubuntu bionic/main arm64 Packages [975 kB]
Get:6 http://us.archive.ubuntu.com/ubuntu bionic/main arm64 Packages [975 kB]
Get:6 http://us.archive.ubuntu.com/ubuntu bionic/main arm64 Packages [975 kB]
Get:6 http://us.archive.ubuntu.com/ubuntu bionic/main arm64 Packages [975 kB]
Ign:6 http://us.archive.ubuntu.com/ubuntu bionic/main arm64 Packages[COLOR=#B26818] [/COLOR][COLOR=#000000] [/COLOR]
Ign:28 http://us.archive.ubuntu.com/ubuntu bionic/restricted arm64 Packages
Ign:29 http://us.archive.ubuntu.com/ubuntu bionic/universe arm64 Packages
Ign:30 http://us.archive.ubuntu.com/ubuntu bionic/multiverse arm64 Packages
Ign:31 http://us.archive.ubuntu.com/ubuntu bionic-updates/main arm64 Packages
Get:32 http://us.archive.ubuntu.com/ubuntu bionic-updates/restricted arm64 Packages [668 B]
Get:32 http://us.archive.ubuntu.com/ubuntu bionic-updates/restricted arm64 Packages [668 B]
Get:32 http://us.archive.ubuntu.com/ubuntu bionic-updates/restricted arm64 Packages [668 B]
Get:32 http://us.archive.ubuntu.com/ubuntu bionic-updates/restricted arm64 Packages [668 B]
Get:32 http://us.archive.ubuntu.com/ubuntu bionic-updates/restricted arm64 Packages [668 B]
Ign:32 http://us.archive.ubuntu.com/ubuntu bionic-updates/restricted arm64 Packages
Ign:38 http://us.archive.ubuntu.com/ubuntu bionic-updates/universe arm64 Packages
Ign:39 http://us.archive.ubuntu.com/ubuntu bionic-updates/multiverse arm64 Packages
Ign:40 http://us.archive.ubuntu.com/ubuntu bionic-backports/universe arm64 Packages
Ign:6 http://us.archive.ubuntu.com/ubuntu bionic/main arm64 Packages[COLOR=#B26818]            [/COLOR][COLOR=#000000] [/COLOR]
Get:41 http://security.ubuntu.com/ubuntu bionic-security/main amd64 Packages [221 kB]
Get:42 http://security.ubuntu.com/ubuntu bionic-security/main i386 Packages [171 kB]
Get:43 http://security.ubuntu.com/ubuntu bionic-security/main arm64 Packages [165 kB]
Get:43 http://security.ubuntu.com/ubuntu bionic-security/main arm64 Packages [165 kB]
Get:43 http://security.ubuntu.com/ubuntu bionic-security/main arm64 Packages [165 kB]
Get:43 http://security.ubuntu.com/ubuntu bionic-security/main arm64 Packages [165 kB]
Get:43 http://security.ubuntu.com/ubuntu bionic-security/main arm64 Packages [165 kB]
Get:43 http://security.ubuntu.com/ubuntu bionic-security/main arm64 Packages [165 kB]
Get:43 http://security.ubuntu.com/ubuntu bionic-security/main arm64 Packages [165 kB]
Get:43 http://security.ubuntu.com/ubuntu bionic-security/main arm64 Packages [165 kB]
Get:43 http://security.ubuntu.com/ubuntu bionic-security/main arm64 Packages [165 kB]
Get:43 http://security.ubuntu.com/ubuntu bionic-security/main arm64 Packages [165 kB]
Get:43 http://security.ubuntu.com/ubuntu bionic-security/main arm64 Packages [165 kB]
Ign:28 http://us.archive.ubuntu.com/ubuntu bionic/restricted arm64 Packages     
Ign:29 http://us.archive.ubuntu.com/ubuntu bionic/universe arm64 Packages[COLOR=#B26818]      [/COLOR][COLOR=#000000] [/COLOR]
Ign:30 http://us.archive.ubuntu.com/ubuntu bionic/multiverse arm64 Packages
Ign:31 http://us.archive.ubuntu.com/ubuntu bionic-updates/main arm64 Packages
Ign:32 http://us.archive.ubuntu.com/ubuntu bionic-updates/restricted arm64 Packages
Ign:38 http://us.archive.ubuntu.com/ubuntu bionic-updates/universe arm64 Packages
Ign:39 http://us.archive.ubuntu.com/ubuntu bionic-updates/multiverse arm64 Packages
Ign:40 http://us.archive.ubuntu.com/ubuntu bionic-backports/universe arm64 Packages
Ign:43 http://security.ubuntu.com/ubuntu bionic-security/main arm64 Packages
Ign:55 http://security.ubuntu.com/ubuntu bionic-security/universe arm64 Packages
Ign:56 http://security.ubuntu.com/ubuntu bionic-security/multiverse arm64 Packages
Ign:6 http://us.archive.ubuntu.com/ubuntu bionic/main arm64 Packages[COLOR=#B26818]        [/COLOR][COLOR=#000000] [/COLOR]
Ign:28 http://us.archive.ubuntu.com/ubuntu bionic/restricted arm64 Packages  
Ign:29 http://us.archive.ubuntu.com/ubuntu bionic/universe arm64 Packages    
Ign:30 http://us.archive.ubuntu.com/ubuntu bionic/multiverse arm64 Packages  
Ign:31 http://us.archive.ubuntu.com/ubuntu bionic-updates/main arm64 Packages
Ign:32 http://us.archive.ubuntu.com/ubuntu bionic-updates/restricted arm64 Packages
Ign:38 http://us.archive.ubuntu.com/ubuntu bionic-updates/universe arm64 Packages
Ign:39 http://us.archive.ubuntu.com/ubuntu bionic-updates/multiverse arm64 Packages
Ign:43 http://security.ubuntu.com/ubuntu bionic-security/main arm64 Packages
Ign:55 http://security.ubuntu.com/ubuntu bionic-security/universe arm64 Packages
Ign:40 http://us.archive.ubuntu.com/ubuntu bionic-backports/universe arm64 Packages
Err:6 http://us.archive.ubuntu.com/ubuntu bionic/main arm64 Packages    
  404  Not Found [IP: 91.189.91.23 80]
Ign:28 http://us.archive.ubuntu.com/ubuntu bionic/restricted arm64 Packages
Ign:29 http://us.archive.ubuntu.com/ubuntu bionic/universe arm64 Packages
Ign:30 http://us.archive.ubuntu.com/ubuntu bionic/multiverse arm64 Packages
Err:31 http://us.archive.ubuntu.com/ubuntu bionic-updates/main arm64 Packages
  404  Not Found [IP: 91.189.91.23 80]
Ign:32 http://us.archive.ubuntu.com/ubuntu bionic-updates/restricted arm64 Packages
Ign:38 http://us.archive.ubuntu.com/ubuntu bionic-updates/universe arm64 Packages
Ign:56 http://security.ubuntu.com/ubuntu bionic-security/multiverse arm64 Packages
Ign:43 http://security.ubuntu.com/ubuntu bionic-security/main arm64 Packages
Ign:39 http://us.archive.ubuntu.com/ubuntu bionic-updates/multiverse arm64 Packages
Err:40 http://us.archive.ubuntu.com/ubuntu bionic-backports/universe arm64 Packages
  404  Not Found [IP: 91.189.91.23 80]
Ign:55 http://security.ubuntu.com/ubuntu bionic-security/universe arm64 Packages
Ign:56 http://security.ubuntu.com/ubuntu bionic-security/multiverse arm64 Packages
Err:43 http://security.ubuntu.com/ubuntu bionic-security/main arm64 Packages
  404  Not Found [IP: 91.189.88.161 80]
Ign:55 http://security.ubuntu.com/ubuntu bionic-security/universe arm64 Packages
Ign:56 http://security.ubuntu.com/ubuntu bionic-security/multiverse arm64 Packages
Fetched 247 kB in 2s (138 kB/s)
Reading package lists... Done
E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/bionic/main/binary-arm64/Packages  404  No
t Found [IP: 91.189.91.23 80]
E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/bionic-updates/main/binary-arm64/Packages 
 404  Not Found [IP: 91.189.91.23 80]
E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/bionic-backports/universe/binary-arm64/Pac
kages  404  Not Found [IP: 91.189.91.23 80]
E: Failed to fetch http://security.ubuntu.com/ubuntu/dists/bionic-security/main/binary-arm64/Packages  
404  Not Found [IP: 91.189.88.161 80]
E: Some index files failed to download. They have been ignored, or old ones used instead.

[/FONT]
```

Another thing to note is that when I try to add a key from a keyserver I get this unusual message. not sure if related. 

```
[FONT=monospace][COLOR=#000000]sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 8AC93F7A[/COLOR]
Executing: /tmp/apt-key-gpghome.1hkAWtLwfB/gpg.1.sh --keyserver keyserver.ubuntu.com --recv-keys 8AC93F
7A
gpg: key B14278488AC93F7A: "Totally Legit Signing Key <mallory@example.org>" not changed
gpg: key 2836CB0A8AC93F7A: 4 signatures not checked due to missing keys
gpg: key 2836CB0A8AC93F7A: "Launchpad Kubuntu Updates" not changed
gpg: Total number processed: 2
gpg:              unchanged: 2

[/FONT]
```

---

### Post by deadflowr on 2018-12-18
There are no arm64 packages in main. (And I'm not sure about universe backports arm64 packages)
You can grab those from the ports repo.
Do you need arm64 packages?

(I see you also have i386(32-bit) packages enabled, but it's unclear what you require
post back
```
dpkg --print-foreign-architectures
dpkg --print-architecture

```
The first wil print out non-default archs and second the systems default arch.)

**Edit:**
deja-vu:
[https://ubuntuforums.org/showthread.php?t=2407619]("https://ubuntuforums.org/showthread.php?t=2407619")

---

### Post by Ziad_Arafat on 2018-12-18
That's interesting. It could be related. I enabled i386 because I was trying to install wine staging at one point but gave up. The arm64 packages could either be when I was compiling something for my raspberry pi or it could be related to the nvidia Jetson SDK I installed. (nvidia jetson is an arm based embedded platform.). Anyhow.

```

i386
arm64 
```

and for the default it's
```

amd64

```

and just to be clear here are my specs. Added them to main post as well. 

```

[FONT=monospace]System:   Host: ziad-Desktop Kernel: 4.15.0-34-generic x86_64 bits: 64 gcc: 7.3.0
Desktop: KDE Plasma 5.12.7 (Qt 5.9.5) Distro: Ubuntu 18.04.1 LTS
Machine:  Device: desktop System: Hewlett-Packard product: HP Z400 Workstation serial: N/A
Mobo: Hewlett-Packard model: 0B4Ch v: D serial: N/A
BIOS: Hewlett-Packard v: 786G3 v03.54 date: 11/02/2011
CPU:      6 core Intel Xeon X5650 (-MT-MCP-) arch: Nehalem rev.2 cache: 12288 KB
flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 31997
clock speeds:max: 2661 MHz 1: 2666 MHz 2: 2666 MHz 3: 2666 MHz 4: 2666 MHz 5: 2666 MHz 6: 2666 MHz
7: 2666 MHz 8: 2666 MHz 9: 2666 MHz 10: 2666 MHz 11: 2666 MHz 12: 2666 MHz                                                
Graphics: Card: NVIDIA GP106 [GeForce GTX 1060 6GB] bus-ID: 0f:00.0                                                                 
Display Server: x11 (X.Org 1.19.6 ) drivers: nvidia (unloaded: modesetting,fbdev,vesa,nouveau)                            
Resolution: 1920x1080@60.00hz, 1920x1080@60.00hz                                                                          
OpenGL: renderer: N/A version: N/A Direct Render: N/A                                                                     
Audio:    Card-1 NVIDIA GP106 High Definition Audio Controller driver: snd_hda_intel bus-ID: 0f:00.1                                
Card-2 Intel 82801JI (ICH10 Family) HD Audio Controller driver: snd_hda_intel bus-ID: 00:1b.0                             
Sound: Advanced Linux Sound Architecture v: k4.15.0-34-generic                                                            
Network:  Card: Broadcom Limited NetXtreme BCM5764M Gigabit Ethernet PCIe driver: tg3 v: 3.137 bus-ID: 01:00.0                      
IF: enp1s0 state: up speed: 100 Mbps duplex: half mac: <filter>                                                           
Drives:   HDD Total Size: 2500.5GB (12.0% used)                                                                                     
ID-1: /dev/sda model: Hitachi_HUA72202 size: 2000.4GB                                                                     
ID-2: /dev/sdb model: Samsung_SSD_860 size: 500.1GB                                                                       
Partition:ID-1: / size: 458G used: 281G (65%) fs: ext4 dev: /dev/sdb1                                                               
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present                                                               
Sensors:  System Temperatures: cpu: 35.0C mobo: N/A gpu: 0.0:29C                                                                    
Fan Speeds (in rpm): cpu: N/A                                                                                             
Info:     Processes: 337 Uptime: 2:25 Memory: 4737.4/24086.5MB Init: systemd runlevel: 5 Gcc sys: 6.4.0                             
Client: Shell (bash 4.4.191) inxi:2.3.56 
[/FONT]
```

---

### Post by Ziad_Arafat on 2018-12-18
I see your edit now. Same exact situation it seems.

---

### Post by Ziad_Arafat on 2018-12-18
[HR][/HR]Ok so the fixes in the other thread have completely solved the issue. I just added ```
[FONT=monospace][COLOR=#B26818]deb[/COLOR][COLOR=#54FFFF]** [arch=arm64] **[/COLOR][COLOR=#54FF54]**http://ports.ubuntu.com/ubuntu-ports**[/COLOR][COLOR=#FF5454]** bionic**[/COLOR][COLOR=#FF54FF]** main universe **[/COLOR][/FONT]
```[FONT=monospace][COLOR=#FF54FF][/COLOR][/FONT]and added  [FONT=monospace][COLOR=#54FFFF]**[arch=amd64,i386] **[/COLOR][/FONT]after "deb"  on all the regular repos. [FONT=monospace]
[/FONT]

---

