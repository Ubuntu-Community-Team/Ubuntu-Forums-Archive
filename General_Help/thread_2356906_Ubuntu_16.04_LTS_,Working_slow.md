---
title: "Ubuntu 16.04 LTS ,Working slow"
date: 2017-03-28
forum: General Help
---

### Post by manad2 on 2017-03-28
Hello Guyz , 

Im using an Assus X556UB , 4GB ram , i7 2.4 , 4 cores , my computer is extremely slow , i'm talking about 100% CPU spikes while having open only Franz , Chrome and Mozzila ...
 
~1 minute to start the browser...~1 minute to start Settings or any other app... Youtube freezing... And overal apps starting and working extremely hard...

Anyone has any idea why it might that be ?

---

### Post by alexandari on 2017-03-28
Open the terminal and type the command ```
 top 
``` . That will provide a list of processes and the resources they are currently taking over. Refer to that, you can even post the output.

---

### Post by manad2 on 2017-03-28
Output here:
```
top - 11:13:20 up  2:46,  1 user,  load average: 1,60, 1,65, 1,86
Tasks: 267 total,   1 running, 266 sleeping,   0 stopped,   0 zombie
%Cpu(s): 11,8 us,  4,6 sy,  0,0 ni, 82,7 id,  0,9 wa,  0,0 hi,  0,0 si,  0,0 st
KiB Mem :  3904080 total,   457152 free,  2427112 used,  1019816 buff/cache
KiB Swap:  4051964 total,  3533512 free,   518452 used.  1125328 avail Mem 


  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND                                                                                                                                               
 1204 root      20   0  360764  51208  38008 S  17,8  1,3  16:29.18 Xorg                                                                                                                                                  
 4946 madalin   20   0 1284636 217476  48708 S  11,9  5,6  25:26.28 Franz                                                                                                                                                 
 2163 madalin   20   0 1736340 252860  44844 S   9,6  6,5  14:37.23 compiz                                                                                                                                                
23464 madalin   20   0  658600  35944  27472 S   8,3  0,9   0:01.06 gnome-terminal-                                                                                                                                       
 2752 madalin   20   0 2868952 548536  60828 S   4,3 14,1  57:51.94 firefox                                                                                                                                               
 4761 madalin   20   0 1446608  71696  29548 S   4,3  1,8   7:59.23 Franz                                                                                                                                                 
 2164 madalin   20   0  510016   6620   4404 S   3,0  0,2   3:27.81 indicator-multi                                                                                                                                       
 1257 root     -51   0       0      0      0 S   2,3  0,0   3:39.09 irq/131-nvidia                                                                                                                                        
 1969 madalin   20   0  647216  34136  14616 S   1,3  0,9   2:02.54 unity-panel-ser                                                                                                                                       
 2019 madalin   20   0  395940   2692   2344 S   1,3  0,1   1:26.74 indicator-appli                                                                                                                                       
 2389 madalin   20   0 1371924 178428  58228 S   1,3  4,6  19:23.16 chrome                                                                                                                                                
 1800 madalin   20   0   44424   3464   1728 S   1,0  0,1   1:07.59 dbus-daemon                                                                                                                                           
 4796 madalin   20   0 1043580  71396  33996 S   0,7  1,8   1:25.33 Franz                                                                                                                                                 
23482 madalin   20   0   43456   4080   3356 R   0,7  0,1   0:00.18 top                                                                                                                                                   
    1 root      20   0  185372   3828   2416 S   0,0  0,1   0:01.65 systemd                                                                                                                                               
    2 root      20   0       0      0      0 S   0,0  0,0   0:00.00 kthreadd                                                                                                                                              
    3 root      20   0       0      0      0 S   0,0  0,0   0:00.22 ksoftirqd/0                                                                                                                                           
    5 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 kworker/0:0H                                                                                                                                          
    7 root      20   0       0      0      0 S   0,0  0,0   0:14.94 rcu_sched                                                                                                                                             
    8 root      20   0       0      0      0 S   0,0  0,0   0:00.00 rcu_bh                                                                                                                                                
    9 root      rt   0       0      0      0 S   0,0  0,0   0:00.05 migration/0                                                                                                                                           
   10 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 lru-add-drain                                                                                                                                         
   11 root      rt   0       0      0      0 S   0,0  0,0   0:00.04 watchdog/0                                                                                                                                            
   12 root      20   0       0      0      0 S   0,0  0,0   0:00.00 cpuhp/0                                                                                                                                               
   13 root      20   0       0      0      0 S   0,0  0,0   0:00.00 cpuhp/1                                                                                                                                               
   14 root      rt   0       0      0      0 S   0,0  0,0   0:00.04 watchdog/1                                                                                                                                            
   15 root      rt   0       0      0      0 S   0,0  0,0   0:00.05 migration/1                                                                                                                                           
   16 root      20   0       0      0      0 S   0,0  0,0   0:00.35 ksoftirqd/1                                                                                                                                           
   18 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 kworker/1:0H                                                                                                                                          
   19 root      20   0       0      0      0 S   0,0  0,0   0:00.00 cpuhp/2                                                                                                                                               
   20 root      rt   0       0      0      0 S   0,0  0,0   0:00.04 watchdog/2                                                                                                                                            
   21 root      rt   0       0      0      0 S   0,0  0,0   0:00.04 migration/2                                                                                                                                           
   22 root      20   0       0      0      0 S   0,0  0,0   0:00.90 ksoftirqd/2                                                                                                                                           
   24 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 kworker/2:0H                                                                                                                                          
   25 root      20   0       0      0      0 S   0,0  0,0   0:00.00 cpuhp/3                                                                                                                                               
   26 root      rt   0       0      0      0 S   0,0  0,0   0:00.04 watchdog/3                                                                                                                                            
   27 root      rt   0       0      0      0 S   0,0  0,0   0:00.06 migration/3                                                                                                                                           
   28 root      20   0       0      0      0 S   0,0  0,0   0:00.18 ksoftirqd/3                                                                                                                                           
   30 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 kworker/3:0H                                                                                                                                          
   31 root      20   0       0      0      0 S   0,0  0,0   0:00.00 kdevtmpfs                                                                                                                                             
   32 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 netns                                                                                                                                                 
   33 root      20   0       0      0      0 S   0,0  0,0   0:00.01 khungtaskd                                                                                                                                            
   34 root      20   0       0      0      0 S   0,0  0,0   0:00.00 oom_reaper                                                                                                                                            
   35 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 writeback                                                                                                                                             
   36 root      20   0       0      0      0 S   0,0  0,0   0:00.00 kcompactd0                                                                                                                                            
   37 root      25   5       0      0      0 S   0,0  0,0   0:00.00 ksmd                                                                                                                                                  
   38 root      39  19       0      0      0 S   0,0  0,0   0:04.62 khugepaged                                                                                                                                            
   39 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 crypto                                                                                                                                                
   40 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 kintegrityd                                                                                                                                           
   41 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 bioset                                                                                                                                                
   42 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 kblockd                                                                                                                                               
   43 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 ata_sff                                                                                                                                               
   44 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 md                                                                                                                                                    
   45 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 devfreq_wq                                                                                                                                            
   46 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 watchdogd

```

---

### Post by ajgreeny on 2017-03-28
Show us a lot more about your hardware please.
As a start let's see the output of terminal command ```
lspci -k
```
Please use **Code-Tags** for terminal output. See my signature below for a **How-to**

---

### Post by manad2 on 2017-03-28
This is the output :

```
00:00.0 Host bridge: Intel Corporation Sky Lake Host Bridge/DRAM Registers (rev 08)    Subsystem: ASUSTeK Computer Inc. Skylake Host Bridge/DRAM Registers
00:02.0 VGA compatible controller: Intel Corporation Sky Lake Integrated Graphics (rev 07)
    Subsystem: ASUSTeK Computer Inc. Skylake Integrated Graphics
    Kernel driver in use: i915
    Kernel modules: i915
00:04.0 Signal processing controller: Intel Corporation Skylake Processor Thermal Subsystem (rev 08)
    Subsystem: ASUSTeK Computer Inc. Skylake Processor Thermal Subsystem
    Kernel driver in use: proc_thermal
    Kernel modules: processor_thermal_device
00:14.0 USB controller: Intel Corporation Sunrise Point-LP USB 3.0 xHCI Controller (rev 21)
    Subsystem: ASUSTeK Computer Inc. Sunrise Point-LP USB 3.0 xHCI Controller
    Kernel driver in use: xhci_hcd
00:14.2 Signal processing controller: Intel Corporation Sunrise Point-LP Thermal subsystem (rev 21)
    Subsystem: ASUSTeK Computer Inc. Sunrise Point-LP Thermal subsystem
    Kernel driver in use: intel_pch_thermal
    Kernel modules: intel_pch_thermal
00:15.0 Signal processing controller: Intel Corporation Sunrise Point-LP Serial IO I2C Controller (rev 21)
    Subsystem: ASUSTeK Computer Inc. Sunrise Point-LP Serial IO I2C Controller
    Kernel driver in use: intel-lpss
    Kernel modules: intel_lpss_pci
00:15.1 Signal processing controller: Intel Corporation Sunrise Point-LP Serial IO I2C Controller (rev 21)
    Subsystem: ASUSTeK Computer Inc. Sunrise Point-LP Serial IO I2C Controller
    Kernel driver in use: intel-lpss
    Kernel modules: intel_lpss_pci
00:16.0 Communication controller: Intel Corporation Sunrise Point-LP CSME HECI (rev 21)
    Subsystem: ASUSTeK Computer Inc. Sunrise Point-LP CSME HECI
    Kernel driver in use: mei_me
    Kernel modules: mei_me
00:17.0 SATA controller: Intel Corporation Sunrise Point-LP SATA Controller [AHCI mode] (rev 21)
    Subsystem: ASUSTeK Computer Inc. Sunrise Point-LP SATA Controller [AHCI mode]
    Kernel driver in use: ahci
    Kernel modules: ahci
00:1c.0 PCI bridge: Intel Corporation Device 9d10 (rev f1)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.4 PCI bridge: Intel Corporation Sunrise Point-LP PCI Express Root Port (rev f1)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.5 PCI bridge: Intel Corporation Sunrise Point-LP PCI Express Root Port (rev f1)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1f.0 ISA bridge: Intel Corporation Sunrise Point-LP LPC Controller (rev 21)
    Subsystem: ASUSTeK Computer Inc. Sunrise Point-LP LPC Controller
00:1f.2 Memory controller: Intel Corporation Sunrise Point-LP PMC (rev 21)
    Subsystem: ASUSTeK Computer Inc. Sunrise Point-LP PMC
    Kernel driver in use: intel_pmc_core
00:1f.3 Audio device: Intel Corporation Sunrise Point-LP HD Audio (rev 21)
    Subsystem: ASUSTeK Computer Inc. Sunrise Point-LP HD Audio
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel, snd_soc_skl
00:1f.4 SMBus: Intel Corporation Sunrise Point-LP SMBus (rev 21)
    Subsystem: ASUSTeK Computer Inc. Sunrise Point-LP SMBus
    Kernel modules: i2c_i801
01:00.0 3D controller: NVIDIA Corporation GM108M [GeForce 940M] (rev a2)
    Subsystem: ASUSTeK Computer Inc. GM108M [GeForce 940M]
    Kernel driver in use: nvidia
    Kernel modules: nvidiafb, nouveau, nvidia_375_drm, nvidia_375
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 10)
    Subsystem: ASUSTeK Computer Inc. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
    Kernel driver in use: r8169
    Kernel modules: r8169
03:00.0 Network controller: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter (rev 01)
    Subsystem: AzureWave QCA9565 / AR9565 Wireless Network Adapter
    Kernel driver in use: ath9k
    Kernel modules: ath9k

```

*Thx for the [code] tip :)

---

### Post by ajgreeny on 2017-03-28
```
01:00.0 3D controller: NVIDIA Corporation GM108M [GeForce 940M] (rev a2)
    Subsystem: ASUSTeK Computer Inc. GM108M [GeForce 940M]
    Kernel driver in use: nvidia
    Kernel modules: nvidiafb, nouveau, nvidia_375_drm, nvidia_375
```
OK, so you have an nvidia graphic card using an nvidia driver, which I assume you must have asked to install as you installed the OS unless you have added it later from the **Additional Drivers** utility.

I've never used an nvidia card so am no expert but can you tell me if that is one of the optimus graphics systems; I believe it may be, and if so you may have to search for info on bumblebee, about which I am unable to assist, never having needed to use it, nor as mentioned, to run an nvidia card of any sort.

---

### Post by manad2 on 2017-03-30
Yes , it apears as recomanded , do you think i should uninstal it ?The driver may be the issue ?

---

### Post by ajgreeny on 2017-03-31
> **manad2 said:**
> Yes , it apears as recomanded , do you think i should uninstal it ?The driver may be the issue ?
Perhaps worth trying, yes, but as I have no experience of nvidia I am the wrong person to know if it will work or not.

---

### Post by manad2 on 2017-03-31
Ok , i'l try uninstaling it for a few days and see what happens .

---

