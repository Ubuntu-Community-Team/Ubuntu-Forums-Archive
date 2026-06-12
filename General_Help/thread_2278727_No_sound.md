---
title: "No sound"
date: 2015-05-14
forum: General Help
---

### Post by mathieu.leonardon on 2015-05-14
Hello, I have a similar problem on my Ubuntu 15.04. Everything was working before yesterday. But suddenly I have no more sound output. So I look into System Settings / Sound. In There is no output device in the list under "play sound through". Moreover, there is nothing in the Input list. Other fact : videos are playing too fast on youtube. All the solutions to similar problems given on forum don't work for me. Mpeg4 Videos play at normal speed. No sound neither. 

I am following [URL="https://help.ubuntu.com/community/SoundTroubleshootingProcedure"]https://help.ubuntu.com/community/SoundTroubleshootingProcedure
[/URL]
I ran "wget -O alsa-info.sh [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh) && chmod +x ./alsa-info.sh && ./alsa-info.sh"

The output is here [http://www.alsa-project.org/db/?f=b9168baa2696cb40cb152d77e106234540bf3607](http://www.alsa-project.org/db/?f=b9168baa2696cb40cb152d77e106234540bf3607)


Then I ran this command proposed on step 4 : 

> 
cat /proc/asound/{version,cards,devices,hwdep,pcm,seq/clients}; sudo rm /etc/asound.conf; sudo rm -r ~/.pulse ~/.asound* ;sudo rm ~/.pulse-cookie; sudo apt-get update; sudo apt-get install aptitude; sudo aptitude install paman gnome-alsamixer libasound2-plugins padevchooser libsdl1.2debian-pulseaudio; sudo lshw -short;ls -lart /dev/snd;  cat /dev/sndstat; lspci -nn; lsusb; sudo which alsactl; sudo fuser -v /dev/dsp /dev/snd/* ; dpkg -S bin/slmodemd; dmesg | egrep 'EMU|probe|emu|ALSA|alsa|ac97|udi|snd|ound|irmware'; sudo /etc/init.d/sl-modem-daemon status; sudo grep model /etc/modprobe.d/* ; sudo dmidecode|egrep 'anufact|roduct|erial|elease'; lsmod | egrep 'snd|usb|midi|udio'; pacmd list-sinks; aplay -l; sudo alsa force-reload;  ubuntu-support-status ; sudo lshw -C sound


And here is the result : 

```
Advanced Linux Sound Architecture Driver Version k3.19.0-16-generic.
 1 [HDMI           ]: HDA-Intel - HDA ATI HDMI
                      HDA ATI HDMI at 0xf0030000 irq 30
  1:        : sequencer
  2: [ 1]   : control
  3: [ 1- 3]: digital audio playback
  4: [ 1- 0]: hardware dependent
 33:        : timer
01-00: HDA Codec 0
01-03: HDMI 0 : HDMI 0 : playback 1
Client info
  cur  clients : 1
  peak clients : 1
  max  clients : 192

Client   0 : "System" [Kernel]
  Port   0 : "Timer" (Rwe-)
  Port   1 : "Announce" (R-e-)
Client  14 : "Midi Through" [Kernel]
  Port   0 : "Midi Through Port-0" (RWe-)
[sudo] password for leonardon: 
rm: cannot remove &#8216;/etc/asound.conf&#8217;: No such file or directory
rm: cannot remove &#8216;/home/leonardon/.pulse&#8217;: No such file or directory
rm: cannot remove &#8216;/home/leonardon/.asound*&#8217;: No such file or directory
rm: cannot remove &#8216;/home/leonardon/.pulse-cookie&#8217;: No such file or directory
Ign [http://dl.google.com](http://dl.google.com) stable InRelease
Ign [http://archive.canonical.com](http://archive.canonical.com) vivid InRelease                               
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg                                    
Hit [http://archive.canonical.com](http://archive.canonical.com) vivid Release.gpg                             
Hit [http://dl.google.com](http://dl.google.com) stable Release                              
Hit [http://archive.canonical.com](http://archive.canonical.com) vivid Release                                 
Hit [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages                            
Ign [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) vivid InRelease                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) vivid-security InRelease                        
Hit [http://archive.canonical.com](http://archive.canonical.com) vivid/partner amd64 Packages                  
Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                             
Hit [http://archive.canonical.com](http://archive.canonical.com) vivid/partner i386 Packages                   
Ign [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) vivid-updates InRelease                       
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) vivid-security Release.gpg [933 B]            
Ign [http://archive.canonical.com](http://archive.canonical.com) vivid/partner Translation-en                  
Ign [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) vivid-backports InRelease            
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) vivid-security Release [63,5 kB]     
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) vivid Release.gpg                            
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                        
Get:3 [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) vivid-updates Release.gpg [933 B]
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) vivid-backports Release.gpg                   
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) vivid-security/main Sources [12,3 kB]
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) vivid Release                                 
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) vivid-security/restricted Sources [28 B]
Get:6 [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) vivid-updates Release [63,5 kB]    
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) vivid-security/universe Sources [4 219 B]
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) vivid-security/multiverse Sources [729 B]     
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) vivid-security/main amd64 Packages [30,5 kB]  
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) vivid-backports Release               
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) vivid-security/restricted amd64 Packages [28 B]
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) vivid/main Sources    
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) vivid-security/universe amd64 Packages [12,6 kB]
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) vivid/restricted Sources                      
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) vivid-security/multiverse amd64 Packages [1 159 B]
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) vivid/universe Sources                        
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) vivid-security/main i386 Packages [30,1 kB]
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) vivid/multiverse Sources                      
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) vivid-security/restricted i386 Packages [28 B]
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) vivid/main amd64 Packages                     
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) vivid-security/universe i386 Packages [12,6 kB]
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) vivid/restricted amd64 Packages               
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) vivid-security/multiverse i386 Packages [1 410 B]
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) vivid/universe amd64 Packages                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) vivid-security/main Translation-en 
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) vivid/multiverse amd64 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) vivid-security/multiverse Translation-en
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) vivid/main i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) vivid-security/restricted Translation-en
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) vivid/restricted i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) vivid-security/universe Translation-en
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) vivid/universe i386 Packages 
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) vivid/multiverse i386 Packages
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) vivid/main Translation-en
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) vivid/multiverse Translation-en
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) vivid/restricted Translation-en
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) vivid/universe Translation-en
Get:17 [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) vivid-updates/main Sources [25,9 kB]
Get:18 [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) vivid-updates/restricted Sources [28 B]
Get:19 [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) vivid-updates/universe Sources [8 990 B]
Get:20 [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) vivid-updates/multiverse Sources [729 B]
Get:21 [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) vivid-updates/main amd64 Packages [55,8 kB]
Get:22 [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) vivid-updates/restricted amd64 Packages [28 B]
Get:23 [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) vivid-updates/universe amd64 Packages [30,4 kB]
Get:24 [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) vivid-updates/multiverse amd64 Packages [1 159 B]
Get:25 [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) vivid-updates/main i386 Packages [55,4 kB]
Get:26 [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) vivid-updates/restricted i386 Packages [28 B]
Get:27 [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) vivid-updates/universe i386 Packages [30,4 kB]
Get:28 [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) vivid-updates/multiverse i386 Packages [1 410 B]
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) vivid-updates/main Translation-en
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) vivid-updates/multiverse Translation-en
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) vivid-updates/restricted Translation-en
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) vivid-updates/universe Translation-en
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) vivid-backports/main Sources
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) vivid-backports/restricted Sources
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) vivid-backports/universe Sources              
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) vivid-backports/multiverse Sources            
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) vivid-backports/main amd64 Packages           
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) vivid-backports/restricted amd64 Packages     
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) vivid-backports/universe amd64 Packages       
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) vivid-backports/multiverse amd64 Packages     
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) vivid-backports/main i386 Packages            
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) vivid-backports/restricted i386 Packages      
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) vivid-backports/universe i386 Packages        
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) vivid-backports/multiverse i386 Packages      
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) vivid-backports/main Translation-en           
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) vivid-backports/multiverse Translation-en     
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) vivid-backports/restricted Translation-en     
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) vivid-backports/universe Translation-en       
Fetched 445 kB in 8s (55,1 kB/s)                                               
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
aptitude is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
No candidate version found for libsdl1.2debian-pulseaudio
No candidate version found for libsdl1.2debian-pulseaudio
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B of archives. After unpacking 0 B will be used.
                                         
H/W path         Device      Class          Description
=======================================================
                             system         Computer
/0                           bus            Motherboard
/0/0                         memory         3808MiB System memory
/0/1                         processor      Intel(R) Core(TM) i3 CPU       M 330
/0/100                       bridge         Core Processor DRAM Controller
/0/100/1                     bridge         Core Processor PCI Express x16 Root 
/0/100/1/0                   display        RV710/M92 [Mobility Radeon HD 4530/4
/0/100/1/0.1                 multimedia     RV710/730 HDMI Audio [Radeon HD 4000
/0/100/16                    communication  5 Series/3400 Series Chipset HECI Co
/0/100/1a                    bus            5 Series/3400 Series Chipset USB2 En
/0/100/1a/1      usb1        bus            EHCI Host Controller
/0/100/1a/1/1                bus            Integrated Rate Matching Hub
/0/100/1a/1/1/2              multimedia     USB 2.0 Camera
/0/100/1a/1/1/6              communication  Broadcom Bluetooth Device
/0/100/1b                    multimedia     5 Series/3400 Series Chipset High De
/0/100/1c                    bridge         5 Series/3400 Series Chipset PCI Exp
/0/100/1c/0      wlan0       network        AR9285 Wireless Network Adapter (PCI
/0/100/1c.1                  bridge         5 Series/3400 Series Chipset PCI Exp
/0/100/1c.1/0                generic        MMC/SD Host Controller
/0/100/1c.1/0.1              generic        R5U2xx (R5U230 / R5U231 / R5U241) [M
/0/100/1c.1/0.4              generic        MMC/SD Host Controller
/0/100/1c.2                  bridge         5 Series/3400 Series Chipset PCI Exp
/0/100/1c.2/0    eth0        network        Yukon Optima 88E8059 [PCIe Gigabit E
/0/100/1c.5                  bridge         5 Series/3400 Series Chipset PCI Exp
/0/100/1d                    bus            5 Series/3400 Series Chipset USB2 En
/0/100/1d/1      usb2        bus            EHCI Host Controller
/0/100/1d/1/1                bus            Integrated Rate Matching Hub
/0/100/1e                    bridge         82801 Mobile PCI Bridge
/0/100/1f                    bridge         Mobile 5 Series Chipset LPC Interfac
/0/100/1f.2                  storage        5 Series/3400 Series Chipset 4 port 
/0/100/1f.3                  bus            5 Series/3400 Series Chipset SMBus C
/0/101                       bridge         Core Processor QuickPath Architectur
/0/102                       bridge         Core Processor QuickPath Architectur
/0/103                       bridge         Core Processor QPI Link 0
/0/104                       bridge         1st Generation Core Processor QPI Ph
/0/105                       bridge         1st Generation Core Processor Reserv
/0/106                       bridge         1st Generation Core Processor Reserv
/0/2             scsi0       storage        
/0/2/0.0.0       /dev/sda    disk           480GB Crucial_CT480M50
/0/2/0.0.0/1     /dev/sda1   volume         341GiB EXT4 volume
/0/2/0.0.0/2     /dev/sda2   volume         101GiB Windows NTFS volume
/0/2/0.0.0/3     /dev/sda3   volume         3948MiB Extended partition
/0/2/0.0.0/3/5   /dev/sda5   volume         3948MiB Linux swap / Solaris partiti
/0/3             scsi1       storage        
/0/3/0.0.0       /dev/cdrom  disk           DVDRAM GT20N
total 0
crw-rw----+  1 root audio 116, 33 mai   14 15:28 timer
crw-rw----+  1 root audio 116,  1 mai   14 15:28 seq
crw-rw----+  1 root audio 116,  4 mai   14 15:28 hwC1D0
crw-rw----+  1 root audio 116,  2 mai   14 15:28 controlC1
drwxr-xr-x   2 root root       60 mai   14 15:28 by-path
drwxr-xr-x   3 root root      160 mai   14 15:28 .
crw-rw----+  1 root audio 116,  3 mai   14 15:28 pcmC1D3p
drwxr-xr-x  20 root root     4480 mai   14 15:40 ..
cat: /dev/sndstat: No such file or directory
00:00.0 Host bridge [0600]: Intel Corporation Core Processor DRAM Controller [8086:0044] (rev 02)
00:01.0 PCI bridge [0604]: Intel Corporation Core Processor PCI Express x16 Root Port [8086:0045] (rev 02)
00:16.0 Communication controller [0780]: Intel Corporation 5 Series/3400 Series Chipset HECI Controller [8086:3b64] (rev 06)
00:1a.0 USB controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b3c] (rev 05)
00:1b.0 Audio device [0403]: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio [8086:3b56] (rev 05)
00:1c.0 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 [8086:3b42] (rev 05)
00:1c.1 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 [8086:3b44] (rev 05)
00:1c.2 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 [8086:3b46] (rev 05)
00:1c.5 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 [8086:3b4c] (rev 05)
00:1d.0 USB controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b34] (rev 05)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev a5)
00:1f.0 ISA bridge [0601]: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller [8086:3b09] (rev 05)
00:1f.2 SATA controller [0106]: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller [8086:3b29] (rev 05)
00:1f.3 SMBus [0c05]: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller [8086:3b30] (rev 05)
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] RV710/M92 [Mobility Radeon HD 4530/4570/545v] [1002:9553]
01:00.1 Audio device [0403]: Advanced Micro Devices, Inc. [AMD/ATI] RV710/730 HDMI Audio [Radeon HD 4000 series] [1002:aa38]
02:00.0 Network controller [0280]: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
03:00.0 SD Host controller [0805]: Ricoh Co Ltd MMC/SD Host Controller [1180:e822]
03:00.1 System peripheral [0880]: Ricoh Co Ltd R5U2xx (R5U230 / R5U231 / R5U241) [Memory Stick Host Controller] [1180:e230]
03:00.4 SD Host controller [0805]: Ricoh Co Ltd MMC/SD Host Controller [1180:e822]
04:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. Yukon Optima 88E8059 [PCIe Gigabit Ethernet Controller with AVB] [11ab:4381] (rev 11)
3f:00.0 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers [8086:2c62] (rev 02)
3f:00.1 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture System Address Decoder [8086:2d01] (rev 02)
3f:02.0 Host bridge [0600]: Intel Corporation Core Processor QPI Link 0 [8086:2d10] (rev 02)
3f:02.1 Host bridge [0600]: Intel Corporation 1st Generation Core Processor QPI Physical 0 [8086:2d11] (rev 02)
3f:02.2 Host bridge [0600]: Intel Corporation 1st Generation Core Processor Reserved [8086:2d12] (rev 02)
3f:02.3 Host bridge [0600]: Intel Corporation 1st Generation Core Processor Reserved [8086:2d13] (rev 02)
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 0489:e00f Foxconn / Hon Hai Foxconn T77H114 BCM2070 [Single-Chip Bluetooth 2.1 + EDR Adapter]
Bus 001 Device 007: ID 064e:a213 Suyin Corp. 
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
/usr/sbin/alsactl
Specified filename /dev/dsp does not exist.
                     USER        PID ACCESS COMMAND
/dev/snd/controlC1:  leonardon   2184 F.... pulseaudio
dpkg-query: no path found matching pattern *bin/slmodemd*
[    0.000000] AGP: No AGP bridge found
[    0.000000] found SMP MP-table at [mem 0x000fc980-0x000fc98f] mapped at [ffff8800000fc980]
[    0.000000] No NUMA configuration found
[    0.000000] AGP: No AGP bridge found
[    0.246357] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.766493] pnp: PnP ACPI: found 5 devices
[    4.370479] audit: initializing netlink subsys (disabled)
[    4.370499] audit: type=2000 audit(1431610117.256:1): initialized
[    4.392446] libphy: Fixed MDIO Bus: probed
[    4.408560] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    4.408759] hub 1-0:1.0: USB hub found
[    4.424700] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    4.424913] hub 2-0:1.0: USB hub found
[    4.432424] PCCT header not found.
[    4.432426] ACPI PCC probe failed.
[    4.452851] ima: No TPM chip found, activating TPM-bypass!
[    4.455626] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    4.507991] sdhci-pci 0000:03:00.0: SDHCI controller found [1180:e822] (rev 0)
[    4.508614] sdhci-pci 0000:03:00.0: No vmmc regulator found
[    4.508617] sdhci-pci 0000:03:00.0: No vqmmc regulator found
[    4.510815] sdhci-pci 0000:03:00.4: SDHCI controller found [1180:e822] (rev 0)
[    4.511047] sdhci-pci 0000:03:00.4: No vmmc regulator found
[    4.511050] sdhci-pci 0000:03:00.4: No vqmmc regulator found
[    4.852707] usb 1-1: New USB device found, idVendor=8087, idProduct=0020
[    4.853018] hub 1-1:1.0: USB hub found
[    4.869215] usb 2-1: New USB device found, idVendor=8087, idProduct=0020
[    4.869728] hub 2-1:1.0: USB hub found
[    5.249920] usb 1-1.2: New USB device found, idVendor=064e, idProduct=a213
[    5.425596] usb 1-1.6: New USB device found, idVendor=0489, idProduct=e00f
[    5.866234] systemd[1]: Listening on Journal Audit Socket.
[    5.866243] systemd[1]: Starting Journal Audit Socket.
[    5.889321] lp: driver loaded but no devices found
[    6.212473] [Firmware Bug]: ACPI(VGA) defines _DOD but not _DOS
[    6.257419] usb 1-1.2: New USB device found, idVendor=064e, idProduct=a213
[    6.265161] lpc_ich: Resource conflict(s) found affecting gpio_ich
[    6.356545] kvm: VM_EXIT_LOAD_IA32_PERF_GLOBAL_CTRL does not work properly. Using workaround
[    6.420743] CRAT table not found
[    6.476666] snd_hda_intel 0000:00:1b.0: no codecs found!
[    7.866600] uvcvideo: Found UVC 1.00 device USB 2.0 Camera (064e:a213)
[    7.886018] snd_hda_intel 0000:01:00.1: Handle VGA-switcheroo audio client
[    7.896562] input: HDA ATI HDMI HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input9
[    8.576948] audit: type=1400 audit(1431610122.618:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/lightdm/lightdm-guest-session" pid=627 comm="apparmor_parser"
[    8.576958] audit: type=1400 audit(1431610122.618:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="chromium" pid=627 comm="apparmor_parser"
[    8.580730] audit: type=1400 audit(1431610122.622:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/x86_64-linux-gnu/lightdm-remote-session-freerdp/freerdp-session-wrapper" pid=627 comm="apparmor_parser"
[    8.580738] audit: type=1400 audit(1431610122.622:5): apparmor="STATUS" operation="profile_load" profile="unconfined" name="chromium" pid=627 comm="apparmor_parser"
[    8.584643] audit: type=1400 audit(1431610122.626:6): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/x86_64-linux-gnu/lightdm-remote-session-uccsconfigure/uccsconfigure-session-wrapper" pid=627 comm="apparmor_parser"
[    8.584652] audit: type=1400 audit(1431610122.626:7): apparmor="STATUS" operation="profile_load" profile="unconfined" name="chromium" pid=627 comm="apparmor_parser"
[    8.588816] audit: type=1400 audit(1431610122.630:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=627 comm="apparmor_parser"
[    8.588826] audit: type=1400 audit(1431610122.630:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=627 comm="apparmor_parser"
[    8.588835] audit: type=1400 audit(1431610122.630:10): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-helper" pid=627 comm="apparmor_parser"
[    9.358152] usb 1-1.2: New USB device found, idVendor=064e, idProduct=a213
[    9.360826] uvcvideo: Found UVC 1.00 device USB 2.0 Camera (064e:a213)
sudo: /etc/init.d/sl-modem-daemon: command not found
    Release Date: 03/17/2010
    Manufacturer: Sony Corporation
    Product Name: VPCEA1S1E
    Serial Number: 27523760-5001703
    Manufacturer: Sony Corporation
    Product Name: VAIO
    Serial Number: C604P0GY
    Manufacturer: Sony Corporation
    Serial Number: N/A
    Manufacturer: GenuineIntel
    Serial Number: N/A
snd_seq_dummy          16384  0 
snd_hda_codec_hdmi     53248  1 
btusb                  32768  0 
bluetooth             491520  22 bnep,btusb,rfcomm
snd_hda_intel          32768  2 
snd_hda_controller     32768  1 snd_hda_intel
snd_hda_codec         143360  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_controller
snd_hwdep              20480  1 snd_hda_codec
snd_pcm               106496  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller
snd_seq_midi           16384  0 
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  1 snd_seq_midi
snd_seq                69632  3 snd_seq_midi_event,snd_seq_dummy,snd_seq_midi
snd_seq_device         16384  4 snd_seq,snd_rawmidi,snd_seq_dummy,snd_seq_midi
snd_timer              32768  2 snd_pcm,snd_seq
snd                    90112  13 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcmsnd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
soundcore              16384  2 snd,snd_hda_codec
1 sink(s) available.
  * index: 0
    name: <alsa_output.pci-0000_01_00.1.hdmi-stereo>
    driver: <module-alsa-card.c>
    flags: HARDWARE DECIBEL_VOLUME LATENCY DYNAMIC_LATENCY
    state: SUSPENDED
    suspend cause: IDLE 
    priority: 9050
    volume: front-left: 53740 /  82% / -5,17 dB,   front-right: 53740 /  82% / -5,17 dB
            balance 0,00
    base volume: 65536 / 100% / 0,00 dB
    volume steps: 65537
    muted: no
    current latency: 0,00 ms
    max request: 0 KiB
    max rewind: 0 KiB
    monitor source: 0
    sample spec: s16le 2ch 44100Hz
    channel map: front-left,front-right
                 Stereo
    used by: 0
    linked by: 0
    configured latency: 0,00 ms; range is 0,50 .. 371,52 ms
    card: 0 <alsa_card.pci-0000_01_00.1>
    module: 6
    properties:
        alsa.resolution_bits = "16"
        device.api = "alsa"
        device.class = "sound"
        alsa.class = "generic"
        alsa.subclass = "generic-mix"
        alsa.name = "HDMI 0"
        alsa.id = "HDMI 0"
        alsa.subdevice = "0"
        alsa.subdevice_name = "subdevice #0"
        alsa.device = "3"
        alsa.card = "1"
        alsa.card_name = "HDA ATI HDMI"
        alsa.long_card_name = "HDA ATI HDMI at 0xf0030000 irq 30"
        alsa.driver_name = "snd_hda_intel"
        device.bus_path = "pci-0000:01:00.1"
        sysfs.path = "/devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1"
        device.bus = "pci"
        device.vendor.id = "1002"
        device.vendor.name = "Advanced Micro Devices, Inc. [AMD/ATI]"
        device.product.id = "aa38"
        device.product.name = "RV710/730 HDMI Audio [Radeon HD 4000 series]"
        device.string = "hdmi:1"
        device.buffering.buffer_size = "65536"
        device.buffering.fragment_size = "32768"
        device.access_mode = "mmap+timer"
        device.profile.name = "hdmi-stereo"
        device.profile.description = "Digital Stereo (HDMI)"
        device.description = "RV710/730 HDMI Audio [Radeon HD 4000 series] Digital Stereo (HDMI)"
        alsa.mixer_name = "ATI R6xx HDMI"
        alsa.components = "HDA:1002aa01,104d4600,00100100"
        module-udev-detect.discovered = "1"
        device.icon_name = "audio-card-pci"
    ports:
        hdmi-output-0: HDMI / DisplayPort (priority 5900, latency offset 0 usec, available: no)
            properties:
                device.icon_name = "video-display"
    active port: <hdmi-output-0>
**** List of PLAYBACK Hardware Devices ****
card 1: HDMI [HDA ATI HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
Unloading ALSA sound driver modules: snd-seq-dummy snd-hda-codec-hdmi snd-hda-intel snd-hda-controller snd-hda-codec snd-hwdep snd-pcm snd-seq-midi snd-seq-midi-event snd-rawmidi snd-seq snd-seq-device snd-timer (failed: modules still loaded: snd-hda-codec-hdmi snd-hda-intel snd-hda-controller snd-hda-codec snd-hwdep snd-pcm snd-timer).
Loading ALSA sound driver modules: snd-seq-dummy snd-hda-codec-hdmi snd-hda-intel snd-hda-controller snd-hda-codec snd-hwdep snd-pcm snd-seq-midi snd-seq-midi-event snd-rawmidi snd-seq snd-seq-device snd-timer.
Support status summary of 'portablebio':

You have 2545 packages (82.4%) supported until janvier 2016 (9m)
You have 4 packages (0.1%) supported until février 2016 (9m)

You have 123 packages (4.0%) that can not/no-longer be downloaded
You have 415 packages (13.4%) that are unsupported

Run with --show-unsupported, --show-supported or --show-all to see more details
  *-multimedia            
       description: Audio device
       product: RV710/730 HDMI Audio [Radeon HD 4000 series]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0.1
       bus info: pci@0000:01:00.1
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msi bus_master cap_list
       configuration: driver=snd_hda_intel latency=0
       resources: irq:30 memory:f0030000-f0033fff
  *-usb:0
       description: Video
       product: USB 2.0 Camera
       vendor: SuYin
       physical id: 2
       bus info: usb@1:1.2
       version: 5.40
       serial: CN0319-S33B-OV02-VS-R05.04.00
       capabilities: usb-2.00
       configuration: driver=uvcvideo maxpower=500mA speed=480Mbit/s
  *-multimedia
       description: Audio device
       product: 5 Series/3400 Series Chipset High Definition Audio
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 05
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=snd_hda_intel latency=0
       resources: irq:28 memory:f5e00000-f5e03fff


```

---

### Post by matt_symes on 2015-05-14
Hi

I'm wondering if this is a pulseaudio problem.

I may have to do some research.

Can you post the output of

```
cat /etc/pulse/daemon.conf
```

Kind regards

---

