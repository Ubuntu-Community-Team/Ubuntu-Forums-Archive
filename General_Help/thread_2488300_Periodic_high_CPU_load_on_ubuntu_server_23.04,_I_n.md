---
title: "Periodic high CPU load on ubuntu server 23.04, I need help with diagnostics and fix"
date: 2023-06-30
forum: General Help
---

### Post by bartoszek on 2023-06-30
I have a fresh install of ubuntu server 23.04 and I can see that CPU  usage on idle is quite high (~0.5) after further investigation I saw  that kworker proces periodically (something like every ~20sec kicks in  and takes 100% of single core. After running sudo perf record -g -a sleep 10 I think I see that see that the issue lies in the intel drivers (intel_hdmi_detect and later), as seen on the screenshot [perf screenshot]("https://i.stack.imgur.com/5UxEh.png") the problem is that I don't really know how to proceed with this, what should I do?

```

 lspci
00:00.0 Host bridge: Intel Corporation 8th Gen Core 4-core Desktop Processor Host Bridge/DRAM Registers [Coffee Lake S] (rev 08)
00:01.0 PCI bridge: Intel Corporation 6th-10th Gen Core Processor PCIe Controller (x16) (rev 08)
00:02.0 Display controller: Intel Corporation CoffeeLake-S GT2 [UHD Graphics 630]
00:08.0 System peripheral: Intel Corporation Xeon E3-1200 v5/v6 / E3-1500 v5 / 6th/7th/8th Gen Core Processor Gaussian Mixture Model
00:12.0 Signal processing controller: Intel Corporation Cannon Lake PCH Thermal Controller (rev 10)
00:14.0 USB controller: Intel Corporation Cannon Lake PCH USB 3.1 xHCI Host Controller (rev 10)
00:14.2 RAM memory: Intel Corporation Cannon Lake PCH Shared SRAM (rev 10)
00:15.0 Serial bus controller: Intel Corporation Cannon Lake PCH Serial IO I2C Controller #0 (rev 10)
00:15.1 Serial bus controller: Intel Corporation Cannon Lake PCH Serial IO I2C Controller #1 (rev 10)
00:16.0 Communication controller: Intel Corporation Cannon Lake PCH HECI Controller (rev 10)
00:16.1 Communication controller: Intel Corporation Device a361 (rev 10)
00:16.4 Communication controller: Intel Corporation Cannon Lake PCH HECI Controller #2 (rev 10)
00:17.0 SATA controller: Intel Corporation Cannon Lake PCH SATA AHCI Controller (rev 10)
00:1b.0 PCI bridge: Intel Corporation Cannon Lake PCH PCI Express Root Port #17 (rev f0)
00:1c.0 PCI bridge: Intel Corporation Cannon Lake PCH PCI Express Root Port #1 (rev f0)
00:1d.0 PCI bridge: Intel Corporation Cannon Lake PCH PCI Express Root Port #9 (rev f0)
00:1d.1 PCI bridge: Intel Corporation Cannon Lake PCH PCI Express Root Port #10 (rev f0)
00:1d.2 PCI bridge: Intel Corporation Cannon Lake PCH PCI Express Root Port #11 (rev f0)
00:1e.0 Communication controller: Intel Corporation Cannon Lake PCH Serial IO UART Host Controller (rev 10)
00:1f.0 ISA bridge: Intel Corporation Cannon Point-LP LPC Controller (rev 10)
00:1f.4 SMBus: Intel Corporation Cannon Lake PCH SMBus Controller (rev 10)
00:1f.5 Serial bus controller: Intel Corporation Cannon Lake PCH SPI Controller (rev 10)
01:00.0 Ethernet controller: Mellanox Technologies MT27500 Family [ConnectX-3]
03:00.0 Non-Volatile memory controller: Samsung Electronics Co Ltd NVMe SSD Controller 980
04:00.0 Ethernet controller: Intel Corporation I210 Gigabit Network Connection (rev 03)
05:00.0 PCI bridge: ASPEED Technology, Inc. AST1150 PCI-to-PCI Bridge (rev 04)
06:00.0 VGA compatible controller: ASPEED Technology, Inc. ASPEED Graphics Family (rev 41)
07:00.0 Ethernet controller: Intel Corporation I210 Gigabit Network Connection (rev 03)


$ sudo dmidecode -t 2
# dmidecode 3.4
Getting SMBIOS data from sysfs.
SMBIOS 3.2.0 present.

Handle 0x0002, DMI type 2, 15 bytes
Base Board Information
        Manufacturer: ASRockRack
        Product Name: E3C246D4U
        Version:                       
        Serial Number: 111111111111111
        Asset Tag:                       
        Features:
                Board is a hosting board
                Board is replaceable
        Location In Chassis:                       
        Chassis Handle: 0x0003
        Type: Motherboard
        Contained Object Handles: 0
```

---

### Post by MAFoElffen on 2023-06-30
Please post the output to the following within CODE Tags:
```

uname -r
sudo dmidecode -t 0
grep 'name' /proc/[COLOR=#ff0000]cpu[/COLOR]info | head -n 1

```
During a high cpu load event, execute this script to try to capture what is going on to a file called 'captured.log'
```

#!/bin/bash
ps aux | sort -nrk 3,3 | head -n 10 >> ~/captured.log
ps fax o uid,%cpu,%mem,time,comm | awk '0+$0 == 1000 {print}' | sort -nrk 2,3 -r | head -n 25 >> ~/captured.log
ps fax o uid,%cpu,%mem,time,comm | awk '0+$0 == 000 {print}' | sort -nrk 2,3 -r | head -n 25 >> ~/captured.log

```

---

### Post by bartoszek on 2023-07-01
Thank you for the response 

```
[FONT=monospace][COLOR=#000000]$ uname -r [/COLOR]
6.2.0-24-generic

[/FONT][FONT=monospace][COLOR=#000000]$ sudo dmidecode -t 0 [/COLOR]
# dmidecode 3.4 
Getting SMBIOS data from sysfs. 
SMBIOS 3.2.0 present. 

Handle 0x0000, DMI type 0, 26 bytes 
BIOS Information 
        Vendor: American Megatrends Inc. 
        Version: P2.30 
        Release Date: 12/25/2019 
        Address: 0xF0000 
        Runtime Size: 64 kB 
        ROM Size: 32 MB 
        Characteristics: 
                PCI is supported 
                BIOS is upgradeable 
                BIOS shadowing is allowed 
                Boot from CD is supported 
                Selectable boot is supported 
                BIOS ROM is socketed 
                EDD is supported 
                5.25"/1.2 MB floppy services are supported (int 13h) 
                3.5"/720 kB floppy services are supported (int 13h) 
                3.5"/2.88 MB floppy services are supported (int 13h) 
                Print screen service is supported (int 5h) 
                Serial services are supported (int 14h) 
                Printer services are supported (int 17h) 
                ACPI is supported 
                USB legacy is supported 
                BIOS boot specification is supported 
                Targeted content distribution is supported 
                UEFI is supported 
        BIOS Revision: 5.13 [/FONT]
```[FONT=monospace]

sadly 

[/FONT][FONT=monospace]```
[COLOR=#000000]$ grep 'name' /proc/info | head -n 1 [/COLOR]
grep: /proc/info: No such file or directory
```

did you ment procinfo?
[/FONT]```
[FONT=monospace][COLOR=#000000][/COLOR][/FONT][FONT=monospace][COLOR=#000000]$ procinfo  [/COLOR]
Memory:        Total        Used        Free     Buffers                        
RAM:        32588836     9444172    23144664      131496                        
Swap:        7406588           0     7406588                                    

Bootup: Thu Jun 29 17:21:50 2023   Load average: 0.44 0.46 0.49 1/369 1114157   

user  :      00:46:53.13   0.5%  page in :          2349624                     
nice  :      00:00:03.10   0.0%  page out:         73745477                     
system:      11:17:55.50   6.9%  page act:           695465                     
IOwait:      00:56:56.42   0.6%  page dea:                0                     
hw irq:      00:00:00.00   0.0%  page flt:         57721158                     
sw irq:      00:01:24.26   0.0%  swap in :                0                     
idle  :   6d 05:04:06.55  91.6%  swap out:                0                     
uptime:   1d 16:48:12.52         context :         97028777                     

irq   8:          0  8-edge rtc0         irq 132:      73957  3-edge eno2-TxRx- 
irq   9:       9725  9-fasteoi acpi      irq 133:      75111  4-edge eno2-TxRx- 
irq  14:          0  14-fasteoi INT345   irq 134:     219874  0-edge xhci_hcd   
irq  16:          5  16-fasteoi i801_s   irq 135:         18  0-edge nvme0q0    
irq  17:          0  17-fasteoi idma64   irq 136:       3375  0-edge vfio-msix[ 
irq  20:          0  20-fasteoi idma64   irq 137:        206  1-edge vfio-msix[ 
irq 120:          0  0-edge dmar0        irq 138:          5  2-edge vfio-msix[ 
irq 121:          0  1-edge dmar1        irq 141:      47817  1-edge nvme0q1    
irq 122:          0  0-edge PCIe PME     irq 142:     110087  2-edge nvme0q2    
irq 123:          0  0-edge PCIe PME     irq 143:     110958  3-edge nvme0q3    
irq 124:          0  0-edge PCIe PME     irq 144:     115999  4-edge nvme0q4    
irq 125:          0  0-edge PCIe PME     irq 145:     554036  0-edge i915       
irq 126:          0  0-edge PCIe PME     irq 146:    1747433  0-edge mlx4-async 
irq 127:          0  0-edge PCIe PME     irq 147:     273837  1-edge mlx4-1@000 
irq 128:          2  0-edge eno2         irq 148:     208345  2-edge mlx4-2@000 
irq 129:      76834  1-edge eno2-TxRx-   irq 149:     160783  3-edge mlx4-3@000 
irq 130:      76851  2-edge eno2-TxRx-   irq 150:     707608  4-edge mlx4-4@000 
irq 131:    2988706  0-edge ahci[0000:                                          


eno1        TX 762.70MiB     RX 232.92MiB     lo          TX 181.97KiB     RX 181.97KiB     
eno2        TX 888.38KiB     RX 890.47KiB     ovs-system  TX 0.00B         RX 0.00B         
eu-de-fr    TX 327.18KiB     RX 70.35KiB      virbr0      TX 0.00B         RX 0.00B         
lan_ovs     TX 0.00B         RX 0.00B         vport21     TX 2.64MiB       RX 29.12MiB
[/FONT]
```
[FONT=monospace]
And some info about CPU[/FONT][FONT=monospace]

[/FONT][FONT=monospace]
[/FONT]```
[FONT=monospace][COLOR=#000000]$ lscpu  [/COLOR]
Architecture:            x86_64 
  CPU op-mode(s):        32-bit, 64-bit 
  Address sizes:         39 bits physical, 48 bits virtual 
  Byte Order:            Little Endian 
CPU(s):                  4 
  On-line CPU(s) list:   0-3 
Vendor ID:               GenuineIntel 
  Model name:            Intel(R) Core(TM) i3-9300T CPU @ 3.20GHz 
    CPU family:          6 
    Model:               158 
    Thread(s) per core:  1 
    Core(s) per socket:  4 
    Socket(s):           1 
    Stepping:            11 
    CPU(s) scaling MHz:  97% 
    CPU max MHz:         3800.0000 
    CPU min MHz:         800.0000 
    BogoMIPS:            6399.96 
    Flags:               fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp lm constant_tsc art arch_perfmon pebs bt 
                         s rep_good nopl xtopology nonstop_tsc cpuid aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 sdbg fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_t 
                         imer aes xsave avx f16c rdrand lahf_lm abm 3dnowprefetch cpuid_fault epb invpcid_single pti ssbd ibrs ibpb stibp tpr_shadow vnmi flexpriority ept vpid ept_ad fsgsbase tsc_adjust bmi1 avx 
                         2 smep bmi2 erms invpcid mpx rdseed adx smap clflushopt intel_pt xsaveopt xsavec xgetbv1 xsaves dtherm ida arat pln pts hwp hwp_notify hwp_act_window hwp_epp md_clear flush_l1d arch_capa 
                         bilities 
Virtualization features:  
  Virtualization:        VT-x 
Caches (sum of all):      
  L1d:                   128 KiB (4 instances) 
  L1i:                   128 KiB (4 instances) 
  L2:                    1 MiB (4 instances) 
  L3:                    8 MiB (1 instance) 
NUMA:                     
  NUMA node(s):          1 
  NUMA node0 CPU(s):     0-3 
Vulnerabilities:          
  Itlb multihit:         KVM: Mitigation: Split huge pages 
  L1tf:                  Mitigation; PTE Inversion; VMX conditional cache flushes, SMT disabled 
  Mds:                   Mitigation; Clear CPU buffers; SMT disabled 
  Meltdown:              Mitigation; PTI 
  Mmio stale data:       Mitigation; Clear CPU buffers; SMT disabled 
  Retbleed:              Mitigation; IBRS 
  Spec store bypass:     Mitigation; Speculative Store Bypass disabled via prctl 
  Spectre v1:            Mitigation; usercopy/swapgs barriers and __user pointer sanitization 
  Spectre v2:            Mitigation; IBRS, IBPB conditional, STIBP disabled, RSB filling, PBRSB-eIBRS Not affected 
  Srbds:                 Mitigation; Microcode 
  Tsx async abort:       Not affected
[/FONT]
```
[FONT=monospace] 
And the requested capture is attached [/FONT][ATTACH]292434[/ATTACH]

---

### Post by MAFoElffen on 2023-07-01
Sorry for the typo. Corrected in previous post.

So it looks like it might be coming from libvirtd and your OpenSense VM guest...

Do you have Virtual Manager installed? If so, startup Virtual Manager, even if it is remotely from your workstation, connected to your KVM host...

The in the menus, select View > Graph > Check all the checkboxes... Look at the graphs to see the line of that running VM Guest and watch it to see how much resources it is using in those graphs... That is how I visually monitor my VM's to quickly get an idea if there is a problem or if one of them needs to have their resources tweaked.

---

### Post by bartoszek on 2023-07-01
Right now I have Virtual Manager disabled, and the spikes are still there. I am almost sure, that I could see them when all the VM where down... Now I can't recheck, because my wife is watching netflix :) and I can't just switch back to connect TV to router, but I'll retry my tests tomorrow and check it the situation is still there when everything (VM's and Virt manager) is down. 
Thank you for the support

---

### Post by MAFoElffen on 2023-07-01
Understood. Keeping the better-half happy is **the** priority. My wife's #1 priority is to be able to watch her shows and movies.

After I posted that, I think maybe that high CPU condition was not happening at that moment in time, so was not captured. Those stat's didn't look that high... It might take some time to capture that.

---

### Post by bartoszek on 2023-07-02
Hi!

I disabled docker / libvirtd services on my server, and virt-manager on my pc, to do some quick tests and the results are very similar to what i saw previously. kworker in top takes periodically 100% CPU and then stops, nothing really change, Also I took 100 of logs (in a loop) just to catch the high cpu  load (and another 100 during the peace time) and tbh all of them look the same


one of file from "peak"

```
[FONT=monospace][COLOR=#000000]root     3466248 11.3  0.0      0     0 ?        R    08:38   1:54 [kworker/3:2+events] [/COLOR]
root     3338967  9.3  0.0      0     0 ?        I    07:45   6:32 [kworker/3:0-events] 
bartosz+ 3491802  3.1  0.0   7256  3456 pts/0    S+   08:55   0:00 /bin/bash ./capture_bug.sh 
root          47  0.6  0.0      0     0 ?        SN   Jun29  22:54 [ksmd] 
root        2208  0.2  0.2 532092 74360 ?        S<Lsl Jun29  10:43 ovs-vswitchd unix:/var/run/openvswitch/db.sock -vconsole:emer -vsyslog:err -vfile:info --mlockall --no-chdir --log-file=/var/log/openvswitch/ov
s-vswitchd.log --pidfile=/var/run/openvswitch/ovs-vswitchd.pid --detach 
bartosz+ 3491141  0.2  0.0  11792  5632 pts/1    S+   08:50   0:00 top 
root         977  0.1  0.0      0     0 ?        S    Jun29   3:57 [l2arc_feed] 
root        1407  0.1  0.0      0     0 ?        S<   Jun29   4:34 [z_wr_iss] 
root     1347730  0.1  0.1 1578408 50304 ?       Ssl  Jul01   1:25 /usr/bin/containerd 
USER         PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND 
 1000  3.0  0.0 00:00:00              \_ capture_bug.sh 
 1000  0.2  0.0 00:00:00          |   \_ top 
 1000  0.0  0.0 00:00:54 systemd 
 1000  0.0  0.0 00:00:17      \_ sshd 
 1000  0.0  0.0 00:00:00                  \_ sort 
 1000  0.0  0.0 00:00:00  \_ (sd-pam) 
 1000  0.0  0.0 00:00:00                  \_ ps 
 1000  0.0  0.0 00:00:00                  \_ head 
 1000  0.0  0.0 00:00:00  \_ bash 
 1000  0.0  0.0 00:00:00          \_ bash 
 1000  0.0  0.0 00:00:00          \_ bash 
 1000  0.0  0.0 00:00:00                  \_ awk 
    0 11.3  0.0 00:01:54  \_ kworker/3:2+events 
    0  9.3  0.0 00:06:32  \_ kworker/3:0-events 
    0  0.6  0.0 00:22:54  \_ ksmd 
    0  0.2  0.2 00:10:43 ovs-vswitchd 
    0  0.1  0.1 00:01:25 containerd 
    0  0.1  0.0 00:04:34  \_ z_wr_iss 
    0  0.1  0.0 00:03:57  \_ l2arc_feed 
  UID %CPU %MEM     TIME COMMAND 
    0  0.0  0.1 00:00:40 systemd-journal 
    0  0.0  0.1 00:00:35 snapd 
    0  0.0  0.0 00:02:45  \_ z_wr_int 
    0  0.0  0.0 00:02:02  \_ rcu_preempt 
    0  0.0  0.0 00:01:35  \_ txg_sync 
    0  0.0  0.0 00:01:28 systemd 
    0  0.0  0.0 00:00:46  \_ z_rd_int 
    0  0.0  0.0 00:00:41  \_ nfsd 
    0  0.0  0.0 00:00:37 kthreadd 
    0  0.0  0.0 00:00:36 systemd-udevd 
    0  0.0  0.0 00:00:33  \_ ksoftirqd/0 
    0  0.0  0.0 00:00:31  \_ z_null_iss 
    0  0.0  0.0 00:00:31 thermald 
    0  0.0  0.0 00:00:28 ovsdb-server 
    0  0.0  0.0 00:00:27  \_ migration/0 
    0  0.0  0.0 00:00:26  \_ z_wr_iss_h 
    0  0.0  0.0 00:00:25 multipathd

[/FONT]
```

and from peace

```
[FONT=monospace][COLOR=#000000]root     3466248 11.6  0.0      0     0 ?        I    08:38   2:08 [kworker/3:2-events] [/COLOR]
root     3338967  9.4  0.0      0     0 ?        I    07:45   6:44 [kworker/3:0-events] 
bartosz+ 3492368  3.6  0.0   7256  3456 pts/0    S+   08:57   0:00 /bin/bash ./capture_bug.sh 
root          47  0.6  0.0      0     0 ?        SN   Jun29  22:54 [ksmd] 
root        2208  0.2  0.2 532092 74360 ?        S<Lsl Jun29  10:43 ovs-vswitchd unix:/var/run/openvswitch/db.sock -vconsole:emer -vsyslog:err -vfile:info --mlockall --no-chdir --log-file=/var/log/openvswitch/ov
s-vswitchd.log --pidfile=/var/run/openvswitch/ovs-vswitchd.pid --detach 
bartosz+ 3491141  0.2  0.0  11792  5632 pts/1    S+   08:50   0:01 top 
root         977  0.1  0.0      0     0 ?        S    Jun29   3:57 [l2arc_feed] 
root        1407  0.1  0.0      0     0 ?        S<   Jun29   4:34 [z_wr_iss] 
root     1347730  0.1  0.1 1578408 50304 ?       Ssl  Jul01   1:25 /usr/bin/containerd 
USER         PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND 
 1000  3.5  0.0 00:00:00              \_ capture_bug.sh 
 1000  0.2  0.0 00:00:01          |   \_ top 
 1000  0.0  0.0 00:00:54 systemd 
 1000  0.0  0.0 00:00:17      \_ sshd 
 1000  0.0  0.0 00:00:00                  \_ sort 
 1000  0.0  0.0 00:00:00  \_ (sd-pam) 
 1000  0.0  0.0 00:00:00                  \_ ps 
 1000  0.0  0.0 00:00:00                  \_ head 
 1000  0.0  0.0 00:00:00  \_ bash 
 1000  0.0  0.0 00:00:00          \_ bash 
 1000  0.0  0.0 00:00:00          \_ bash 
 1000  0.0  0.0 00:00:00                  \_ awk 
    0 11.6  0.0 00:02:08  \_ kworker/3:2-events 
    0  9.4  0.0 00:06:44  \_ kworker/3:0-events 
    0  0.6  0.0 00:22:54  \_ ksmd 
    0  0.2  0.2 00:10:43 ovs-vswitchd 
    0  0.1  0.1 00:01:25 containerd 
    0  0.1  0.0 00:04:34  \_ z_wr_iss 
    0  0.1  0.0 00:03:57  \_ l2arc_feed 
  UID %CPU %MEM     TIME COMMAND 
    0  0.0  0.1 00:00:40 systemd-journal 
    0  0.0  0.1 00:00:35 snapd 
    0  0.0  0.0 00:02:45  \_ z_wr_int 
    0  0.0  0.0 00:02:02  \_ rcu_preempt 
    0  0.0  0.0 00:01:35  \_ txg_sync 
    0  0.0  0.0 00:01:28 systemd 
    0  0.0  0.0 00:00:46  \_ z_rd_int 
    0  0.0  0.0 00:00:41  \_ nfsd 
    0  0.0  0.0 00:00:37 kthreadd 
    0  0.0  0.0 00:00:36 systemd-udevd 
    0  0.0  0.0 00:00:33  \_ ksoftirqd/0 
    0  0.0  0.0 00:00:31  \_ z_null_iss 
    0  0.0  0.0 00:00:31 thermald 
    0  0.0  0.0 00:00:29 ovsdb-server 
    0  0.0  0.0 00:00:27  \_ migration/0 
    0  0.0  0.0 00:00:26  \_ z_wr_iss_h 
    0  0.0  0.0 00:00:25 multipathd
[/FONT]
```

so disabling anything related to libvirt, and nothing really changed regarding my issue ;(

---

### Post by MAFoElffen on 2023-07-02
Step #1: Please post the output of this:
```

sudo systemctl status ovs-vswitchd.service | grep .

```
Also check this log for anomalies: /var/log/openvswitch/ovs-vswitchd.log
```

grep '-vsyslog:err\|unknown anon_inode\|dropped\|WARN\|ERR' /var/log/openvswitch/ovs-vswitchd.log

```
Step #2: Add this to your loop to capture what ovs-vswitch is doing during that.
```

sudo ovs-appctl coverage/show | grep -e put -e xlate
sudo ovs-dpctl dump-flows -s

```
After an even, then do this...
Step #3: Try temporarily stopping ovs-vswitchd.service and see if that  is what is sucking that up... 
```

sudo systemctl stop ovs-vswitchd.service

```
Do this to see if it prevents a high CPU  event.

If we see that as the culprit: [https://bugs.launchpad.net/ubuntu/+source/openvswitch/+bug/1827264](https://bugs.launchpad.net/ubuntu/+source/openvswitch/+bug/1827264)

Please post this to see if it falls into that what may cause that condition:
```

apt list libc --installed

```

---

### Post by bartoszek on 2023-07-03
I see that you look for foult in the openvswitch implementation, and to check this I need to basically disable my home network, which at this point is problematic (I don't have a separate connection to KVM yet)

And at this point I decided to confirm that my intuition is right (or wrong), and stoopped searching for a bug in openvswitch AND test i915 instead, so...

```
[FONT=monospace][COLOR=#000000]sudo modprobe -r i915[/COLOR][/FONT]
```

I don't know why I didn't do this earlier...  because I always suspected the intel drivers to be faulty... anyway after unloading i915 driver the problem is gone, avg load (with 4 VMs) dropped from 0.76 to 0.24

what now? :)

ALSO... I checked logs for ovs and there was no error, and no indication of [https://bugs.launchpad.net/ubuntu/+source/openvswitch/+bug/1827264](https://bugs.launchpad.net/ubuntu/+source/openvswitch/+bug/1827264) being reproduced

---

### Post by MAFoElffen on 2023-07-03
Happy that you found it. funny the it didn't show anything as load in ps(?) 

Note the version number of the Kernel... What is it?

The i915 driver is in the Linux Kernel (actually, a module). At the Grub2 menu, select advanced options, then select and an older kernel version. If that solves it then file a bug against the kernel that there is a problem. Usually Launchpad will have people try a kernel from the MAIN repo, so they can see if there was a problem they they caused when they applied Ubuntu kinds of tweak to the in their repo's.  Trying different kernels would give you a different i915 driver.

If that is what is causing it, then the next thing to do might be if you are running is to do while running that Kernel is to do is to see if you are running a GA or HWE kernel... then run the other series... or use a kernel variant series.

RE: [https://ubuntu.com/kernel/variants](https://ubuntu.com/kernel/variants)

For my Workstation, that hosts Plex media Server, I run the HWE series kernels, because streams seem to process the sound better on them. On my main KVM Server, it is ZFS based, and seems to run better on the HWE stack because of the some of the Bifurcation NVMe 4x storage controllers I am using need it...

Hmmm
> 
Intel(R) Core(TM) i3-9300T CPU @ 3.20GHz

So Intel UHD Graphics 630... Honestly, I haven't seen a problem with high CPU usage with i915 drivers for about 6 years. This is surprising and has my curiosity going. Now you have more of my attention.

---

### Post by bartoszek on 2023-07-03
Hi!

I have iommu enabled in the system, so my plan is to pass my  GPU to VM and test it there, first for reproduction and then solution. I  saw this issue before I updated the kernel (now running latest)   also... yes the ps output is strange, but I can see CPU usage in top and also  as system load.
Also running the original script once again shows

```

[FONT=monospace][COLOR=#000000] 1000  0.0  0.0 00:00:10      \_ sshd [/COLOR]
 1000  0.0  0.0 00:00:04              \_ virt-ssh-helper 
 1000  0.0  0.0 00:00:00 systemd 
 1000  0.0  0.0 00:00:00          |       \_ sort 
 1000  0.0  0.0 00:00:00          \_ sh 
 1000  0.0  0.0 00:00:00  \_ (sd-pam) 
 1000  0.0  0.0 00:00:00          |       \_ ps 
 1000  0.0  0.0 00:00:00          |       \_ head 
 1000  0.0  0.0 00:00:00          |   \_ capture_bug.sh 
 1000  0.0  0.0 00:00:00  \_ bash 
 1000  0.0  0.0 00:00:00          \_ bash 
 1000  0.0  0.0 00:00:00          |       \_ awk 
    **0  2.2  0.0 00:00:04  \_ kworker/3:1-events** 
    0  1.9  0.0 00:00:04  \_ kworker/u8:2-events_power_efficient 
    **0  1.1  0.0 00:07:36  \_ kworker/3:3-events **
    0  0.5  0.0 00:07:21  \_ vhost-39281 
    0  0.3  0.2 00:04:48 ovs-vswitchd 
    0  0.2  0.0 00:04:06 libvirtd 
    0  0.2  0.0 00:03:05  \_ ksmd 
    0  0.1  0.0 00:02:34  \_ l2arc_feed 
    0  0.1  0.0 00:02:14  \_ z_wr_iss 
    0  0.1  0.0 00:01:34  \_ z_wr_int 
    0  0.1  0.0 00:00:00  \_ kworker/2:1-events 
    0  0.1  0.0 00:00:00  \_ kworker/0:2-events
[/FONT]
```[FONT=monospace]

Previous logs reported ~12% of usage for those processes, so that's something :) 
I'll try to prepare a VM with PCI passthrough and will see what will happen.
[/FONT]

---

### Post by bartoszek on 2023-07-09
Hi!

It took me a while, but here I am. Sadly no real progress had been made, newer kernel didn't change a thing and GPU passthrough is quite an overkill in my situation because it is my only GPU and I don't really know how it will work with my KVM... probably not so well as there will be no graphics to show me. So right now my plan is to, ehem, ignore those spikes and hope that newer kernel fixes the problem.

---

