---
title: "2-minute Boot with Ubuntu 21.04..."
date: 2022-01-08
forum: General Help
---

### Post by 2CV67 on 2022-01-08
Can somebody please guide me to troubleshoot very long boot time (over 2 minutes) with Ubuntu 21.04?

I found several threads about this but they were mostly pretty old so maybe no longer relevant.
I would prefer to start with up-to-date information if possible.

Thanks for any suggestions!

---

### Post by oldfred on 2022-01-08
Post in code tags the output from these commands:
systemd-analyze
And just first page or top items from:
systemd-analyze blame

[https://ubuntuforums.org/showthread.php?t=2450783](https://ubuntuforums.org/showthread.php?t=2450783)

---

### Post by 2CV67 on 2022-01-08
Thanks, oldfred:

```
chris@AcerTC:~$ systemd-analyze
Startup finished in 8.144s (firmware) + 6.067s (loader) + 5.222s (kernel) + 1min 58.004s (userspace) = 2min 17.439s 
graphical.target reached after 1min 57.964s in userspace
chris@AcerTC:~$ 
```

```
chris@AcerTC:~$ systemd-analyze blame
1min 8.895s plymouth-quit-wait.service
1min 1.546s resolvconf-pull-resolved.service
    27.625s dev-sda7.device
    24.937s udisks2.service
    17.118s snapd.service
    16.325s networkd-dispatcher.service
    15.398s cups.service
    14.362s accounts-daemon.service
    10.527s NetworkManager-wait-online.service
    10.474s dev-loop12.device
    10.427s polkit.service
     9.948s dev-loop14.device
     9.840s dev-loop21.device
     9.653s dev-loop11.device
     9.582s dev-loop20.device
     9.534s dev-loop24.device
     9.526s NetworkManager.service
     9.522s avahi-daemon.service
     9.478s dev-loop10.device
     9.264s power-profiles-daemon.service
     9.237s dev-loop8.device
     9.217s dev-loop25.device
     9.143s dev-loop17.device
lines 1-23...skipping...
1min 8.895s plymouth-quit-wait.service
1min 1.546s resolvconf-pull-resolved.service
```

---

### Post by tea for one on 2022-01-08
Have you tried a previous kernel?

Secondly, Ubuntu 21.04 reaches end of life on 20 January 2022 therefore it may be beneficial to move to a supported version?

---

### Post by oldfred on 2022-01-08
I have in my notes that 21.04 expires EoL 2022-01.
You may want to upgrade first and then resolve issues.

I do change quiet splash to noplymouth in /etc/default/grub.
G[FONT=monospace][COLOR=#000000]RUB_CMDLINE_LINUX_DEFAULT="noplymouth"
But then you see entire boot process which I do prefer so I know it is working rather than just see the Ubuntu icon.

Not familar with[/COLOR][/FONT] resolvconf-pull-resolved.service[FONT=monospace], but seems to be related to network issue. 
Have they turned off repositories for 21.04? Or a DHCP issue?

What is sda7? Are you mounting in fstab & have a valid UUID to mount?

I do not use snaps and have NVMe boot drive. Kubuntu is a bit more lightweight than Ubuntu, more of a middle weight system.

[/FONT]```
[FONT=monospace][COLOR=#54ff54]**fred@z170-focal-k**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ systemd-analyze [/COLOR]
Startup finished in 24min 55.347s (firmware) + 3.655s (loader) + 3.700s (kernel) + 5.587s (userspace) = 25min 8.291s  
graphical.target reached after 5.573s in userspace
[/FONT]
```

This system was shutdown for  a month while up north for Christmas. So I think that is why my firmware shows as slow. But I get usable screen in the 5 seconds.

---

### Post by 2CV67 on 2022-01-21
> **oldfred said:**
> I have in my notes that 21.04 expires EoL 2022-01.
You may want to upgrade first and then resolve issues.

What is sda7? Are you mounting in fstab & have a valid UUID to mount?

I upgraded to 21.10 & still have the same boot time.

sda7 is the partition with my main (slow boot) Ubuntu - was 21.04, now 21.10.

I don't really understand fstab or UUID, but here is the output from sudo blkid which I hope answers the question!
```
chris@AcerTC:~$ sudo blkid
[sudo] password for chris: 
/dev/sda8: UUID="eafb3efb-2b4d-4dbe-b157-9b4c294d889c" TYPE="swap" PARTUUID="2bb927e3-b381-43bf-af50-499d616b5b69"
/dev/sda7: UUID="4520a9c5-025c-4a61-a895-23ebdad720b9" BLOCK_SIZE="4096" TYPE="ext4" PARTUUID="8bd455dd-fcfb-4d90-bc88-1ce29e8b23f2"
/dev/loop0: TYPE="squashfs"
/dev/loop1: TYPE="squashfs"
/dev/loop2: TYPE="squashfs"
/dev/loop3: TYPE="squashfs"
/dev/loop4: TYPE="squashfs"
/dev/loop5: TYPE="squashfs"
/dev/loop6: TYPE="squashfs"
/dev/loop7: TYPE="squashfs"
/dev/sda1: LABEL="Recovery" BLOCK_SIZE="512" UUID="50C6D271C6D25736" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="e8add274-1dba-4b02-a8f3-7122f74553b7"
/dev/sda2: LABEL_FATBOOT="ESP" LABEL="ESP" UUID="5CD4-9C1F" BLOCK_SIZE="512" TYPE="vfat" PARTLABEL="EFI system partition" PARTUUID="c92b95c7-6f8c-4b52-b317-a9fda21b73af"
/dev/sda3: PARTLABEL="Microsoft reserved partition" PARTUUID="0b4c5b9c-df2d-4ec5-ae15-73788596136c"
/dev/sda4: LABEL="Acer" BLOCK_SIZE="512" UUID="185CD6025CD5DB18" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="1e5100d8-2a7a-43d4-a93a-84e8941ca1b9"
/dev/sda5: LABEL="DATA" BLOCK_SIZE="512" UUID="A034D77234D749C4" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="c3e0fe98-f227-405a-bd34-fe7cbfb54300"
/dev/sda6: LABEL="Push Button Reset" BLOCK_SIZE="512" UUID="BEECD8F1ECD8A545" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="6c65cd5c-9443-4029-8c80-ee142f992e60"
/dev/sda9: LABEL="Old LTS-16.04" UUID="733193de-c7ce-468a-a93d-48c40e96a40b" BLOCK_SIZE="4096" TYPE="ext4" PARTUUID="478e3ac6-4fcd-4606-a300-1d9a423f8b30"
/dev/sda10: UUID="6f7e8b5e-b6b1-4884-b784-95690b5350ee" BLOCK_SIZE="4096" TYPE="ext4" PARTUUID="87305cc9-17de-4f3f-b742-5e1cca9b8ea0"
/dev/sdb1: LABEL="Toshi-A" UUID="e2fc69be-9081-42c6-a17b-cba4dea5cac7" BLOCK_SIZE="4096" TYPE="ext4" PARTUUID="e8911d49-01"
/dev/loop8: TYPE="squashfs"
/dev/loop9: TYPE="squashfs"
/dev/loop10: TYPE="squashfs"
/dev/loop11: TYPE="squashfs"
/dev/loop12: TYPE="squashfs"
/dev/loop13: TYPE="squashfs"
/dev/loop14: TYPE="squashfs"
/dev/loop15: TYPE="squashfs"
/dev/loop16: TYPE="squashfs"
/dev/loop17: TYPE="squashfs"
/dev/loop18: TYPE="squashfs"
/dev/loop19: TYPE="squashfs"
/dev/loop20: TYPE="squashfs"
/dev/loop21: TYPE="squashfs"
/dev/loop22: TYPE="squashfs"
/dev/loop23: TYPE="squashfs"
/dev/loop24: TYPE="squashfs"
/dev/loop25: TYPE="squashfs"
/dev/loop26: TYPE="squashfs"
/dev/loop27: TYPE="squashfs"
chris@AcerTC:~$ 

```

---

### Post by Holger_Gehrke on 2022-01-21
I think all those "squashfs" mounts might have something to do with your problem. Unless I'm guessing completely wrong, those are snap packages. A snap file is mainly a compressed file system image - that's what squashfs is - which gets partially decompressed in memory and mounted. In my experience each snap you've got installed adds something to the time it takes to boot (mounting, applying an app-armour profile, setting up the various links ... it all adds up). That's one of the reasons I avoid snaps whenever possible ...

Holger

---

### Post by oldfred on 2022-01-21
Is this one of the AcerTC-100 in your signature? 

It shows 4GB RAM as default, is that what you have? And just the HDD?
May want to see full hardware specs:
Hardware doucumentation script
[https://github.com/UbuntuForums/system-info](https://github.com/UbuntuForums/system-info)
This is a one line command using && and \ to combine commands.
```
wget -N -t 5 -T 10 https://github.com/UbuntuForums/system-info/raw/main/system-info && \
chmod +x system-info && \
./system-info

```

And just to confirm boot configuration:
Please copy & paste the pastebin link to the Bootinfo summary report ( do not post report), do not run the auto fix till reviewed.Lets see details, use ppa version with your USB installer (2nd option) or any working install,  not Boot-Repair ISO
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
Boot-Repair uses separate lines to install & run.
```
sudo apt-get update
sudo add-apt-repository ppa:yannubuntu/boot-repair
sudo apt-get update
sudo apt-get install -y boot-repair && boot-repair


```

Do you use all the snap packages?

If older lightweight system a different flavor may work better.
sudo apt-get update
sudo add-apt-repository ppa:yannubuntu/boot-repair
sudo apt-get update
sudo apt-get install -y boot-repair && boot-repair

I switched to Kubuntu 20.04LTS and was surprised it even worked on my old 2006 laptop with only 1.5GB of RAM. Somewhat slow, but that laptop was never fast. Kubuntu is more of a middleweight system.

---

### Post by GhX6GZMB on 2022-01-21
snap strikes again.

---

### Post by 2CV67 on 2022-01-22
> **oldfred said:**
> Is this one of the AcerTC-100 in your signature? 

It shows 4GB RAM as default, is that what you have? And just the HDD?
May want to see full hardware specs:

Please copy & paste the pastebin link to the Bootinfo summary report ( do not post report)

Do you use all the snap packages?

Yes - the AcerTC-100 with 4GB RAM & just the HDD.
Here are the hardware specs:
```
Starting the Ubuntu Forums 'system-info' Report: 2022-01-22  14:57:36 CET (+0100)
	Part of the Ama-gi Project
	Version: 01.00-02, Script Date: 2021.12.06

---------------------------------------------------------------
Main Complaint: Slow boot
Problem Description:  2 minutes
---------- General Computer Specifications:

  --- Computer/CPU Information from 'lshw -C cpu' --- 
*-Cpu
    Description: CPU
    Product: AMD A4-5000 APU with Radeon(TM) HD Graphics
    Vendor: Advanced Micro Devices [AMD]
    Physical id: 1b
    Bus info: cpu@0
    Version: AMD A4-5000 APU with Radeon(TM) HD Graphics
    Slot: P0
    Size: 1067MHz
    Capacity: 1500MHz
    Width: 64 bits
    Clock: 100MHz
    Capabilities: lm fpu fpu_exception wp vme de pse tsc msr pae mce cx8 
        apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht 
        syscall nx mmxext fxsr_opt pdpe1gb rdtscp x86-64 constant_tsc rep_good 
        nopl nonstop_tsc cpuid extd_apicid aperfmperf pni pclmulqdq monitor 
        ssse3 cx16 sse4_1 sse4_2 movbe popcnt aes xsave avx f16c lahf_lm 
        cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch 
        osvw ibs skinit wdt topoext perfctr_nb bpext perfctr_llc hw_pstate 
        proc_feedback ssbd vmmcall bmi1 xsaveopt arat npt lbrv svm_lock 
        nrip_save tsc_scale flushbyasid decodeassists pausefilter pfthreshold 
        overflow_recov cpufreq
    Configuration: cores=4 enabledcores=4 threads=4

computer
    Description: Desktop Computer
    Product: Aspire TC-100
    Vendor: Acer
    Serial: [REMOVED]
    Width: 64 bits
    Capabilities: smbios-2.7 dmi-2.7 smp vsyscall32
    Configuration:
        administrator_password=disabled
        boot=normal
        chassis=desktop
        family=Acer Desktop
        power-on_password=disabled
        uuid=[REMOVED]

------------------ SMBIOS Information from '/sys/class/dmi/id/' 
Bios Vendor:         American Megatrends Inc.
Bios Version:        P11-A4
Bios Release:        4.6
Board Vendor:        Acer
Board Name:          Aspire TC-100
Board Version:       
Board Serial:        DBSR2CN00242284CFA30A1
Board Asset Tag:     

Current boot mode:   UEFI Firmware mode
SecureBoot disabled


---------- Memory Information:
               total        used        free      shared  buff/cache   available
Mem:           3.3Gi       1.7Gi       151Mi        14Mi       1.5Gi       1.3Gi
Swap:          2.0Gi        30Mi       1.9Gi

---------- IP Address Information:
  --- IP Address Information from 'ip addr' --- 
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    inet [REMOVED]
    inet6 [REMOVED]
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    inet [REMOVED]
    inet6 [REMOVED]
    inet6 [REMOVED]
    inet6 [REMOVED]
3: wlan0: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN group default qlen 1000

  --- Internet Connection Status from 'ping [various addresses]' --- 
Connected to Internet with DNS

  --- Network Device Status Summary from 'ip addr' ---  
These Network Devices are up:
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000

  --- Hostname from 'hostname --fqdn' ---  
The 'Hostname' of the computer system is: AcerTC


---------- File system specs from 'df -h':
Filesystem     Type  Size  Used Avail Use% Mounted on
/dev/sda7      ext4  354G  158G  179G  47% /
/dev/sda2      vfat  296M   56M  241M  19% /boot/efi

---------- Disk/Partition Information From 'fdisk':

Disk /dev/sda: 931.51 GiB, 1000204886016 bytes, 1953525168 sectors
Disk model: WDC WD10EZEX-21M
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: D790A53C-6A44-484A-91FF-D11483FE4E47

Device          Start        End   Sectors   Size Type
/dev/sda1        2048     821247    819200   400M Windows recovery environment
/dev/sda2      821248    1435647    614400   300M EFI System
/dev/sda3     1435648    1697791    262144   128M Microsoft reserved
/dev/sda4     1697792  206497791 204800000  97.7G Microsoft basic data
/dev/sda5   960983040 1834250239 873267200 416.4G Microsoft basic data
/dev/sda6  1920268288 1953523711  33255424  15.9G Windows recovery environment
/dev/sda7   206497792  960982166 754484375 359.8G Microsoft basic data
/dev/sda8  1916172288 1920268287   4096000     2G Linux swap
/dev/sda9  1875212288 1916172287  40960000  19.5G Linux filesystem
/dev/sda10 1834250240 1875212287  40962048  19.5G Linux filesystem

Partition table entries are not in disk order.

Disk /dev/sdb: 931.51 GiB, 1000204883968 bytes, 1953525164 sectors
Disk model: External USB 3.0
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xe8911d49

Device     Boot Start        End    Sectors   Size Id Type
/dev/sdb1        2048 1953523711 1953521664 931.5G 83 Linux


---------- Disk/Partition Information From 'lsblk':
NAME      SIZE FSTYPE   LABEL             MOUNTPOINT                     MODEL
sda     931.5G                                                           WDC_WD10EZEX-21M2NA0
|-sda1    400M ntfs     Recovery                                         
|-sda2    300M vfat     ESP               /boot/efi                      
|-sda3    128M                                                           
|-sda4   97.7G ntfs     Acer                                             
|-sda5  416.4G ntfs     DATA                                             
|-sda6   15.9G ntfs     Push Button Reset                                
|-sda7  359.8G ext4                       /                              
|-sda8      2G swap                       [SWAP]                         
|-sda9   19.5G ext4     Old LTS-16.04                                    
`-sda10  19.5G ext4                                                      
sdb     931.5G                                                           External_USB_3.0
`-sdb1  931.5G ext4     Toshi-A                                          
sr0      1024M                                                           ATAPI_DVD_A_DH16ACSH
   ------- 'lsblk' information continued ...
NAME    HOTPLUG PARTUUID                             UUID
sda           0                                      
|-sda1        0 e8add274-1dba-4b02-a8f3-7122f74553b7 50C6D271C6D25736
|-sda2        0 c92b95c7-6f8c-4b52-b317-a9fda21b73af 5CD4-9C1F
|-sda3        0 0b4c5b9c-df2d-4ec5-ae15-73788596136c 
|-sda4        0 1e5100d8-2a7a-43d4-a93a-84e8941ca1b9 185CD6025CD5DB18
|-sda5        0 c3e0fe98-f227-405a-bd34-fe7cbfb54300 A034D77234D749C4
|-sda6        0 6c65cd5c-9443-4029-8c80-ee142f992e60 BEECD8F1ECD8A545
|-sda7        0 8bd455dd-fcfb-4d90-bc88-1ce29e8b23f2 4520a9c5-025c-4a61-a895-23ebdad720b9
|-sda8        0 2bb927e3-b381-43bf-af50-499d616b5b69 eafb3efb-2b4d-4dbe-b157-9b4c294d889c
|-sda9        0 478e3ac6-4fcd-4606-a300-1d9a423f8b30 733193de-c7ce-468a-a93d-48c40e96a40b
`-sda10       0 87305cc9-17de-4f3f-b742-5e1cca9b8ea0 6f7e8b5e-b6b1-4884-b784-95690b5350ee
sdb           1                                      
`-sdb1        1 e8911d49-01                          e2fc69be-9081-42c6-a17b-cba4dea5cac7
sr0           1                                      

---------- Mount Details of '/etc/fstab':
UUID=4520a9c5-025c-4a61-a895-23ebdad720b9 /               ext4    errors=remount-ro 0       1
UUID=5CD4-9C1F  /boot/efi       vfat    defaults        0       1
UUID=eafb3efb-2b4d-4dbe-b157-9b4c294d889c none            swap    sw              0       0

---------- Current Mount Details of 'mount':
/dev/sda2 on /boot/efi type vfat (rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/sda7 on / type ext4 (rw,relatime,errors=remount-ro)

---------- USB Information from 'lsusb -t -v':
/:  Bus 06.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/2p, 5000M
    ID 1d6b:0003 Linux Foundation 3.0 root hub
/:  Bus 05.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/2p, 480M
    ID 1d6b:0002 Linux Foundation 2.0 root hub
/:  Bus 04.Port 1: Dev 1, Class=root_hub, Driver=ohci-pci/4p, 12M
    ID 1d6b:0001 Linux Foundation 1.1 root hub
/:  Bus 03.Port 1: Dev 1, Class=root_hub, Driver=ohci-pci/4p, 12M
    ID 1d6b:0001 Linux Foundation 1.1 root hub
    |__ Port 1: Dev 2, If 0, Class=Human Interface Device, Driver=usbhid, 1.5M
        ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
/:  Bus 02.Port 1: Dev 1, Class=root_hub, Driver=ehci-pci/4p, 480M
    ID 1d6b:0002 Linux Foundation 2.0 root hub
    |__ Port 3: Dev 2, If 0, Class=Vendor Specific Class, Driver=rtsx_usb, 480M
        ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
/:  Bus 01.Port 1: Dev 1, Class=root_hub, Driver=ehci-pci/4p, 480M
    ID 1d6b:0002 Linux Foundation 2.0 root hub
    |__ Port 2: Dev 3, If 0, Class=Mass Storage, Driver=usb-storage, 480M
        ID 0480:a00c Toshiba America Inc 
    |__ Port 3: Dev 4, If 0, Class=Vendor Specific Class, Driver=ath9k_htc, 480M
        ID 0cf3:9271 Qualcomm Atheros Communications AR9271 802.11n

---------- Video Details from 'lshw':

  *-display
       description: VGA compatible controller
       product: Kabini [Radeon HD 8330]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 1
       bus info: pci@0000:00:01.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: 
           irq:37 
           memory:c0000000-cfffffff 
           memory:d0000000-d07fffff 
           ioport:f000(size=256) 
           memory:feb00000-feb3ffff 
           memory:c0000-dffff

   --- Graphics Environment Continued from 'various graphics ENVs' ----
The Current Configured Destop is: ubuntu:GNOME 
The Current Desktop Session is: ubuntu-xorg 
The Current X Desktop Information Details from 'xrandr' are: 
Screen 0: minimum 320 x 200, current 1280 x 1024, maximum 16384 x 16384
HDMI-0 disconnected (normal left inverted right x axis y axis)
VGA-0 connected primary 1280x1024+0+0 (normal left inverted right x axis y axis) 338mm x 270mm
The Current Session Type is: x11 
The Current Display Manager is: gdm3
The Current Desktop Theme: 'Yaru'
The Current Virtual TTYs being used are:
	TTY#	Used By
	tty2	gdm-x-session
	tty2	Xorg
	tty2	gnome-session-b

---------- Repository Information from '/etc/apt/sources.list and etc/apt/sources.list.d/':

Sources List:
deb http://fr.archive.ubuntu.com/ubuntu/ impish main restricted
deb-src http://fr.archive.ubuntu.com/ubuntu/ impish main restricted
deb http://fr.archive.ubuntu.com/ubuntu/ impish-updates main restricted
deb-src http://fr.archive.ubuntu.com/ubuntu/ impish-updates main restricted
deb http://fr.archive.ubuntu.com/ubuntu/ impish universe
deb-src http://fr.archive.ubuntu.com/ubuntu/ impish universe
deb http://fr.archive.ubuntu.com/ubuntu/ impish-updates universe
deb-src http://fr.archive.ubuntu.com/ubuntu/ impish-updates universe
deb http://fr.archive.ubuntu.com/ubuntu/ impish multiverse
deb-src http://fr.archive.ubuntu.com/ubuntu/ impish multiverse
deb http://fr.archive.ubuntu.com/ubuntu/ impish-updates multiverse
deb-src http://fr.archive.ubuntu.com/ubuntu/ impish-updates multiverse
deb http://fr.archive.ubuntu.com/ubuntu/ impish-backports main restricted universe multiverse
deb-src http://fr.archive.ubuntu.com/ubuntu/ impish-backports main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu impish-security main restricted
deb-src http://security.ubuntu.com/ubuntu impish-security main restricted
deb http://security.ubuntu.com/ubuntu impish-security universe
deb-src http://security.ubuntu.com/ubuntu impish-security universe
deb http://security.ubuntu.com/ubuntu impish-security multiverse
deb-src http://security.ubuntu.com/ubuntu impish-security multiverse

Sources List from SourcesD:
/etc/apt/sources.list.d/danielrichter2007-grub-customizer-trusty.list:
File had no entries.
/etc/apt/sources.list.d/peterlevi-ppa-trusty.list.save:
File had no entries.
/etc/apt/sources.list.d/dlynch3-ubuntu-ppa-xenial.list.distUpgrade:
File had no entries.
/etc/apt/sources.list.d/dlynch3-ppa-trusty.list:
File had no entries.
/etc/apt/sources.list.d/peterlevi-ubuntu-ppa-utopic.list.save:
File had no entries.
/etc/apt/sources.list.d/dlynch3-ppa-trusty.list.save:
File had no entries.
/etc/apt/sources.list.d/peterlevi-ubuntu-ppa-vivid.list.distUpgrade:
File had no entries.
/etc/apt/sources.list.d/danielrichter2007-ubuntu-grub-customizer-vivid.list:
File had no entries.
/etc/apt/sources.list.d/michael-gruz-ubuntu-canon-trunk-utopic.list.save:
File had no entries.
/etc/apt/sources.list.d/peterlevi-ubuntu-ppa-wily.list.distUpgrade:
deb http://ppa.launchpad.net/peterlevi/ppa/ubuntu wily main
/etc/apt/sources.list.d/ian-berke-ubuntu-ppa-drawers-utopic.list.save:
File had no entries.
/etc/apt/sources.list.d/danielrichter2007-ubuntu-grub-customizer-xenial.list.distUpgrade:
File had no entries.
/etc/apt/sources.list.d/peterlevi-ppa-trusty.list.distUpgrade:
deb http://ppa.launchpad.net/peterlevi/ppa/ubuntu trusty main
/etc/apt/sources.list.d/danielrichter2007-ubuntu-grub-customizer-yakkety.list.distUpgrade:
File had no entries.
/etc/apt/sources.list.d/thomas_tsai-ubuntu-ubuntu-tuxboot-disco.list.save:
File had no entries.
/etc/apt/sources.list.d/michael-gruz-ubuntu-canon-trunk-utopic.list.distUpgrade:
File had no entries.
/etc/apt/sources.list.d/peterlevi-ubuntu-ppa-xenial.list.distUpgrade:
File had no entries.
/etc/apt/sources.list.d/danielrichter2007-ubuntu-grub-customizer-yakkety.list.save:
File had no entries.
/etc/apt/sources.list.d/danielrichter2007-ubuntu-grub-customizer-utopic.list.save:
File had no entries.
/etc/apt/sources.list.d/dlynch3-ppa-trusty.list.distUpgrade:
deb http://ppa.launchpad.net/dlynch3/ppa/ubuntu trusty main
/etc/apt/sources.list.d/danielrichter2007-ubuntu-grub-customizer-vivid.list.distUpgrade:
File had no entries.
/etc/apt/sources.list.d/dlynch3-ubuntu-ppa-wily.list.distUpgrade:
deb http://ppa.launchpad.net/dlynch3/ppa/ubuntu wily main
/etc/apt/sources.list.d/dlynch3-ubuntu-ppa-xenial.list:
File had no entries.
/etc/apt/sources.list.d/danielrichter2007-ubuntu-grub-customizer-zesty.list.distUpgrade:
File had no entries.
/etc/apt/sources.list.d/bneijt-ubuntu-ppa-groovy.list.save:
File had no entries.
/etc/apt/sources.list.d/danielrichter2007-grub-customizer-trusty.list.save:
File had no entries.
/etc/apt/sources.list.d/danielrichter2007-ubuntu-grub-customizer-utopic.list.distUpgrade:
File had no entries.
/etc/apt/sources.list.d/peterlevi-ubuntu-ppa-wily.list.save:
File had no entries.
/etc/apt/sources.list.d/danielrichter2007-ubuntu-grub-customizer-xenial.list.save:
File had no entries.
/etc/apt/sources.list.d/peterlevi-ubuntu-ppa-vivid.list:
File had no entries.
/etc/apt/sources.list.d/dlynch3-ubuntu-ppa-utopic.list.distUpgrade:
File had no entries.
/etc/apt/sources.list.d/dlynch3-ubuntu-ppa-utopic.list:
File had no entries.
/etc/apt/sources.list.d/peterlevi-ubuntu-ppa-wily.list:
File had no entries.
/etc/apt/sources.list.d/danielrichter2007-ubuntu-grub-customizer-zesty.list.save:
File had no entries.
/etc/apt/sources.list.d/peterlevi-ppa-trusty.list:
File had no entries.
/etc/apt/sources.list.d/thomas_tsai-ubuntu-ubuntu-tuxboot-disco.list:
File had no entries.
/etc/apt/sources.list.d/peterlevi-ubuntu-ppa-utopic.list.distUpgrade:
File had no entries.
/etc/apt/sources.list.d/peterlevi-ubuntu-ppa-vivid.list.save:
File had no entries.
/etc/apt/sources.list.d/ian-berke-ppa-drawers-trusty.list.save:
File had no entries.
/etc/apt/sources.list.d/danielrichter2007-ubuntu-grub-customizer-utopic.list:
File had no entries.
/etc/apt/sources.list.d/bneijt-ubuntu-ppa-groovy.list:
File had no entries.
/etc/apt/sources.list.d/peterlevi-ubuntu-ppa-xenial.list:
File had no entries.
/etc/apt/sources.list.d/michael-gruz-ubuntu-canon-trunk-utopic.list:
File had no entries.
/etc/apt/sources.list.d/danielrichter2007-ubuntu-grub-customizer-zesty.list:
File had no entries.
/etc/apt/sources.list.d/ian-berke-ppa-drawers-trusty.list.distUpgrade:
deb http://ppa.launchpad.net/ian-berke/ppa-drawers/ubuntu trusty main
/etc/apt/sources.list.d/danielrichter2007-ubuntu-grub-customizer-wily.list.save:
File had no entries.
/etc/apt/sources.list.d/danielrichter2007-ubuntu-grub-customizer-xenial.list:
File had no entries.
/etc/apt/sources.list.d/dlynch3-ubuntu-ppa-utopic.list.save:
File had no entries.
/etc/apt/sources.list.d/ian-berke-ubuntu-ppa-drawers-utopic.list.distUpgrade:
File had no entries.
/etc/apt/sources.list.d/ian-berke-ubuntu-ppa-drawers-utopic.list:
File had no entries.
/etc/apt/sources.list.d/ian-berke-ppa-drawers-trusty.list:
File had no entries.
/etc/apt/sources.list.d/danielrichter2007-ubuntu-grub-customizer-vivid.list.save:
File had no entries.
/etc/apt/sources.list.d/dlynch3-ubuntu-ppa-xenial.list.save:
File had no entries.
/etc/apt/sources.list.d/danielrichter2007-ubuntu-grub-customizer-wily.list.distUpgrade:
deb http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu wily main
/etc/apt/sources.list.d/danielrichter2007-ubuntu-grub-customizer-yakkety.list:
File had no entries.
/etc/apt/sources.list.d/thomas_tsai-ubuntu-ubuntu-tuxboot-disco.list.distUpgrade:
File had no entries.
/etc/apt/sources.list.d/peterlevi-ubuntu-ppa-utopic.list:
File had no entries.
/etc/apt/sources.list.d/dlynch3-ubuntu-ppa-wily.list:
File had no entries.
/etc/apt/sources.list.d/dlynch3-ubuntu-ppa-wily.list.save:
File had no entries.
/etc/apt/sources.list.d/peterlevi-ubuntu-ppa-xenial.list.save:
File had no entries.
/etc/apt/sources.list.d/danielrichter2007-ubuntu-grub-customizer-wily.list:
File had no entries.
/etc/apt/sources.list.d/danielrichter2007-grub-customizer-trusty.list.distUpgrade:
deb http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu trusty main

---------- Other Details from 'Various':
The current kernel version is:       5.13.0-27-generic 
The current release description is:  Ubuntu 21.10 
Original Installation Date:          2014-10-23+15:38:21 
Original Installation Media: Ubuntu 14.04.1 LTS "Trusty Tahr" - Release amd64 (20140722.2)


These are the current kernel ranges for HWE kernels for this release.
   --- HWE Kernel Reference from 'apt-cache show':
For HWE Package: linux-image-generic-hwe-20.04, Kernel Version: 5.13.0.27.37
For HWE Package: linux-image-generic-hwe-20.04, Kernel Version: 5.13.0.19.30

   --- HWE Package Status from 'dpkg':
HWE package linux-generic-hwe-20.04 was not detected. Please check 
kernel version to verify range

   --- Certified Hardware Platform Status: (By the Ubuntu Wiki Standards)
Ubuntu Certified Hardware Platform. Safe to install 
the Hardware Enablement Stack (HWE).

Currently logged in User(s):
NAME     LINE         TIME             COMMENT
chris    :0           2022-01-22 14:40 (:0)

The User running this script was: chris
uid=1000(chris)
gid=1000(chris)
groups=1000(chris),4(adm),7(lp),24(cdrom),27(sudo),30(dip),46(plugdev),
108(lpadmin),109(scanner),124(sambashare),1001(carolyn),1002(family)

---- Required Programs For Report.
    --- Some Programs This Script Uses Were Missing --- 
    curl

*** End Of Report ***
```
Boot info report:
[https://paste.ubuntu.com/p/F7T485kkh9/]("https://paste.ubuntu.com/p/F7T485kkh9/")

Snaps list:
```
chris@AcerTC:~$ snap list
Name                  Version                     Rev    Tracking         Publisher   Notes
autotrash-unofficial  0.1.5                       5      latest/stable    qkiz        -
bare                  1.0                         5      latest/stable    canonical&#10003;  base
chromium              97.0.4692.99                1878   latest/stable    canonical&#10003;  -
core                  16-2.52.1                   11993  latest/stable    canonical&#10003;  core
core18                20211215                    2284   latest/stable    canonical&#10003;  base
core20                20211129                    1270   latest/stable    canonical&#10003;  base
firefox               96.0.2-1                    886    latest/stable/…  mozilla&#10003;    -
gnome-3-26-1604       3.26.0.20210629             104    latest/stable    canonical&#10003;  -
gnome-3-28-1804       3.28.0-19-g98f9e67.98f9e67  161    latest/stable    canonical&#10003;  -
gnome-3-34-1804       0+git.3556cb3               77     latest/stable    canonical&#10003;  -
gnome-3-38-2004       0+git.cd626d1               87     latest/stable    canonical&#10003;  -
gnome-system-monitor  41.0-5-g91e67f7982          174    latest/stable/…  canonical&#10003;  -
gtk-common-themes     0.1-59-g7bca6ae             1519   latest/stable/…  canonical&#10003;  -
snap-store            3.38.0-66-gbd5b8f7          558    latest/stable/…  canonical&#10003;  -
zoom-client           5.9.1.1380                  167    latest/stable    ogra        -
chris@AcerTC:~$ 

```
I actively use autotrash, firefox, gnome & zoom.
I now avoid Chromium.
I don't really understand the others...

Thanks for your patience!

---

### Post by oldfred on 2022-01-22
Looks like you have upgraded a lot.
You show many ppas but most have no entries.
But some do show entries.
You need to houseclean all the old ppas.

I think that is why I often suggest new install, partially to houseclean old, obsolete cruft & log files so system is clean.
And years ago when updating every 6 months my wife complained about all the changes. So now just use LTS version as main working install, but also install newer versions to test and learn what differences are.

Ubuntu/gnome also has grown a lot to offer features for newer faster systems.
Your older system may be to the point where a lighter weight system would be better.
I like Kubuntu, which is more of a middle weight system. But old 2006 laptop that ran Ubuntu from 2012, would not install 20.04LTS. But Kubuntu 20.04 did install which surprised me. Laptop is retired, all batteries are dead, so just installed 20.04 as test.

Have you do a full houseclean?
Older:
[https://help.ubuntu.com/community/RecoverLostDiskSpace](https://help.ubuntu.com/community/RecoverLostDiskSpace)

---

### Post by 2CV67 on 2022-01-27
Yes - I continue to upgrade rather than fresh-install so long as it works!

I am well aware of less-demanding systems - I have to use Lubuntu to keep the old Netbook running.
So I can go that way when necessary, but don't think I need that yet.

I am fairly careful about removing, for instance, old kernels & emptying trash after x days (autotrash) but have never been encouraged to delete old ppa's.
I was very surprised to see such a long list in the hardware specs in /etc/apt/sources.list.d
The list in SynApt > Other Software only had 16 ppa's & they were nearly all unchecked, so I had assumed they were no handicap...

Anyway, I removed all the ppa's from SynApt.
But they are all still present in sources.list.d!

So I am a bit confused now...

---

### Post by oldfred on 2022-01-27
I would think removing ppa would remove the folder also.
So then Boot-Repair is just seeing the folders.
If ppa folder is empty then you can just manually delete it.

---

### Post by Autodave on 2022-01-27
Yes - I continue to upgrade rather than fresh-install so long as it works!

Hmmm....maybe it isn't working! :-)  I run a bunch of machines.....usually 10 to 15 of them.  I learned a looooong time ago to forget about upgrading to the new LTS and simply just do a clean install.  It saved me so much time and my blood pressure was happy, too.

---

### Post by HermanAB on 2022-01-27
Why reboot? Use suspend.

---

### Post by 2CV67 on 2022-02-03
OK - I think I will draw a line under this one now.

I did a fresh install of 21.10 on a spare partition (still keeping the old version available).

Before making any additions to that empty installation, I had total boot times (switch-to-desk) of 1min 25sec.

After adding most of my old data & applications and switching Firefox from snap to deb, I end up with 1min 51sec.
Systemd-analyze puts it at 1min 28sec, presumably not measuring exactly the same events.

So I assume that is about "normal" for 21.10 on my dated PC.

Quite a contrast with my new Lenovo laptop with SSD & 8GB Ram which boots 21.10 in 12sec...

Thanks to everybody for your help on this one!

---

