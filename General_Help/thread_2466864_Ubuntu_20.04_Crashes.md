---
title: "Ubuntu 20.04 Crashes"
date: 2021-09-08
forum: General Help
---

### Post by sdam1n on 2021-09-08
I recently bought a pc. After installing ubuntu it constantly crashes after about 1 hour.
The screen remains frozen. Sometimes pc doesn't restart or shutdown or start. Mainly the gui remains stuck. Then the pc needs to hard reset. I clean reinstalled Ubuntu again but the problem remains the same. During the reinstallation,the installer also crashed once.  


I am using an old monitor with hdmi to vga converter.


Installation Info:
I used GPT partition scheme to install ubuntu by enabling uefi from the bios.


My PC Config:   
Processor: Ryzen 3 3200G   
Mobo: MSI A320M pro max   
Ram: 16 GB   
SSD: 120 GB   
HDD: 500 GB(This is a old HDD)  
and an old asus optical drive from my previous Desktop. 


free -h:
              total        used        free      shared  buff/cache   available
Mem:           13Gi       1.5Gi        10Gi        46Mi       1.4Gi        11Gi
Swap:         2.0Gi          0B       2.0Gi  

sysctl vm.swappiness

vm.swappiness = 60

swapon -s

Filename                Type        Size    Used    Priority
/swapfile                file        2097148    0         -2



sudo lshw -C memory

  *-firmware                
       description: BIOS
       vendor: American Megatrends Inc.
       physical id: 0
       version: 2.80
       date: 12/07/2020
       size: 64KiB
       capacity: 16MiB
       capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer acpi usb biosbootspecification uefi
  *-memory
       description: System Memory
       physical id: f
       slot: System board or motherboard
       size: 16GiB
     *-bank:0
          description: DIMM DDR4 Synchronous Unbuffered (Unregistered) 2400 MHz (0.4 ns)
          product: F4-2400C15-8GVR
          vendor: Unknown
          physical id: 0
          serial: 00000000
          slot: DIMM 0
          size: 8GiB
          width: 64 bits
          clock: 2400MHz (0.4ns)
     *-bank:1
          description: DIMM DDR4 Synchronous Unbuffered (Unregistered) 2400 MHz (0.4 ns)
          product: F4-2400C15-8GVR
          vendor: Unknown
          physical id: 1
          serial: 00000000
          slot: DIMM 0
          size: 8GiB
          width: 64 bits
          clock: 2400MHz (0.4ns)
  *-cache:0
       description: L1 cache
       physical id: 11
       slot: L1 - Cache
       size: 384KiB
       capacity: 384KiB
       clock: 1GHz (1.0ns)
       capabilities: pipeline-burst internal write-back unified
       configuration: level=1
  *-cache:1
       description: L2 cache
       physical id: 12
       slot: L2 - Cache
       size: 2MiB
       capacity: 2MiB
       clock: 1GHz (1.0ns)
       capabilities: pipeline-burst internal write-back unified
       configuration: level=2
  *-cache:2
       description: L3 cache
       physical id: 13
       slot: L3 - Cache
       size: 4MiB
       capacity: 4MiB
       clock: 1GHz (1.0ns)
       capabilities: pipeline-burst internal write-back unified
       configuration: level=3

sudo dmidecode -s bios-version

2.80

[COLOR=#232629][FONT=ui-monospace]sudo journalctl  -b -1 -e 

[/FONT][/COLOR]Sep 08 17:08:02 my-pc kernel: loop1: detected capacity change from 0 to 133320
Sep 08 17:08:02 my-pc kernel: loop2: detected capacity change from 0 to 66152
Sep 08 17:08:02 my-pc kernel: loop3: detected capacity change from 0 to 113536
Sep 08 17:08:02 my-pc kernel: loop4: detected capacity change from 0 to 104360
Sep 08 17:08:02 my-pc systemd[1]: Finished Flush Journal to Persistent Storage.
Sep 08 17:08:02 my-pc systemd[1]: Started udev Kernel Device Manager.
Sep 08 17:08:02 my-pc systemd[1]: Starting Show Plymouth Boot Screen...
Sep 08 17:08:02 my-pc kernel: loop5: detected capacity change from 0 to 66144
Sep 08 17:08:02 my-pc systemd[1]: Mounted Mount unit for snapd, revision 12883.
Sep 08 17:08:02 my-pc systemd[1]: Mounted Mount unit for gnome-3-34-1804, revis>
Sep 08 17:08:02 my-pc systemd[1]: Mounted Mount unit for gtk-common-themes, rev>
Sep 08 17:08:02 my-pc systemd[1]: Received SIGRTMIN+20 from PID 344 (plymouthd).
Sep 08 17:08:02 my-pc systemd[1]: Started Show Plymouth Boot Screen.
Sep 08 17:08:02 my-pc systemd[1]: Condition check resulted in Dispatch Password>
Sep 08 17:08:02 my-pc systemd[1]: Started Forward Password Requests to Plymouth>
Sep 08 17:08:02 my-pc systemd[1]: Reached target Local Encrypted Volumes.
Sep 08 17:08:02 my-pc systemd[1]: Mounted Mount unit for snap-store, revision 5>
Sep 08 17:08:02 my-pc systemd[1]: Mounted Mount unit for core18, revision 2128.
Sep 08 17:08:02 my-pc systemd[1]: Mounted Mount unit for snapd, revision 12704.
Sep 08 17:08:10 my-pc systemd[1]: plymouth-start.service: Main process exited, >
Sep 08 17:08:10 my-pc systemd[1]: plymouth-start.service: Failed with result 's>
Sep 08 17:08:17 my-pc systemd[1]: Caught <ABRT>, dumped core as pid 353.
Sep 08 17:08:17 my-pc systemd[1]: Freezing execution.
lines 979-1001/1001 (END)
Sep 08 17:08:02 my-pc kernel: loop1: detected capacity change from 0 to 133320
Sep 08 17:08:02 my-pc kernel: loop2: detected capacity change from 0 to 66152
Sep 08 17:08:02 my-pc kernel: loop3: detected capacity change from 0 to 113536
Sep 08 17:08:02 my-pc kernel: loop4: detected capacity change from 0 to 104360
Sep 08 17:08:02 my-pc systemd[1]: Finished Flush Journal to Persistent Storage.
Sep 08 17:08:02 my-pc systemd[1]: Started udev Kernel Device Manager.
Sep 08 17:08:02 my-pc systemd[1]: Starting Show Plymouth Boot Screen...
Sep 08 17:08:02 my-pc kernel: loop5: detected capacity change from 0 to 66144
Sep 08 17:08:02 my-pc systemd[1]: Mounted Mount unit for snapd, revision 12883.
Sep 08 17:08:02 my-pc systemd[1]: Mounted Mount unit for gnome-3-34-1804, revision 72.
Sep 08 17:08:02 my-pc systemd[1]: Mounted Mount unit for gtk-common-themes, revision 1515.
Sep 08 17:08:02 my-pc systemd[1]: Received SIGRTMIN+20 from PID 344 (plymouthd).
Sep 08 17:08:02 my-pc systemd[1]: Started Show Plymouth Boot Screen.
Sep 08 17:08:02 my-pc systemd[1]: Condition check resulted in Dispatch Password Requests to Console Directory Watch being skipped.
Sep 08 17:08:02 my-pc systemd[1]: Started Forward Password Requests to Plymouth Directory Watch.
Sep 08 17:08:02 my-pc systemd[1]: Reached target Local Encrypted Volumes.
Sep 08 17:08:02 my-pc systemd[1]: Mounted Mount unit for snap-store, revision 547.
Sep 08 17:08:02 my-pc systemd[1]: Mounted Mount unit for core18, revision 2128.
Sep 08 17:08:02 my-pc systemd[1]: Mounted Mount unit for snapd, revision 12704.
Sep 08 17:08:10 my-pc systemd[1]: plymouth-start.service: Main process exited, code=killed, status=11/SEGV
Sep 08 17:08:10 my-pc systemd[1]: plymouth-start.service: Failed with result 'signal'.
Sep 08 17:08:17 my-pc systemd[1]: Caught <ABRT>, dumped core as pid 353.
Sep 08 17:08:17 my-pc systemd[1]: Freezing execution.
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
lines 979-1001/1001 (END)
Sep 08 17:08:02 my-pc kernel: loop1: detected capacity change from 0 to 133320
Sep 08 17:08:02 my-pc kernel: loop2: detected capacity change from 0 to 66152
Sep 08 17:08:02 my-pc kernel: loop3: detected capacity change from 0 to 113536
Sep 08 17:08:02 my-pc kernel: loop4: detected capacity change from 0 to 104360
Sep 08 17:08:02 my-pc systemd[1]: Finished Flush Journal to Persistent Storage.
Sep 08 17:08:02 my-pc systemd[1]: Started udev Kernel Device Manager.
Sep 08 17:08:02 my-pc systemd[1]: Starting Show Plymouth Boot Screen...
Sep 08 17:08:02 my-pc kernel: loop5: detected capacity change from 0 to 66144
Sep 08 17:08:02 my-pc systemd[1]: Mounted Mount unit for snapd, revision 12883.
Sep 08 17:08:02 my-pc systemd[1]: Mounted Mount unit for gnome-3-34-1804, revision 72.
Sep 08 17:08:02 my-pc systemd[1]: Mounted Mount unit for gtk-common-themes, revision 1515.
Sep 08 17:08:02 my-pc systemd[1]: Received SIGRTMIN+20 from PID 344 (plymouthd).
Sep 08 17:08:02 my-pc systemd[1]: Started Show Plymouth Boot Screen.
Sep 08 17:08:02 my-pc systemd[1]: Condition check resulted in Dispatch Password Requests to Console Directory Watch being skipped.
Sep 08 17:08:02 my-pc systemd[1]: Started Forward Password Requests to Plymouth Directory Watch.
Sep 08 17:08:02 my-pc systemd[1]: Reached target Local Encrypted Volumes.
Sep 08 17:08:02 my-pc systemd[1]: Mounted Mount unit for snap-store, revision 547.
Sep 08 17:08:02 my-pc systemd[1]: Mounted Mount unit for core18, revision 2128.
Sep 08 17:08:02 my-pc systemd[1]: Mounted Mount unit for snapd, revision 12704.
Sep 08 17:08:10 my-pc systemd[1]: plymouth-start.service: Main process exited, code=killed, status=11/SEGV
Sep 08 17:08:10 my-pc systemd[1]: plymouth-start.service: Failed with result 'signal'.
Sep 08 17:08:17 my-pc systemd[1]: Caught <ABRT>, dumped core as pid 353.
Sep 08 17:08:17 my-pc systemd[1]: Freezing execution.

---

