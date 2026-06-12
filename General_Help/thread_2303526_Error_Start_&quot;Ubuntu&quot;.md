---
title: "Error Start &quot;Ubuntu&quot;"
date: 2015-11-19
forum: General Help
---

### Post by molao on 2015-11-19
[COLOR=#000000][FONT=Arial]Hello,[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Unable to access Ubuntu I have error messages :

*******************************[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]mount: mounting /dev/disk/by-uuid/6f5381ab-1736-4a4c-bd02-859c6970dc70 on /root
failed: invalid argument[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]mount: mounting /dev on/root/dev failed: No such file or directory
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: no such file or directory[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Target filesystem doesn't have requested /sbin/init.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]No init found .Try passing init=bootarg.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]BusyBox v1.21.1 (Ubuntu 1:1.21.0-1 ubuntu1) built-in shell (ash)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Enter 'help' for a list of built-in commands.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial](initramfs)

***************************

Thank You[/FONT][/COLOR]

---

### Post by ian-weisser on 2015-11-19
How many disks do you have installed?
Is Ubuntu the only OS on this system?
Was the system working properly before? Did anything change or update?

---

### Post by molao on 2015-11-19
> **molao said:**
> [COLOR=#000000][FONT=Arial]Hello,[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Unable to access Ubuntu I have error messages :

*******************************[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]mount: mounting /dev/disk/by-uuid/6f5381ab-1736-4a4c-bd02-859c6970dc70 on /root
failed: invalid argument[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]mount: mounting /dev on/root/dev failed: No such file or directory
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: no such file or directory[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Target filesystem doesn't have requested /sbin/init.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]No init found .Try passing init=bootarg.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]BusyBox v1.21.1 (Ubuntu 1:1.21.0-1 ubuntu1) built-in shell (ash)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Enter 'help' for a list of built-in commands.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial](initramfs)

***************************

Thank You[/FONT][/COLOR]


[COLOR=#000000]**How many disks do you have installed?  **
[/COLOR]it is an on laptop[COLOR=#000000]

[/COLOR][COLOR=#000000]**Is Ubuntu the only OS on this system?**
Windows 10 and Ubuntu 14
[/COLOR]
[B][COLOR=#000000]Was the system working properly before? Did anything change or update?
[/COLOR][/B]No Upgrade days was made, Ubuntu works well, there are more than 3 months I upgrade windows 8 to 10 and ubuntu it does not reach had a problem,[COLOR=#000000][/COLOR]

---

### Post by molao on 2015-11-19
Disk Information : 
Information on the disc by the live cd , impossible to try to save data to disk " ubuntu " because I can not access them while those windows runs on the live usb

Boot-info url : [http://paste.ubuntu.com/13353585/](http://paste.ubuntu.com/13353585/)

Thank You

--------------------
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x76692ca8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      718847      358400    7  HPFS/NTFS/exFAT
/dev/sda2          718848   278999039   139140096    7  HPFS/NTFS/exFAT
/dev/sda3       279000916   976771071   348885078    f  W95 Ext'd (LBA)
/dev/sda5       279000918   886651968   303825525+   7  HPFS/NTFS/exFAT
/dev/sda6       886654976   968386559    40865792   83  Linux
/dev/sda7       968388608   976771071     4191232   82  Linux swap / Solaris

Disk /dev/sdb: 8036 MB, 8036285952 bytes
255 heads, 63 sectors/track, 977 cylinders, total 15695871 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0f3e3e0f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048    15695870     7846911+   c  W95 FAT32 (LBA)
ubuntu@ubuntu:~$

---

### Post by molao on 2015-11-20
what should I do?
thank you

---

### Post by yancek on 2015-11-20
In your initial post you show this message:  ```
[COLOR=#000000][FONT=Arial]failed: invalid argument[/FONT][/COLOR]
```

So what exactly were you doing when you got that message, what was the argument?  Were you trying to manually mount?
In post #3, you say that Ubuntu works well and also indicate you have windows 10 install so the question is, do they both boot and if so, what is the problem?

---

### Post by molao on 2015-11-21
> **yancek said:**
> In your initial post you show this message:  ```
[COLOR=#000000][FONT=Arial]failed: invalid argument[/FONT][/COLOR]
```

So what exactly were you doing when you got that message, what was the argument?  Were you trying to manually mount?
In post #3, you say that Ubuntu works well and also indicate you have windows 10 install so the question is, do they both boot and if so, what is the problem?
I can go on windows to ubuntu I can not access it, i made his test, which did not resolve the probmème


```
 ubuntu@ubuntu:~$ dmesg | tail -50
[   28.813723] EDAC amd64: DRAM ECC disabled.
[   28.813730] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
[   28.813730]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
[   28.813730]  (Note that use of the override may cause unknown side effects.)
[   28.914742] device-mapper: multipath: version 1.7.0 loaded
[   28.939494] media: Linux media interface: v0.10
[   28.959281] Linux video capture interface: v2.00
[   29.061187] uvcvideo: Found UVC 1.00 device USB 2.0 Camera (13d3:5130)
[   29.078434] input: USB 2.0 Camera as /devices/pci0000:00/0000:00:13.2/usb2/2-2/2-2:1.0/input/input15
[   29.078641] usbcore: registered new interface driver uvcvideo
[   29.078647] USB Video Class driver (1.1.1)
[   29.205552] ath: phy0: Enable LNA combining
[   29.215752] ath: EEPROM regdomain: 0x60
[   29.215759] ath: EEPROM indicates we should expect a direct regpair map
[   29.215764] ath: Country alpha2 being used: 00
[   29.215766] ath: Regpair used: 0x60
[   29.233521] kvm: Nested Virtualization enabled
[   29.233530] kvm: Nested Paging enabled
[   29.261368] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   29.262375] ieee80211 phy0: Atheros AR9285 Rev:2 mem=0xffffc90010a60000, irq=18
[   29.356942] snd_hda_intel 0000:01:00.1: Handle VGA-switcheroo audio client
[   29.386863] input: HDA ATI HDMI HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card1/input16
[   29.422912] sound hdaudioC0D0: autoconfig: line_outs=1 (0x1c/0x0/0x0/0x0/0x0) type:speaker
[   29.422921] sound hdaudioC0D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   29.422925] sound hdaudioC0D0:    hp_outs=1 (0x1d/0x0/0x0/0x0/0x0)
[   29.422928] sound hdaudioC0D0:    mono: mono_out=0x0
[   29.422931] sound hdaudioC0D0:    inputs:
[   29.422935] sound hdaudioC0D0:      Internal Mic=0x1e
[   29.422938] sound hdaudioC0D0:      Mic=0x1a
[   29.441649] input: HDA ATI SB Mic as /devices/pci0000:00/0000:00:14.2/sound/card0/input17
[   29.441779] input: HDA ATI SB Headphone as /devices/pci0000:00/0000:00:14.2/sound/card0/input18
[   29.752394] init: failsafe main process (1424) killed by TERM signal
[   29.758143] cfg80211: World regulatory domain updated:
[   29.758152] cfg80211:  DFS Master region: unset
[   29.758155] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
[   29.758160] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[   29.758164] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[   29.758167] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm), (N/A)
[   29.758170] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[   29.758173] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[   31.009935] init: alsa-restore main process (1806) terminated with status 99
[   31.523460] ATL1E 0000:02:00.0 eth0: NIC Link is Up <1000 Mbps Full Duplex>
[   31.526278] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   31.526874] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   31.606357] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   35.218160] init: plymouth-upstart-bridge main process ended, respawning
[   35.233519] init: plymouth-upstart-bridge main process (2307) terminated with status 1
[   35.233539] init: plymouth-upstart-bridge main process ended, respawning
[  209.979779] ATL1E 0000:02:00.0 eth0: NIC Link is Down
[  212.226238] ATL1E 0000:02:00.0 eth0: NIC Link is Up <1000 Mbps Full Duplex>
ubuntu@ubuntu:~$ sudo fsck -NV /dev/sda6
fsck from util-linux 2.20.1
[/sbin/fsck.ext4 (1) -- /dev/sda6] fsck.ext4 /dev/sda6 
ubuntu@ubuntu:~$
   
```


and


```
  buntu@ubuntu:~$ sudo  umount  /dev/sda6
umount: /dev/sda6: not mounted
ubuntu@ubuntu:~$ sudo  mount   /dev/sda6
mount: can't find /dev/sda6 in /etc/fstab or /etc/mtab
ubuntu@ubuntu:~$ dmesg  |   tail    -50
[   28.382239] input: HDA ATI HDMI HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card1/input15
[   28.385905] sound hdaudioC0D0: autoconfig: line_outs=1 (0x1c/0x0/0x0/0x0/0x0) type:speaker
[   28.385921] sound hdaudioC0D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   28.385924] sound hdaudioC0D0:    hp_outs=1 (0x1d/0x0/0x0/0x0/0x0)
[   28.385926] sound hdaudioC0D0:    mono: mono_out=0x0
[   28.385928] sound hdaudioC0D0:    inputs:
[   28.385931] sound hdaudioC0D0:      Internal Mic=0x1e
[   28.385933] sound hdaudioC0D0:      Mic=0x1a
[   28.393406] input: HDA ATI SB Mic as /devices/pci0000:00/0000:00:14.2/sound/card0/input16
[   28.393542] input: HDA ATI SB Headphone as /devices/pci0000:00/0000:00:14.2/sound/card0/input17
[   28.414320] kvm: Nested Virtualization enabled
[   28.414332] kvm: Nested Paging enabled
[   28.436575] uvcvideo: Found UVC 1.00 device USB 2.0 Camera (13d3:5130)
[   28.445732] input: USB 2.0 Camera as /devices/pci0000:00/0000:00:13.2/usb2/2-2/2-2:1.0/input/input18
[   28.445886] usbcore: registered new interface driver uvcvideo
[   28.445889] USB Video Class driver (1.1.1)
[   28.554219] ath: phy0: Enable LNA combining
[   28.730629] ath: EEPROM regdomain: 0x60
[   28.730636] ath: EEPROM indicates we should expect a direct regpair map
[   28.730639] ath: Country alpha2 being used: 00
[   28.730641] ath: Regpair used: 0x60
[   28.754905] cfg80211: World regulatory domain updated:
[   28.754913] cfg80211:  DFS Master region: unset
[   28.754915] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
[   28.754920] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[   28.754922] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[   28.754925] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm), (N/A)
[   28.754927] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[   28.754929] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[   28.798818] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   28.799328] ieee80211 phy0: Atheros AR9285 Rev:2 mem=0xffffc90010ee0000, irq=18
[   28.818694] init: failsafe main process (1421) killed by TERM signal
[   29.737419] init: alsa-restore main process (1764) terminated with status 99
[   30.234156] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   30.237660] ATL1E 0000:02:00.0 eth0: NIC Link is Up <1000 Mbps Full Duplex>
[   30.237682] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   30.318460] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   33.267577] init: plymouth-upstart-bridge main process ended, respawning
[   44.972226] ATL1E 0000:02:00.0 eth0: NIC Link is Down
[   47.187082] ATL1E 0000:02:00.0 eth0: NIC Link is Up <1000 Mbps Full Duplex>
[   59.533522] ATL1E 0000:02:00.0 eth0: NIC Link is Down
[   61.731071] ATL1E 0000:02:00.0 eth0: NIC Link is Up <1000 Mbps Full Duplex>
[   62.691477] ATL1E 0000:02:00.0 eth0: NIC Link is Down
[   64.919086] ATL1E 0000:02:00.0 eth0: NIC Link is Up <1000 Mbps Full Duplex>
[   65.814952] ATL1E 0000:02:00.0 eth0: NIC Link is Down
[   70.845300] ATL1E 0000:02:00.0 eth0: NIC Link is Up <1000 Mbps Full Duplex>
[   71.622312] ATL1E 0000:02:00.0 eth0: NIC Link is Down
[   73.703274] ATL1E 0000:02:00.0 eth0: NIC Link is Up <1000 Mbps Full Duplex>
[   74.633297] ATL1E 0000:02:00.0 eth0: NIC Link is Down
[   76.108398] ATL1E 0000:02:00.0 eth0: NIC Link is Up <100 Mbps Full Duplex>
ubuntu@ubuntu:~$ 
  
  
```[COLOR=#000000][FONT=Arial]

and


```
  [/FONT][/COLOR] ubuntu@ubuntu:~$ sudo smartctl  -a    /dev/sda
sudo: smartctl: command not found
ubuntu@ubuntu:~$ [COLOR=#000000][FONT=Arial]  
```[COLOR=#000000][FONT=Arial]

and


```
 [/FONT][/COLOR][/FONT][/COLOR]  ubuntu@ubuntu:~$  sudo fsck -NV /dev/sda6
fsck from util-linux 2.20.1
[/sbin/fsck.ext4 (1) -- /dev/sda6] fsck.ext4 /dev/sda6 
ubuntu@ubuntu:~$ [COLOR=#000000][FONT=Arial][COLOR=#000000][FONT=Arial]   
```[COLOR=#000000][FONT=Arial]

and


```
  [/FONT][/COLOR][/FONT][/COLOR][/FONT][/COLOR]ubuntu@ubuntu:~$ sudo add-apt-repository "deb http://archive.ubuntu.com/ubuntu $(lsb_release -sc) universe"
ubuntu@ubuntu:~$ sudo apt-get update
Ign cdrom://Ubuntu 14.04.3 LTS _Trusty Tahr_ - Beta amd64 (20150805) trusty InRelease
Ign cdrom://Ubuntu 14.04.3 LTS _Trusty Tahr_ - Beta amd64 (20150805) trusty/main Translation-fr_FR
Ign cdrom://Ubuntu 14.04.3 LTS _Trusty Tahr_ - Beta amd64 (20150805) trusty/main Translation-fr
Ign cdrom://Ubuntu 14.04.3 LTS _Trusty Tahr_ - Beta amd64 (20150805) trusty/main Translation-en
Ign cdrom://Ubuntu 14.04.3 LTS _Trusty Tahr_ - Beta amd64 (20150805) trusty/restricted Translation-fr_FR
Ign cdrom://Ubuntu 14.04.3 LTS _Trusty Tahr_ - Beta amd64 (20150805) trusty/restricted Translation-fr
Ign cdrom://Ubuntu 14.04.3 LTS _Trusty Tahr_ - Beta amd64 (20150805) trusty/restricted Translation-en
Réception de : 1 http://security.ubuntu.com trusty-security InRelease [64,4 kB]
Ign http://archive.ubuntu.com trusty InRelease                                 
Réception de : 2 http://archive.ubuntu.com trusty-updates InRelease [64,4 kB]
Réception de : 3 http://security.ubuntu.com trusty-security/main amd64 Packages [370 kB]
Atteint http://archive.ubuntu.com trusty Release.gpg                           
Réception de : 4 http://archive.ubuntu.com trusty-updates/main amd64 Packages [653 kB]
Réception de : 5 http://security.ubuntu.com trusty-security/restricted amd64 Packages [13,0 kB]
Réception de : 6 http://security.ubuntu.com trusty-security/main Translation-en [201 kB]
Réception de : 7 http://security.ubuntu.com trusty-security/restricted Translation-en [3 206 B]
Réception de : 8 http://archive.ubuntu.com trusty-updates/restricted amd64 Packages [15,9 kB]
Réception de : 9 http://archive.ubuntu.com trusty-updates/main Translation-en [320 kB]
Réception de : 10 http://archive.ubuntu.com trusty-updates/restricted Translation-en [3 699 B]
Atteint http://archive.ubuntu.com trusty Release                    
Atteint http://archive.ubuntu.com trusty/main amd64 Packages
Atteint http://archive.ubuntu.com trusty/restricted amd64 Packages
Réception de : 11 http://archive.ubuntu.com trusty/universe amd64 Packages [5 859 kB]
Réception de : 12 http://archive.ubuntu.com trusty/main Translation-fr [814 kB]
Atteint http://archive.ubuntu.com trusty/main Translation-en                   
Réception de : 13 http://archive.ubuntu.com trusty/restricted Translation-fr [3 879 B]
Atteint http://archive.ubuntu.com trusty/restricted Translation-en             
Réception de : 14 http://archive.ubuntu.com trusty/universe Translation-fr [2 942 kB]
Réception de : 15 http://archive.ubuntu.com trusty/universe Translation-en [4 089 kB]
Ign http://archive.ubuntu.com trusty/main Translation-fr_FR                    
Ign http://archive.ubuntu.com trusty/restricted Translation-fr_FR              
Ign http://archive.ubuntu.com trusty/universe Translation-fr_FR                
15,4 Mo réceptionnés en 22s (697 ko/s)                                         
Lecture des listes de paquets... Fait
ubuntu@ubuntu:~$ sudo apt-get install --no-install-recommends smartmontools 
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances       
Lecture des informations d'état... Fait
Paquets suggérés :
  gsmartcontrol smart-notifier
Paquets recommandés :
  mailx mailutils
Les NOUVEAUX paquets suivants seront installés :
  smartmontools
0 mis à jour, 1 nouvellement installés, 0 à enlever et 197 non mis à jour.
Il est nécessaire de prendre 445 ko dans les archives.
Après cette opération, 1 650 ko d'espace disque supplémentaires seront utilisés.
Réception de : 1 http://archive.ubuntu.com/ubuntu/ trusty/main smartmontools amd64 6.2+svn3841-1.2 [445 kB]
445 ko réceptionnés en 0s (2 117 ko/s)
Sélection du paquet smartmontools précédemment désélectionné.
(Lecture de la base de données... 170586 fichiers et répertoires déjà installés.)
Preparing to unpack .../smartmontools_6.2+svn3841-1.2_amd64.deb ...
Unpacking smartmontools (6.2+svn3841-1.2) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Processing triggers for ureadahead (0.100.0-16) ...
Paramétrage de smartmontools (6.2+svn3841-1.2) ...
Processing triggers for ureadahead (0.100.0-16) ...
ubuntu@ubuntu:~$ [COLOR=#000000][FONT=Arial][COLOR=#000000][FONT=Arial][COLOR=#000000][FONT=Arial]  
```[COLOR=#000000][FONT=Arial]

and


```
 [/FONT][/COLOR][/FONT][/COLOR][/FONT][/COLOR][/FONT][/COLOR]ubuntu@ubuntu:~$ sudo smartctl  -s on /dev/sda
smartctl 6.2 2013-07-26 r3841 [x86_64-linux-3.19.0-25-generic] (local build)
Copyright (C) 2002-13, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF ENABLE/DISABLE COMMANDS SECTION ===
SMART Enabled.

ubuntu@ubuntu:~$ sudo smartctl  -a    /dev/sda
smartctl 6.2 2013-07-26 r3841 [x86_64-linux-3.19.0-25-generic] (local build)
Copyright (C) 2002-13, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF INFORMATION SECTION ===
Model Family:     Seagate Momentus 5400.6
Device Model:     ST9500325AS
Serial Number:    6VE6ZQGF
LU WWN Device Id: 5 000c50 02280a870
Firmware Version: 0003SDM1
User Capacity:    500 107 862 016 bytes [500 GB]
Sector Size:      512 bytes logical/physical
Rotation Rate:    5400 rpm
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ATA8-ACS T13/1699-D revision 4
SATA Version is:  SATA 2.6, 3.0 Gb/s
Local Time is:    Fri Nov 20 09:39:19 2015 UTC
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED
See vendor-specific Attribute list for marginal Attributes.

General SMART Values:
Offline data collection status:  (0x82)	Offline data collection activity
					was completed without error.
					Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0)	The previous self-test routine completed
					without error or no self-test has ever 
					been run.
Total time to complete Offline 
data collection: 		(    0) seconds.
Offline data collection
capabilities: 			 (0x7b) SMART execute Offline immediate.
					Auto Offline data collection on/off support.
					Suspend Offline collection upon new
					command.
					Offline surface scan supported.
					Self-test supported.
					Conveyance Self-test supported.
					Selective Self-test supported.
SMART capabilities:            (0x0003)	Saves SMART data before entering
					power-saving mode.
					Supports SMART auto save timer.
Error logging capability:        (0x01)	Error logging supported.
					General Purpose Logging supported.
Short self-test routine 
recommended polling time: 	 (   1) minutes.
Extended self-test routine
recommended polling time: 	 ( 136) minutes.
Conveyance self-test routine
recommended polling time: 	 (   2) minutes.
SCT capabilities: 	       (0x103b)	SCT Status supported.
					SCT Error Recovery Control supported.
					SCT Feature Control supported.
					SCT Data Table supported.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   102   099   006    Pre-fail  Always       -       104984633
  3 Spin_Up_Time            0x0003   099   098   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   088   088   020    Old_age   Always       -       12836
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       2
  7 Seek_Error_Rate         0x000f   089   060   030    Pre-fail  Always       -       829374676
  9 Power_On_Hours          0x0032   097   075   000    Old_age   Always       -       2751
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   088   037   020    Old_age   Always       -       12973
184 End-to-End_Error        0x0032   100   100   099    Old_age   Always       -       0
187 Reported_Uncorrect      0x0032   001   001   000    Old_age   Always       -       162
188 Command_Timeout         0x0032   100   001   000    Old_age   Always       -       339307598712
189 High_Fly_Writes         0x003a   100   100   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0022   060   039   045    Old_age   Always   In_the_past 40 (9 126 40 19 0)
191 G-Sense_Error_Rate      0x0032   100   100   000    Old_age   Always       -       257
192 Power-Off_Retract_Count 0x0032   099   099   000    Old_age   Always       -       3686
193 Load_Cycle_Count        0x0032   045   045   000    Old_age   Always       -       111267
194 Temperature_Celsius     0x0022   040   061   000    Old_age   Always       -       40 (0 14 0 0 0)
195 Hardware_ECC_Recovered  0x001a   044   034   000    Old_age   Always       -       104984633
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       2
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       2
199 UDMA_CRC_Error_Count    0x003e   200   173   000    Old_age   Always       -       1371
254 Free_Fall_Sensor        0x0032   100   100   000    Old_age   Always       -       0

SMART Error Log Version: 1
ATA Error Count: 214 (device log contains only the most recent five errors)
	CR = Command Register [HEX]
	FR = Features Register [HEX]
	SC = Sector Count Register [HEX]
	SN = Sector Number Register [HEX]
	CL = Cylinder Low Register [HEX]
	CH = Cylinder High Register [HEX]
	DH = Device/Head Register [HEX]
	DC = Device Command Register [HEX]
	ER = Error register [HEX]
	ST = Status register [HEX]
Powered_Up_Time is measured from power on, and printed as
DDd+hh:mm:SS.sss where DD=days, hh=hours, mm=minutes,
SS=sec, and sss=millisec. It "wraps" after 49.710 days.

Error 214 occurred at disk power-on lifetime: 2750 hours (114 days + 14 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 ff ff ff 0f  Error: UNC at LBA = 0x0fffffff = 268435455

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 00 08 ff ff ff 4f 00      00:02:55.691  READ FPDMA QUEUED
  60 00 08 ff ff ff 4f 00      00:02:55.682  READ FPDMA QUEUED
  60 00 08 ff ff ff 4f 00      00:02:55.682  READ FPDMA QUEUED
  60 00 08 ff ff ff 4f 00      00:02:55.681  READ FPDMA QUEUED
  60 00 08 ff ff ff 4f 00      00:02:55.680  READ FPDMA QUEUED

Error 213 occurred at disk power-on lifetime: 2750 hours (114 days + 14 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 ff ff ff 0f  Error: UNC at LBA = 0x0fffffff = 268435455

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 00 08 ff ff ff 4f 00      00:01:12.501  READ FPDMA QUEUED
  60 00 08 ff ff ff 4f 00      00:01:12.498  READ FPDMA QUEUED
  60 00 08 ff ff ff 4f 00      00:01:12.498  READ FPDMA QUEUED
  60 00 08 ff ff ff 4f 00      00:01:12.488  READ FPDMA QUEUED
  60 00 08 ff ff ff 4f 00      00:01:12.487  READ FPDMA QUEUED

Error 212 occurred at disk power-on lifetime: 2750 hours (114 days + 14 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 ff ff ff 0f  Error: UNC at LBA = 0x0fffffff = 268435455

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 00 08 ff ff ff 4f 00      00:00:17.262  READ FPDMA QUEUED
  60 00 08 ff ff ff 4f 00      00:00:17.260  READ FPDMA QUEUED
  60 00 08 ff ff ff 4f 00      00:00:17.250  READ FPDMA QUEUED
  60 00 08 ff ff ff 4f 00      00:00:17.249  READ FPDMA QUEUED
  60 00 08 ff ff ff 4f 00      00:00:17.243  READ FPDMA QUEUED

Error 211 occurred at disk power-on lifetime: 2750 hours (114 days + 14 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 ff ff ff 0f  Error: UNC at LBA = 0x0fffffff = 268435455

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 00 08 ff ff ff 4f 00      00:31:10.027  READ FPDMA QUEUED
  60 00 08 ff ff ff 4f 00      00:31:10.024  READ FPDMA QUEUED
  60 00 08 ff ff ff 4f 00      00:31:10.015  READ FPDMA QUEUED
  60 00 08 ff ff ff 4f 00      00:31:10.014  READ FPDMA QUEUED
  60 00 08 ff ff ff 4f 00      00:31:10.006  READ FPDMA QUEUED

Error 210 occurred at disk power-on lifetime: 2749 hours (114 days + 13 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 ff ff ff 0f  Error: UNC at LBA = 0x0fffffff = 268435455

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 00 08 ff ff ff 4f 00      00:01:13.124  READ FPDMA QUEUED
  60 00 08 ff ff ff 4f 00      00:01:13.122  READ FPDMA QUEUED
  60 00 08 ff ff ff 4f 00      00:01:13.112  READ FPDMA QUEUED
  60 00 08 ff ff ff 4f 00      00:01:13.112  READ FPDMA QUEUED
  60 00 08 ff ff ff 4f 00      00:01:13.103  READ FPDMA QUEUED

SMART Self-test log structure revision number 1
No self-tests have been logged.  [To run self-tests, use: smartctl -t]


SMART Selective self-test log data structure revision number 1
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Not_testing
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.

ubuntu@ubuntu:~$ [COLOR=#000000][FONT=Arial][COLOR=#000000][FONT=Arial][COLOR=#000000][FONT=Arial][COLOR=#000000][FONT=Arial]   
```[COLOR=#000000][FONT=Arial]

and



```
   [/FONT][/COLOR][/FONT][/COLOR][/FONT][/COLOR][/FONT][/COLOR][/FONT][/COLOR]ubuntu@ubuntu:~$ sudo fsck -nv /dev/sda6
fsck from util-linux 2.20.1
e2fsck 1.42.9 (4-Feb-2014)
Avertissement : saute la récupération du journal puisque l'on
procède à l'examen d'un système de fichiers en lecture seule.
/dev/sda6 : propre, 304075/2555904 fichiers, 6307756/10216448 blocs
ubuntu@ubuntu:~$ [COLOR=#000000][FONT=Arial][COLOR=#000000][FONT=Arial][COLOR=#000000][FONT=Arial][COLOR=#000000][FONT=Arial][COLOR=#000000][FONT=Arial] 
```[COLOR=#000000][FONT=Arial]
[COLOR=#000000][FONT=Arial][COLOR=#000000][FONT=Arial][COLOR=#000000][FONT=Arial][COLOR=#000000][FONT=Arial][COLOR=#000000][FONT=Arial][COLOR=#000000][FONT=Arial][COLOR=#000000][FONT=Arial][COLOR=#000000][FONT=Arial][COLOR=#000000][FONT=Arial][COLOR=#000000][FONT=Arial][COLOR=#000000][FONT=Arial][COLOR=#000000][FONT=Arial][COLOR=#000000][FONT=Arial][/FONT][/COLOR][/FONT][/COLOR][/FONT][/COLOR][/FONT][/COLOR][/FONT][/COLOR][/FONT][/COLOR][/FONT][/COLOR][/FONT][/COLOR][/FONT][/COLOR][/FONT][/COLOR][/FONT][/COLOR][/FONT][/COLOR]


and


```
 ubuntu@ubuntu:~$ sudo umount /dev/sda6
umount: /dev/sda6: not mounted
ubuntu@ubuntu:~$ sudo umount /dev/sda6
umount: /dev/sda6: not mounted
ubuntu@ubuntu:~$ sudo fsck  -av /dev/sda6
fsck from util-linux 2.20.1
/dev/sda6 : récupération du journal
Erreur de lecture du bloc 4755815 (La tentative de lecture d'un bloc depuis le système de fichiers a produit une lecture tronquée). 

/dev/sda6: INCONSISTENCE INATTENDUE ; EXÉCUTEZ fsck MANUELLEMENT.
    (i.e., sans options -a ou -p)
ubuntu@ubuntu:~$ 

   
```[COLOR=#000000][FONT=Arial][/FONT][/COLOR][/FONT][/COLOR][/FONT][/COLOR][/FONT][/COLOR][/FONT][/COLOR][/FONT][/COLOR][/FONT][/COLOR][/FONT][/COLOR][COLOR=#000000][FONT=Arial][/FONT][/COLOR]


thank you

---

### Post by yancek on 2015-11-21
> I can go on windows to ubuntu I can not access it

I don't understand what  that means.  Seems like you say you can boot windows but not access Ubuntu, is that right?  If so, not a problem as that is expecxted behavior from windows.  Windows won't recognize a partition with a Linux filesystem.  That's a simple business decision by microsoft.

On the other hand, all the commands with output you post are from Ubuntu and it seems like you are using a Live CD/flash drive.  Do you have a Linux ext4 filesystem on sda6?  Your mount command is incorrect.  You first need to create a mount point.  Try this:  sudo mkdir /mnt/sda6  After that do the mount command:  sudo mount -t ext4 /dev/sda6 /mnt/sda6

Are you doing this from a Live CD?  Can you clarify what you can boot?  Can you translate the output of the fsck command on sda6 to English?

---

