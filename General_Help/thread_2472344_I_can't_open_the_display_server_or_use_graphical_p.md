---
title: "I can't open the display server or use graphical programs/load desktop environments"
date: 2022-02-24
forum: General Help
---

### Post by ash22 on 2022-02-24
I suspended network manager to test something and resumed it and now I can't boot into a desktop environment or use anything graphical. I can only use the tty. When I use startx, nothing happens. Ive been looking online for different solutions and a lot of answers said to try xhost +. But that didnt work either. It says
Code:

```
xhost: unable to open display ":0.0"
```

When I echo the display varible, it's empty, so I exported DISPLAY as 0.0 with xhost but it says
Code:
```

Invalid MIT-MAGIC-COOKIE-1 keyxhost: unable to open display ":0.0"
```

When I try to launch mate-session, it says
Code:

```
Invalid MIT-MAGIC-COOKIE-1 keyUnable to init server: could not connect: connection refused
```

When I launch Plasma it says something similar but also says it can't start because Plasma's graphical platform plugin could be initialized. I don't know how to fix it. 

I tried regenerating the .Xauthority file but I get an error when I do that too.
```
xauth generate :0 . trusted no protocool specified unable to open
```
I get an error for every single solution I try

Every time I reboot, there is no $DISPLAY variable set. When I echo $DISPLAY, I just get (''''). It's empty so I export :0.0 to display, but I still get an error that the display can't open.

Do I need to reinstall Ubuntu? Is it not repairable?

---

### Post by Xian on 2022-02-24
If .Xauthority still exists then rename it:
```
cd $HOME
mv .Xauthority old.Xauthority
```

Create/Regenerate file:
```
touch ~/.Xauthority
xauth generate :0 . trusted
```

Any change?

---

### Post by MAFoElffen on 2022-02-25
> **ash22 said:**
> I suspended network manager to test something and resumed it and now I can't boot into a desktop environment or use anything graphical. I can only use the tty. When I use startx, nothing happens. Ive been looking online for different solutions and a lot of answers said to try xhost +. But that didnt work either. It says

How did you "suspend" the network manager?

What version and flavor of Ubuntu are you running?
What Desktop Environment (DE) did you last use successfully? (because it sounds like you might have a few...)
What is your configured Desktop Manager (DE)? (The graphical Login manager...)
Or did you not have a Graphical Login Manager configured?
What is your video GPU?

If you run the UbuntuForums 'system-info' script in my signature line, that will answer most of those questions, more, and give us a good idea of what we are looking at...

I few more questions... Such as-- Have you tried rebooting and does it show the splash and get to a Login Manager?

EDIT--
On your last questions: Do you need to reinstall Ubuntu. Most likely not. Can you repair this? Yes... If you looked at the Graphics Resolution Sticky of mine, in my Signature Line, the Graphics Layer can be repaired in place. If you can get a tty console like you did, your kernel boots and you have a console prompt. As you can see from the date of that sticky, I have over twice that in years of experience with helping people to resolve Graphics Issues.... 
> *"Don't worry. I saw this work once in a cartoon..."*

---

### Post by ash22 on 2022-02-25
That doesn't work

---

### Post by ash22 on 2022-02-25
> **Xian said:**
> If .Xauthority still exists then rename it:
```
cd $HOME
mv .Xauthority old.Xauthority
```

Create/Regenerate file:
```
touch ~/.Xauthority
xauth generate :0 . trusted
```


That doesn't work

---

### Post by MAFoElffen on 2022-02-26
No it wouldn't work that way at all... To try that solution, for what he suspected, there were many missing steps and would leave you in a broken state. Let me explain to get you htrough the missing steps...

Refer to my "Graphics Resolution" Sticky from the Installation and Upgrades Section in my signature line, Post #2 (table Of Contents) links to this: **["Resetting .Xauthority permissions file For Logging into X"]("http://ubuntuforums.org/showpost.php?p=11404605&postcount=766")**

Boils down to this (updated):
```

rm $HOME/.Xauthority* 
touch $HOME/.Xauthority 
chmod 600 ~/.Xauthority
chown $USER $HOME/.Xauthority
sudo reboot

```
What that person had you do was just to move it... Which to XServer, instead of it being there and corrupted, or there with the incorrect permissions, it ended up not being there at all. Whic just movingit, does not create a replacement for, which would work for you... It was missing those steps.

Why did he suggest that? Because XServer cannot start a session unless a user has this file in their home directory, and that is s owned by them, wit the correct permissions. Even, and especially when you are trying to manually start an XSession, this needs to be there and correct...

(And that assumes that you were running XServer, and not Wayland...)

Yes, that was one of my solutions for some things even back in that post, way back in mid 2011... What? yes, I've been supporting XServer since 1988. I have learned a few things along the way. Even though I still give out that solution, there are questions to be answered before having a User do that. You understand that right?

I asked you a few question in my last post to get an idea of what was happening and at what point. I support the Linux Graphics Layer... So I do have an understaning of what happens under the hood for that to work.

As just going out and trying to manually start a session... I need to know what is in place now, and what is being used on what. Do not make any changes yet please. You may have to recover from things you might not need to... For instance, many things have to be in place in a very specific "order". For example; in when it is installed/reinstalled, when it was configured, for the connections to work out.)

Just saying the order of, and what goes to what matters.

---

### Post by ash22 on 2022-02-26
Thanks for the reply

My Ubuntu version is 20.4 and the only environment I can boot into is awesom session, but it can't use any graphics. Programs won't launch and missing icons. The other DEs I use are MATE and Plasma. The graphical login manager that starts after boot is KDE's SDDM.

I suspended the Network Manager in the system monitor and it required the root password.

I ran that script and have the page, how should I share it? Should I  copy it and paste it somewhere? Because it only lets me see the  page.

---

### Post by MAFoElffen on 2022-02-26
If, it is a picture:
While you are trying to post, you go to "Advanced Reply" ... At the bottom of that page, look for the Link that says "Manage Attachments".

Attachments can only be one of these files types:
```

Valid file extensions: bmp bz2 deb doc gif gp3 gp4 gp5 gpl gz jpe jpeg  jpg odg odp ods odt pdf png psd py sh svg tar tg txt xcf zip

```
...and pictures can only be below a certain size, so ensure it is of standard or lower resolution. Many photo/graphics apps can do that for you, or to convert a type to something else.

A window will open > Click "Add Files" button to upload new files... navigate to where the picture file is and "Select" it. Select "Upload". If picture appears in the Lower Left, select "Done". If not, then something is wrong... Such as file type or size.


If it is output you are trying to post, go to that same "Go Advanced" Post page > Press the "#" Icon in the edit toolbar. Copy and paste the output within the CODE Tags...

EDIT: Yes, if you got to SDDM and from there it went to what it is doing, then the ~/.Xauthority file is suspect as the primary culprit, then the local sddm config file (to where it may be pointing to as a DE)...

---

### Post by ash22 on 2022-02-27
Reseting the .Xauthority file didn't fix it either

This is the output of the script

```
Starting the Ubuntu Forums 'system-info' Report: 2022-02-26  11:43:37 GMT (+0000)
    Part of the Ama-gi Project
    Version: 01.00-04, Script Date: 2022.02.24

---------------------------------------------------------------
Main Complaint: Opening the display server
Problem Description:  $DISPLAY varible is not set after rebooting and starting X does not work. Graphical programs will not run.
---------- General Computer Specifications:

  --- Computer/CPU Information from 'lshw -C cpu' --- 
*-Cpu
    Description: CPU
    Product: AMD Ryzen 5 2600 Six-Core Processor
    Vendor: Advanced Micro Devices [AMD]
    Physical id: 26
    Bus info: cpu@0
    Version: AMD Ryzen 5 2600 Six-Core Processor
    Serial: [REMOVED]
    Slot: AM4
    Size: 2265MHz
    Capacity: 3900MHz
    Width: 64 bits
    Clock: 100MHz
    Capabilities: lm fpu fpu_exception wp vme de pse tsc msr pae mce cx8 
        apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht 
        syscall nx mmxext fxsr_opt pdpe1gb rdtscp x86-64 constant_tsc rep_good 
        nopl nonstop_tsc cpuid extd_apicid aperfmperf pni pclmulqdq monitor 
        ssse3 fma cx16 sse4_1 sse4_2 movbe popcnt aes xsave avx f16c rdrand 
        lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 
        3dnowprefetch osvw skinit wdt tce topoext perfctr_core perfctr_nb 
        bpext perfctr_llc mwaitx cpb hw_pstate sme ssbd sev ibpb vmmcall 
        fsgsbase bmi1 avx2 smep bmi2 rdseed adx smap clflushopt sha_ni 
        xsaveopt xsavec xgetbv1 xsaves clzero irperf xsaveerptr arat npt lbrv 
        svm_lock nrip_save tsc_scale vmcb_clean flushbyasid decodeassists 
        pausefilter pfthreshold avic v_vmsave_vmload vgif overflow_recov 
        succor smca cpufreq
    Configuration: cores=6 enabledcores=6 threads=12

computer
    Description: Desktop Computer
    Product: System Product Name (SKU)
    Vendor: System manufacturer
    Version: System Version
    Serial: [REMOVED]
    Width: 64 bits
    Capabilities: smbios-3.1.1 dmi-3.1.1 smp vsyscall32
    Configuration:
        boot=normal
        chassis=desktop
        family=To be filled by O.E.M.
        sku=SKU
        uuid=[REMOVED]

------------------ SMBIOS Information from '/sys/class/dmi/id/' 
Bios Vendor:         American Megatrends Inc.
Bios Version:        2301
Board Vendor:        ASUSTeK COMPUTER INC.
Board Name:          ROG STRIX B450-F GAMING
Board Version:       Rev 1.xx
Board Serial:        181141091008315
Board Asset Tag:     Default string

Current boot mode:   Legacy mode (alias CSM alias BIOS mode)
    This would check / have checked if SecureBoot was enabled or not, 
    and checks if the system BIOS was UEFI or Lagacy only BIOS, 
    but package mokutil was not installed. If you would like to check
    this information, please install 'mokutil' and rerun script.

---------- Memory Information:
              total        used        free      shared  buff/cache   available
Mem:           15Gi       832Mi        10Gi       3.0Mi       4.1Gi        14Gi
Swap:         2.0Gi          0B       2.0Gi

---------- IP Address Information:
  --- IP Address Information from 'ip addr' --- 
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    inet [REMOVED]
    inet6 [REMOVED]
2: enp4s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default qlen 1000
    inet [REMOVED]
    inet6 [REMOVED]
    inet6 [REMOVED]
    inet6 [REMOVED]

  --- Internet Connection Status from 'ping [various addresses]' --- 
Connected to Internet with DNS

  --- Network Device Status Summary from 'ip addr' ---  
These Network Devices are up:
2: enp4s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default qlen 1000

  --- Hostname from 'hostname --fqdn' ---  
The 'Hostname' of the computer system is: boxx


---------- File system specs from 'df -h':
Filesystem     Type      Size  Used Avail Use% Mounted on
/dev/sdb1      ext4      229G  209G  7.9G  97% /
/dev/nvme0n1   ext4      117G   61G   51G  55% /mnt/4b45931c-d7ea-4d58-acaa-47d20dfda66d
/dev/sda2      fuseblk   465G  412G   54G  89% /mnt/8482DBD682DBCB36
/dev/sdc1      fuseblk   932G  779G  153G  84% /mnt/1TB

---------- Disk/Partition Information From 'fdisk':

Disk /dev/nvme0n1: 119.25 GiB, 128035676160 bytes, 250069680 sectors
Disk model: SSSTC CL1-8D128-HP                      
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

Disk /dev/sda: 465.78 GiB, 500107862016 bytes, 976773168 sectors
Disk model: WDC WDS500G2B0A 
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xf3fd52f3

Device     Boot     Start       End   Sectors   Size Id Type
/dev/sda1            2048    718846    716799   350M  7 HPFS/NTFS/exFAT
/dev/sda2  *       718848 975637608 974918761 464.9G  7 HPFS/NTFS/exFAT
/dev/sda3       975638528 976766975   1128448   551M 27 Hidden NTFS WinRE

Disk /dev/sdb: 232.91 GiB, 250059350016 bytes, 488397168 sectors
Disk model: Samsung SSD 850 
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x59eece0a

Device     Boot Start       End   Sectors   Size Id Type
/dev/sdb1        2048 488396799 488394752 232.9G 83 Linux

Disk /dev/sdd: 1.84 TiB, 2000398934016 bytes, 3907029168 sectors
Disk model: SEAGATE ST2000NM
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x03c99ff2

Device     Boot Start        End    Sectors  Size Id Type
/dev/sdd1        2048 3907026943 3907024896  1.8T  7 HPFS/NTFS/exFAT

Disk /dev/sdc: 931.53 GiB, 1000204886016 bytes, 1953525168 sectors
Disk model: SAMSUNG HD103SI 
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xa7e7e8a9

Device     Boot Start        End    Sectors   Size Id Type
/dev/sdc1           2 1953525167 1953525166 931.5G  7 HPFS/NTFS/exFAT


---------- Disk/Partition Information From 'lsblk':
NAME      SIZE FSTYPE   LABEL           MOUNTPOINT                                MODEL
sda     465.8G                                                                    WDC_WDS500G2B0A
|-sda1    350M ntfs     System Reserved                                           
|-sda2  464.9G ntfs                     /mnt/8482DBD682DBCB36                     
`-sda3    551M ntfs                                                               
sdb     232.9G                                                                    Samsung_SSD_850_EVO_250GB
`-sdb1  232.9G ext4                     /                                         
sdc     931.5G                                                                    SAMSUNG_HD103SI
`-sdc1  931.5G ntfs     1Tb Drive       /mnt/1TB                                  
sdd       1.8T                                                                    SEAGATE_ST2000NM0033
`-sdd1    1.8T ntfs     2TB game drive                                            
sr0      1024M                                                                    ASUS_DRW-24F1ST_a
nvme0n1 119.2G ext4     Wine games      /mnt/4b45931c-d7ea-4d58-acaa-47d20dfda66d SSSTC CL1-8D128-HP
   ------- 'lsblk' information continued ...
NAME    HOTPLUG PARTUUID                             UUID
sda           0                                      
|-sda1        0 f3fd52f3-01                          AEAAB0FCAAB0C25F
|-sda2        0 f3fd52f3-02                          8482DBD682DBCB36
`-sda3        0 f3fd52f3-03                          70266E9B266E61D8
sdb           0                                      
`-sdb1        0 59eece0a-01                          5c2b9425-cdab-488a-b848-c936c19ddafd
sdc           0                                      
`-sdc1        0 a7e7e8a9-01                          DC9C1F849C1F587A
sdd           0                                      
`-sdd1        0 03c99ff2-01                          2E36B1AD36B17685
sr0           1                                      
nvme0n1       0                                      4b45931c-d7ea-4d58-acaa-47d20dfda66d

---------- Mount Details of '/etc/fstab':
UUID=5c2b9425-cdab-488a-b848-c936c19ddafd /               ext4    errors=remount-ro 0       1
/swapfile                                 none            swap    sw              0       0
/dev/disk/by-uuid/8482DBD682DBCB36 /mnt/8482DBD682DBCB36 auto nosuid,nodev,nofail,x-gvfs-show,remove_hiberfile 0 0
UUID=DC9C1F849C1F587A /mnt/1TB                           auto nosuid,nodev,nofail,x-gvfs-show 0 0

/dev/disk/by-uuid/2E36B1AD36B17685 /mnt/2E36B1AD36B17685 auto nosuid,nodev,nofail,x-gvfs-show,noauto 0 0
/dev/disk/by-uuid/4b45931c-d7ea-4d58-acaa-47d20dfda66d /mnt/4b45931c-d7ea-4d58-acaa-47d20dfda66d auto nosuid,nodev,nofail,x-gvfs-show 0 0

---------- Current Mount Details of 'mount':
/dev/nvme0n1 on /mnt/4b45931c-d7ea-4d58-acaa-47d20dfda66d type ext4 (rw,nosuid,nodev,relatime,x-gvfs-show)
/dev/sda2 on /mnt/8482DBD682DBCB36 type fuseblk (rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096,x-gvfs-show)
/dev/sdb1 on / type ext4 (rw,relatime,errors=remount-ro)
/dev/sdc1 on /mnt/1TB type fuseblk (rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096,x-gvfs-show)

---------- USB Information from 'lsusb -t -v':
/:  Bus 06.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/4p, 5000M
    ID 1d6b:0003 Linux Foundation 3.0 root hub
/:  Bus 05.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/4p, 480M
    ID 1d6b:0002 Linux Foundation 2.0 root hub
    |__ Port 3: Dev 2, If 0, Class=Human Interface Device, Driver=usbhid, 1.5M
        ID 047d:2048 Kensington Orbit Trackball with Scroll Ring
/:  Bus 04.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/4p, 5000M
    ID 1d6b:0003 Linux Foundation 3.0 root hub
/:  Bus 03.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/4p, 480M
    ID 1d6b:0002 Linux Foundation 2.0 root hub
/:  Bus 02.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/4p, 10000M
    ID 1d6b:0003 Linux Foundation 3.0 root hub
/:  Bus 01.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/10p, 480M
    ID 1d6b:0002 Linux Foundation 2.0 root hub
    |__ Port 6: Dev 2, If 0, Class=Human Interface Device, Driver=usbhid, 1.5M
        ID 1c4f:0024 SiGma Micro 
    |__ Port 6: Dev 2, If 1, Class=Human Interface Device, Driver=usbhid, 1.5M
        ID 1c4f:0024 SiGma Micro 

---------- Video Details from 'lshw':

  *-display
       description: VGA compatible controller
       product: Tonga PRO [Radeon R9 285/380]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:09:00.0
       version: f1
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=amdgpu latency=0
       resources: 
           irq:92 
           memory:e0000000-efffffff 
           memory:f0000000-f01fffff 
           ioport:d000(size=256) 
           memory:fce00000-fce3ffff 
           memory:c0000-dffff

   --- Graphics Environment Continued from 'various graphics ENVs' ----
The Current Configured Desktop is: <Not Populated> 
The Current Desktop Session is: <Not Populated> 
The Current Session Type is: tty 
The Current Display Manager is: 
The Current Desktop Theme: <None Configured>
The Current Virtual TTYs being used are:
    TTY#    Used By
    tty1    Xorg
    tty2    login
    tty2    fish
    tty2    system-info
    tty2    system-info
    tty2    sed
    tty2    system-info
    tty2    ps
    tty2    awk

---------- Repository Information from '/etc/apt/sources.list and etc/apt/sources.list.d/':

Sources List:
deb http://gb.archive.ubuntu.com/ubuntu/ focal main
deb http://gb.archive.ubuntu.com/ubuntu/ focal-updates main
deb-src http://gb.archive.ubuntu.com/ubuntu/ bionic-updates main restricted
deb http://gb.archive.ubuntu.com/ubuntu/ focal universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ bionic universe
deb http://gb.archive.ubuntu.com/ubuntu/ focal-updates universe
deb http://gb.archive.ubuntu.com/ubuntu/ focal multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ focal-updates multiverse
deb http://archive.canonical.com/ubuntu bionic partner
deb http://security.ubuntu.com/ubuntu focal-security main
deb http://security.ubuntu.com/ubuntu focal-security universe
deb http://security.ubuntu.com/ubuntu focal-security multiverse

Sources List from SourcesD:
/etc/apt/sources.list.d/braewoods-ubuntu-ungoogled-chromium-bionic.list:
File had no entries.
/etc/apt/sources.list.d/alexlarsson-ubuntu-flatpak-bionic.list.save:
File had no entries.
/etc/apt/sources.list.d/brave-browser-release-bionic.list.distUpgrade:
deb [arch=amd64] https://brave-browser-apt-release.s3.brave.com/ bionic main
/etc/apt/sources.list.d/teejee2008-ubuntu-ppa-bionic.list:
File had no entries.
/etc/apt/sources.list.d/papirus-ubuntu-papirus-bionic.list.distUpgrade:
deb http://ppa.launchpad.net/papirus/papirus/ubuntu bionic main
/etc/apt/sources.list.d/kxstudio-debian-ppas.list.save:
File had no entries.
/etc/apt/sources.list.d/teejee2008-ubuntu-ppa-bionic.list.save:
File had no entries.
/etc/apt/sources.list.d/jonaski-ubuntu-strawberry-focal.list:
deb http://ppa.launchpad.net/jonaski/strawberry/ubuntu focal main
/etc/apt/sources.list.d/kxstudio-debian.new.list.save:
deb http://ppa.launchpad.net/kxstudio-debian/libs/ubuntu trusty main
deb http://ppa.launchpad.net/kxstudio-debian/music/ubuntu trusty main
deb http://ppa.launchpad.net/kxstudio-debian/plugins/ubuntu trusty main
deb http://ppa.launchpad.net/kxstudio-debian/apps/ubuntu trusty main
deb http://ppa.launchpad.net/kxstudio-debian/kxstudio/ubuntu trusty main
/etc/apt/sources.list.d/kxstudio-debian-ppas.list:
File had no entries.
/etc/apt/sources.list.d/nordvpn.list.distUpgrade:
deb https://repo.nordvpn.com/deb/nordvpn/debian stable main
/etc/apt/sources.list.d/braewoods-ubuntu-ungoogled-chromium-bionic.list.distUpgrade:
File had no entries.
/etc/apt/sources.list.d/braewoods-ubuntu-ungoogled-chromium-bionic.list.save:
File had no entries.
/etc/apt/sources.list.d/damentz-ubuntu-liquorix-focal.list.save:
deb http://ppa.launchpad.net/damentz/liquorix/ubuntu focal main
/etc/apt/sources.list.d/kxstudio-debian-ubuntu-ubuntus-bionic.list.save:
deb-src http://ppa.launchpad.net/kxstudio-debian/ubuntus/ubuntu bionic main
/etc/apt/sources.list.d/inkscape_dev-ubuntu-stable-bionic.list.distUpgrade:
deb http://ppa.launchpad.net/inkscape.dev/stable/ubuntu bionic main
/etc/apt/sources.list.d/xanmod-kernel.list:
deb http://deb.xanmod.org releases main
/etc/apt/sources.list.d/kisak-ubuntu-kisak-mesa-bionic.list.distUpgrade:
deb http://ppa.launchpad.net/kisak/kisak-mesa/ubuntu bionic main
/etc/apt/sources.list.d/nathan-renniewaldock-ubuntu-flux-bionic.list:
File had no entries.
/etc/apt/sources.list.d/elthariel-ubuntu-audio-focal.list.save:
deb http://ppa.launchpad.net/elthariel/audio/ubuntu focal main
/etc/apt/sources.list.d/kxstudio-debian-ubuntu-ubuntus-bionic.list:
deb-src http://ppa.launchpad.net/kxstudio-debian/ubuntus/ubuntu bionic main
/etc/apt/sources.list.d/kxstudio-external.list:
File had no entries.
/etc/apt/sources.list.d/vivaldi.list:
File had no entries.
/etc/apt/sources.list.d/nathan-renniewaldock-ubuntu-flux-bionic.list.distUpgrade:
deb http://ppa.launchpad.net/nathan-renniewaldock/flux/ubuntu bionic main
/etc/apt/sources.list.d/flexiondotorg-ubuntu-mangohud-focal.list.save:
deb http://ppa.launchpad.net/flexiondotorg/mangohud/ubuntu focal main
/etc/apt/sources.list.d/brave-browser-release-bionic.list:
File had no entries.
/etc/apt/sources.list.d/papirus-ubuntu-papirus-bionic.list:
File had no entries.
/etc/apt/sources.list.d/kxstudio-debian-ubuntu-ubuntus-bionic.list.distUpgrade:
deb http://ppa.launchpad.net/kxstudio-debian/ubuntus/ubuntu bionic main
/etc/apt/sources.list.d/elthariel-ubuntu-audio-focal.list:
deb http://ppa.launchpad.net/elthariel/audio/ubuntu focal main
/etc/apt/sources.list.d/papirus-ubuntu-papirus-bionic.list.save:
File had no entries.
/etc/apt/sources.list.d/nathan-renniewaldock-ubuntu-flux-bionic.list.save:
File had no entries.
/etc/apt/sources.list.d/kxstudio-external.list.distUpgrade:
deb [arch=amd64,i386] https://kx.studio/repo/ stable free
deb [arch=amd64,i386] https://kx.studio/repo/ gcc5 free
/etc/apt/sources.list.d/jonaski-ubuntu-strawberry-focal.list.save:
deb http://ppa.launchpad.net/jonaski/strawberry/ubuntu focal main
/etc/apt/sources.list.d/nordvpn.list:
File had no entries.
/etc/apt/sources.list.d/inkscape_dev-ubuntu-stable-bionic.list.save:
File had no entries.
/etc/apt/sources.list.d/kxstudio-external.list.save:
File had no entries.
/etc/apt/sources.list.d/brave-browser-release.list:
deb [signed-by=/usr/share/keyrings/brave-browser-archive-keyring.gpg arch=amd64] https://brave-browser-apt-release.s3.brave.com/ stable main
/etc/apt/sources.list.d/xanmod-kernel.list.save:
deb http://deb.xanmod.org releases main
/etc/apt/sources.list.d/flexiondotorg-ubuntu-mangohud-focal.list:
deb http://ppa.launchpad.net/flexiondotorg/mangohud/ubuntu focal main
/etc/apt/sources.list.d/kxstudio-debian.list.save:
deb [arch=amd64,i386] http://ppa.launchpad.net/kxstudio-debian/libs/ubuntu lucid main
deb [arch=amd64,i386] http://ppa.launchpad.net/kxstudio-debian/music/ubuntu lucid main
deb [arch=amd64,i386] http://ppa.launchpad.net/kxstudio-debian/plugins/ubuntu lucid main
deb [arch=amd64,i386] http://ppa.launchpad.net/kxstudio-debian/apps/ubuntu lucid main
deb [arch=amd64,i386] http://ppa.launchpad.net/kxstudio-debian/kxstudio/ubuntu lucid main
/etc/apt/sources.list.d/openmw-ubuntu-openmw-focal.list:
deb http://ppa.launchpad.net/openmw/openmw/ubuntu focal main
/etc/apt/sources.list.d/teejee2008-ubuntu-ppa-bionic.list.distUpgrade:
deb http://ppa.launchpad.net/teejee2008/ppa/ubuntu bionic main
/etc/apt/sources.list.d/damentz-ubuntu-liquorix-focal.list:
deb http://ppa.launchpad.net/damentz/liquorix/ubuntu focal main
/etc/apt/sources.list.d/kisak-ubuntu-kisak-mesa-bionic.list.save:
deb-src http://ppa.launchpad.net/kisak/kisak-mesa/ubuntu bionic main
/etc/apt/sources.list.d/kxstudio-debian-ppas.list.distUpgrade:
deb http://ppa.launchpad.net/kxstudio-debian/libs/ubuntu bionic main
deb http://ppa.launchpad.net/kxstudio-debian/music/ubuntu bionic main
deb http://ppa.launchpad.net/kxstudio-debian/plugins/ubuntu bionic main
deb http://ppa.launchpad.net/kxstudio-debian/apps/ubuntu bionic main
deb http://ppa.launchpad.net/kxstudio-debian/kxstudio/ubuntu bionic main
/etc/apt/sources.list.d/dolphin-emu-ubuntu-ppa-focal.list:
deb http://ppa.launchpad.net/dolphin-emu/ppa/ubuntu focal main
/etc/apt/sources.list.d/kxstudio-free.list.save:
deb [arch=amd64,i386] http://kxstudio.linuxaudio.org/repo/ stable free
/etc/apt/sources.list.d/liquorix.list.save:
File had no entries.
/etc/apt/sources.list.d/openmw-ubuntu-openmw-focal.list.save:
deb http://ppa.launchpad.net/openmw/openmw/ubuntu focal main
/etc/apt/sources.list.d/alexlarsson-ubuntu-flatpak-bionic.list.distUpgrade:
deb http://ppa.launchpad.net/alexlarsson/flatpak/ubuntu bionic main
/etc/apt/sources.list.d/kisak-ubuntu-kisak-mesa-bionic.list:
deb-src http://ppa.launchpad.net/kisak/kisak-mesa/ubuntu bionic main
/etc/apt/sources.list.d/inkscape_dev-ubuntu-stable-bionic.list:
File had no entries.
/etc/apt/sources.list.d/vivaldi.list.distUpgrade:
deb http://repo.vivaldi.com/stable/deb/ stable main
/etc/apt/sources.list.d/vivaldi.list.save:
File had no entries.
/etc/apt/sources.list.d/lutris-team-ubuntu-lutris-focal.list:
deb http://ppa.launchpad.net/lutris-team/lutris/ubuntu focal main
/etc/apt/sources.list.d/lutris-team-ubuntu-lutris-focal.list.save:
deb http://ppa.launchpad.net/lutris-team/lutris/ubuntu focal main
/etc/apt/sources.list.d/alexlarsson-ubuntu-flatpak-bionic.list:
File had no entries.
/etc/apt/sources.list.d/nordvpn.list.save:
File had no entries.
/etc/apt/sources.list.d/brave-browser-release-bionic.list.save:
File had no entries.

---------- Other Details from 'Various':
The current kernel version is:       5.4.0-100-generic 
The current release description is:  Ubuntu 20.04.4 LTS 
Original Installation Date:          2018-10-22+23:16:35 
Original Installation Media: Ubuntu-MATE 18.04.1 LTS "Bionic Beaver" - Release amd64 (20180725)


These are the current kernel ranges for HWE kernels for this release.
   --- HWE Kernel Reference from 'apt-cache show':
For HWE Package: linux-image-generic-hwe-20.04, Kernel Version: 5.13.0.30.33
For HWE Package: linux-image-generic-hwe-20.04, Kernel Version: 5.4.0.26.32

   --- HWE Package Status from 'dpkg':
HWE package linux-generic-hwe-20.04 was not detected. Please check 
kernel version to verify range

   --- Certified Hardware Platform Status: (By the Ubuntu Wiki Standards)
Ubuntu Certified Hardware Platform. Safe to install 
the Hardware Enablement Stack (HWE).

   --- User Installed Package List:
0ad                    kolourpaint
apparmor-utils                konqueror
apt-transport-https            ksysguard
ardour                    kvantum
arduino                    kwin-x11
audacious                kxstudio-repos
audacity                kylin-burner
avldrums.lv2                latte-dock
awesome                    libappindicator-dev
bb                    libappindicator1
bison                    libasound2-dev
brave-browser                libdbus-1-dev
brave-keyring                libdvd-pkg
build-essential                libdvdcss-dev
cargo                    libdvdcss2
carla                    libjcat1
carla-bridge-win64            libllvm12:i386
clipit                    libncursesw5-dev
cmatrix                    libobasis6.2-base
cmus                    libobasis6.2-calc
cowsay                    libobasis6.2-core
curl                    libobasis6.2-draw
deja-dup                libobasis6.2-en-us
deluge                    libobasis6.2-extension-beanshell-sc
drumkv1                    libobasis6.2-extension-javascript-s
duplicity                libobasis6.2-extension-mediawiki-pu
ecm                    libobasis6.2-extension-nlpsolver
emacs                    libobasis6.2-extension-pdf-import
emacs-gtk                libobasis6.2-extension-report-build
equivs                    libobasis6.2-firebird
expect                    libobasis6.2-gnome-integration
feathernotes                libobasis6.2-graphicfilter
featherpad                libobasis6.2-images
ffmpegthumbs                libobasis6.2-impress
figlet                    libobasis6.2-kde-integration
filelight                libobasis6.2-librelogo
fish                    libobasis6.2-libreofficekit-data
flatpak                    libobasis6.2-math
flex                    libobasis6.2-ogltrans
fluxgui                    libobasis6.2-onlineupdate
gconf2                    libobasis6.2-ooofonts
gigedit                    libobasis6.2-ooolinguistic
gimp-help-common            libobasis6.2-postgresql-sdbc
gimp-help-en                libobasis6.2-python-script-provider
git                    libobasis6.2-pyuno
gnome-disk-utility            libobasis6.2-writer
golang                    libobasis6.2-xsltfilter
gparted                    libolm-dev
groff                    libpam0g-dev
grub-customizer                libpulse-dev
gstreamer1.0-libav            libreadline-dev
gwenview                libreoffice
gzdoom                    libreoffice-style-tango
htop                    libreoffice6.2
hydrogen                libreoffice6.2-base
inkscape                libreoffice6.2-calc
jackd                    libreoffice6.2-debian-menus
k3b                    libreoffice6.2-dict-en
kde-plasma-desktop            libreoffice6.2-dict-es
kde-spectacle                libreoffice6.2-dict-fr
kdeconnect                libreoffice6.2-draw
kdenlive                libreoffice6.2-en-us
keepass2                libreoffice6.2-impress
kio                    libreoffice6.2-math
kio-extras                libreoffice6.2-ure
klystrack                libreoffice6.2-writer
libsdl-ttf2.0-0                nitrogen
libsensors-config            nm-tray
libsensors5:i386            nnn
libsnmp35                nordvpn
libssl-dev                nordvpn-release
links2                    npm
linux-headers-4.8.10-040810        ocs-url
linux-headers-4.8.10-040810-generic openmw
linux-headers-5.10.27-xanmod1        openmw-launcher
linux-headers-5.10.28-xanmod1        packaging-dev
linux-headers-5.10.32-xanmod1        pass
linux-headers-5.10.33-xanmod1        pavucontrol
linux-headers-5.4.0-56            pcsx2:i386
linux-headers-5.4.0-56-lowlatency   petri-foo
linux-headers-5.4.0-60            plasma-discover-backend-flatpak
linux-headers-5.4.0-60-generic        plasma-pa
linux-headers-5.4.0-60-lowlatency   polkit-kde-agent-1
linux-headers-5.4.102-xanmod1        polyphone
linux-headers-5.4.108-xanmod1        preload
linux-image-4.8.10-040810-generic   puredata-core
linux-image-5.4.0-56-lowlatency        puredata-doc
linux-image-5.4.0-60-generic        python-is-python3
linux-image-5.4.0-60-lowlatency        python-pygments
linux-image-5.4.102-xanmod1        python3-pip
linux-image-5.4.108-xanmod1        qapt-deb-installer
linux-lowlatency            qbittorrent
linux-modules-5.4.0-56-lowlatency   qcomicbook
linux-modules-5.4.0-60-generic        qlipper
linux-modules-5.4.0-60-lowlatency   qpdfview
linux-modules-extra-5.4.0-60-generi qps
linuxsampler-lv2            qsampler
lmms                    qsynth
lolcat                    qt4-qmake
lutris                    qt5-qmake
lximage-qt                qt5-style-kvantum
lxqt-about                qt5-style-kvantum-themes
lxqt-admin                qt5ct
lxqt-branding-debian            qterminal
lxqt-config                qutebrowser
lxqt-globalkeys                redshift
lxqt-notificationd            ripgrep
lxqt-openssh-askpass            rosegarden
lxqt-qtplugin                samplv1-lv2
lxqt-runner                sc
lxqt-sudo                screenfetch
lxqt-system-theme            screengrab
lxqt-theme-debian            sddm
lxqt-themes                sddm-theme-breeze
mailutils                smartmontools
make                    smplayer
mangohud                smtube
mencoder                spotifyd
mesa-vulkan-drivers            steam-devices
mesa-vulkan-drivers:i386        steam-installer
meteo-qt                steam:i386
milkytracker                stow
mpd                    strawberry
mpv                    surge
muse                    sxiv
musescore3                synaptic
mutter                    testdisk
ncmpcpp                    thunderbird
neofetch                tlp
nestopia                tmux
net.downloadhelper.coapp        toilet
newsboat                torbrowser-launcher
trash-cli                wine32:i386
tty-clock                wine64
ubuntustudio-installer            wine64-tools
ubuntustudio-lowlatency-settings    winetricks
ubuntustudio-publishing            wmctrl
vifm                    xbindkeys
vlc-plugin-notify            xdg-desktop-portal
vlc-plugin-samba            xdg-desktop-portal-kde
vulkan-utils                xfwm4
w3m                    xscreensaver
w3m-img                    yoshimi
weechat                    youtube-dl
winbind                    zathura
wine                    zathura-cb
wine-stable                zsh

Currently logged in User(s):
NAME     LINE         TIME         COMMENT
trashly  tty2         Feb 26 11:32

The User running this script was: trashly
uid=1000(trashly)
gid=1000(trashly)
groups=1000(trashly),4(adm),20(dialout),24(cdrom),27(sudo),29(audio),
30(dip),46(plugdev),118(lpadmin),128(sambashare)

---- Required Programs For Report.
    --- Some Programs This Script Uses Were Missing --- 
    mokutil
    pastebinit

*** End Of Report ***
```

---

### Post by MAFoElffen on 2022-02-27
Looking through the report... But also going to need to get ready for work soon. I may need to get an answer to you later...

Initially, I don't see anything jumping out at me, for your specific problem... But there are some things that would cause other things. Looking through it to see what may be related to what is your 'chief complaint' and not be sidelined/distracked by those.

EDIT:
I see that XOrg XServer started, but it never made it to the Desktop Environment, so is hung there in that graphics session. That is where that is stuck currently...

---

### Post by MAFoElffen on 2022-03-01
You have tried adding 'nomodeset' to the grub boot line, so it is not your video driver. You have renewed your .Xauthority file, so it is not a permissions problem...

At the Grub Boot Menu, using the same method for editing the Linux Kernel Boot line, adding and trying 'nomodeset'... You could alternately try the boot parameter 'amdgpu.dc=0', then <Cntrl><X> to continue the boot process to see if that helped... But I am thinking, try that next, if that doesn't help, then we need to go on and dig deeper.  

The order of installation and connections of is as follows:
[LIST]
[*]Display Engine (XServer or Wayland), 
[*]If Xserver, then Xinit... 
[*]DM (Display Manager [the graphical login manager]- SDDM. etc.) 
[*]DE (Desktop Environment- Plasma, etc.) 
[/LIST]

I have a plan. I think the connections between the pieces of might have gotten 'confused'. Each part of this plan, starts from the least invasive to more invasive...

In the first part of the plan, try 
```

sudo dpkg --configure -a

```
This will try to reconfigure all that is installed... It knows the order it needs to do things, and how. Let it go through everything them. On successful completion, reboot to test... if that does not work, then on to the next step....

Next would try to reconfigure each piece in order
```

sudo dpkg --configure xorg-xserver
sudo dpkg --configure xinit
sudo dpkg --configure sddm
sudo dpkg --configure plasma-desktop

```
This does the same as above, but tells it to do it in the order, We are telling it, to those specific packages... On successful completion, reboot and test. If that doesn't work...

What I am thinking,and have seem work, it that if you reinstall the pieces of your graphics layer, in order, then it will reinstall everything needed to get everything reconnected (including the soft and hard links). 

What I do not know is the desktops you may have installed...
```

ls /usr/share/xsessions/

```
That will list all your installed desktops.

Then do
```

sudo apt update
sudo apt install --reinstall xorg-xserver xinint
sudo apt install --reinstall sddm
sudo apt install --reinstall plasma-desktop

```
Which will reinstall XServer, xinit, sddm and plasma.desktop in order... At successful completion, reboot and test.

If at any time, if one of those commands do not complete 'successfully', stop and post the error, and we will go from there to resolve that.

---

### Post by ash22 on 2022-03-01
I tried the "sudo dpkg --reconfigure -a" command but got an error that said "--reconfigure" is an unkown option.

I also tried ```
dpkg-reconfigure -a
``` but then it just gave another error:
```
Unknown option: a
```

So I couldn't try any of those steps

---

### Post by MAFoElffen on 2022-03-05
Dang. My fault on that...

There was a change in the commands between a few versions... And I was in a hurry and had my own typo's there (sorry). My mind was thinking one thing, and fingers typing another. I went back and edited the commands in the previous post for you.
```

sudo dpkg --configure -a
# OR
sudo dpkg-reconfigure -all

```
But the later command (dpkg-reconfigure), with the --all flag stopped working sometime around 16.04 LTS... After they changed it.

---

### Post by ash22 on 2022-03-06
I get an error from that command too

```
dpkg: error processing package xorg-xserver (--configure)
No package named 'xorg-xserver' is installed, cannot configure

```

Would I need to do it on one of the "xserver-xorg-video" packages? Because there are different ones that are installed and I wouldn't know which one to try them on.

---

### Post by MAFoElffen on 2022-03-06
I just checked what is current for Ubuntu... Dang.

Substitute 'xserver-xorg' instead of 'xorg-xserver'

---

### Post by ash22 on 2022-03-07
What I got was
```
dpkg: error processing package xserver-xorg (--configure):
package xserver-xorg is already installed and configured
errors were encountered while processing:
xerver-xorg

```

---

### Post by MAFoElffen on 2022-03-08
That is only one line from Post #11... Did the other in that same Code block return the same? If they did, then reinstall those individual packages according to the commands in the next Code Block there in that Post...

The idea there was to reconnect any unconnected between them... Starting with the least invasive to more... Even if you reinstall those packages, that does not affect your personal data, installed aplications or the core system.

---

### Post by ash22 on 2022-03-08
> Did the other in that same Code block return the same?
Yeah, it happened with all of them

---

### Post by MAFoElffen on 2022-03-09
And what happened when you did these?
```

sudo apt update
sudo apt install --reinstall xorg-xserver xinint
sudo apt install --reinstall sddm
sudo apt install --reinstall plasma-desktop

```

---

### Post by ash22 on 2022-03-10
> **MAFoElffen said:**
> And what happened when you did these?
```

sudo apt update
sudo apt install --reinstall xorg-xserver xinint
sudo apt install --reinstall sddm
sudo apt install --reinstall plasma-desktop

```

They reinstalled but I still couldn't open the xserver

---

### Post by MAFoElffen on 2022-03-10
So the connections are made. The only thing left is the graphics driver... and it is 'amdgpu' (Tonga PRO [Radeon R9 285/380]), which the driver is internal in the Linux kernel.

Confirm a few thing for me, that we have tried or not, so we can try other things:

[LIST]
[*]You have tried the rescue menu to try to boot with safe graphics. 
[*]You have edited the Linux boot line and used 'nomodeset' as a boot parameter 
[*]You have edited the Linux boot line and used 'amdgpu.dc=0' as a boot parameter. 
[/LIST]
 

For graphics, you have: Tonga PRO [Radeon R9 285/380]

In current Linux Kernel (where the amdgpu driver is) and Newer AMD graphics, while using the 'amdgpu' driver, DT is needed, so in the newer kernels, DT is set to be on by default. But your card does not support that... So DT on yours,  _not for your graphics card and older AMD/Radeon GPU's_, DT needs to be turned off. It is a translation layer in newer AMD graphics cards, which used to be referred to as DAL. 

Your GPU card does not support that... So it should be put into the /etc/default/grub file, line "GRUB_CMDLINE_LINUX_DEFAULT" after quiet splash, add 'amdgpu.dt=0', save/exit, and run 'update-grub'... So that it turns that off for your video card... Try that in this way and see if it helps. If it helps or not for this current problem... It eventually needs to be set this way anyways.

---

### Post by ash22 on 2022-03-13
The 'amdgpu.dc=0' line got it working :o. I've added the line in my GRUB file and now I can use graphics and desktop environments again. Do you know what could have made DT turn on?

---

