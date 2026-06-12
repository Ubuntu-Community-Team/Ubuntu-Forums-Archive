---
title: "Ubuntu almost unresponsive with full RAM"
date: 2018-08-28
forum: General Help
---

### Post by coderwolf161 on 2018-08-28
Hi guys, until recently I had a devils canyon i5 system which I would render on in blender using all of my RAM and some 60GB swap in some cases. This was all fine and the system ran beautifully. Sure you'd get a tiny bit of choppiness when it started using the swap space but I could watch youtube, even play games smoothly.
I just upgraded to a Ryzen 2700 and now as soon as the same render hits the page file the whole system becomes extremely laggy. I can hardly move the mouse, sometimes it will take minutes before I can do that much. It seems as though blender itself is also held back and is not running normally in the background as it should drop a lot of memory from time to time while it's doing pre-render things but that takes forever to get to.
The swap file is on a pair of SSDs in mdadm raid 0. Was in BIOS fake RAID in the previous system. The SSDs are flat out in use when this happens.

I have done some searching for fixes but anything I've found is outdated, such as a bug that was marked as fixed, or just didn't work. Changing swappiness hasn't worked.

This is on Kubuntu 18.04
Just did a kernel update with no change.

Any ideas?
Thanks

---

### Post by him610 on 2018-08-28
I see you are are first time participant in the forum. You might get better response by posting more about your system.
Try running this on the command line and posting the results within the code tags.
```
inxi -F
```

---

### Post by coderwolf161 on 2018-08-28
Here is the output, thanks for replying. The only hardware changed was CPU/RAM/Motherboard.

```
System:    Host: CoderDesktop Kernel: 4.15.0-32-generic x86_64 bits: 64 Desktop: KDE Plasma 5.12.6
           Distro: Ubuntu 18.04.1 LTS                                                                                                                                                                                                                                           
Machine:   Device: desktop Mobo: Micro-Star model: X470 GAMING PRO CARBON (MS-7B78) v: 1.0 serial: N/A                                                                                                                                                                          
           UEFI: American Megatrends v: 2.30 date: 06/28/2018                                                                                                                                                                                                                   
CPU:       8 core AMD Ryzen 7 2700 Eight-Core (-MT-MCP-) cache: 4096 KB                                                                                                                                                                                                         
           clock speeds: max: 3200 MHz 1: 1376 MHz 2: 1374 MHz 3: 1373 MHz 4: 1377 MHz 5: 1375 MHz 6: 1373 MHz                                                                                                                                                                  
           7: 1376 MHz 8: 1375 MHz 9: 1315 MHz 10: 1325 MHz 11: 1317 MHz 12: 1371 MHz 13: 1357 MHz 14: 1330 MHz                                                                                                                                                                 
           15: 1385 MHz 16: 1447 MHz                                                                                                                                                                                                                                            
Graphics:  Card: NVIDIA GP106 [GeForce GTX 1060 6GB]                                                                                                                                                                                                                            
           Display Server: x11 (X.Org 1.19.6 ) drivers: nvidia (unloaded: modesetting,fbdev,vesa,nouveau)                                                                                                                                                                       
           Resolution: 1920x1080@60.00hz, 1920x1080@60.00hz                                                                                                                                                                                                                     
           OpenGL: renderer: GeForce GTX 1060 6GB/PCIe/SSE2 version: 4.6.0 NVIDIA 390.48                                                                                                                                                                                        
Audio:     Card-1 Advanced Micro Devices [AMD] Family 17h (Models 00h-0fh) HD Audio Controller                                                                                                                                                                                  
           driver: snd_hda_intel                                                                                                                                                                                                                                                
           Card-2 NVIDIA GP106 High Definition Audio Controller driver: snd_hda_intel                                                                                                                                                                                           
           Sound: Advanced Linux Sound Architecture v: k4.15.0-32-generic                                                                                                                                                                                                       
Network:   Card: Intel I211 Gigabit Network Connection driver: igb                                                                                                                                                                                                              
           IF: enp24s0 state: up speed: 100 Mbps duplex: full mac: 30:9c:23:af:57:82                                                                                                                                                                                            
Drives:    HDD Total Size: 4012.8GB (5.9% used)                                                                                                                                                                                                                                 
           ID-1: USB /dev/sda model: P9220 size: 1000.2GB                                                                                                                                                                                                                       
           ID-2: /dev/sdb model: Samsung_SSD_850 size: 500.1GB                                                                                                                                                                                                                  
           ID-3: /dev/sdc model: Samsung_SSD_850 size: 512.1GB                                                                                                                                                                                                                  
           ID-4: /dev/sdd model: Hitachi_HDT72101 size: 1000.2GB                                                                                                                                                                                                                
           ID-5: /dev/sde model: Hitachi_HDT72101 size: 1000.2GB                                                                                                                                                                                                                
Partition: ID-1: / size: 866G used: 164G (20%) fs: ext4 dev: /dev/md0p1                                                                                                                                                                                                         
           ID-2: /boot size: 291M used: 219M (80%) fs: ext2 dev: /dev/sdc1                                                                                                                                                                                                      
           ID-3: swap-1 size: 65.54GB used: 0.00GB (0%) fs: swap dev: /dev/md0p2                                                                                                                                                                                                
RAID:      Device-1: /dev/md0 - active raid: 0 components: online: sdc3 sdb3                                                                                                                                                                                                    
Sensors:   System Temperatures: cpu: 32.6C mobo: N/A gpu: 29C                                                                                                                                                                                                                   
           Fan Speeds (in rpm): cpu: N/A                                                                                                                                                                                                                                        
Info:      Processes: 339 Uptime: 4 min Memory: 1481.3/16054.2MB Client: Shell (bash) inxi: 2.3.56

```

---

### Post by coderwolf161 on 2018-09-02
I have solved the issue. It was essentially the solution in this thread:
[https://askubuntu.com/questions/41778/computer-freezing-on-almost-full-ram-possibly-disk-cache-problem](https://askubuntu.com/questions/41778/computer-freezing-on-almost-full-ram-possibly-disk-cache-problem)

However I am under the impression that the high core count of Ryzen requires more RAM to be free. Perhaps the calculation should have involved multiplying as oppose to dividing by the number of cores?
In any case by running:
```
sysctl -w vm.min_free_kbytes=524288
```
The system now swaps as expected without freezing up.

Following the calculations on that post resulted in too little a value which made no difference, I'm no expert but I suggest just tweaking it yourself.

---

