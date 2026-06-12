---
title: "e1000e NIC issues"
date: 2022-09-10
forum: General Help
---

### Post by pook2022 on 2022-09-10
My 22.04 machine only downloads at 840KB/s maximum while the Windows 10 machine next to it gets 4MB/s
Swapped cables between them and that doesn't change anything.
I've been trawling through the e1000e related issues hoping for some answers.  
Added 'pcie_aspm=off' to /etc/modules.  Didn't do anything
Should I be using a different driver?
Anyone have any thoughts?

- Pook

dmesg
> [    3.836765] e1000e: Intel(R) PRO/1000 Network Driver
[    3.836768] e1000e: Copyright(c) 1999 - 2015 Intel Corporation.
[    3.837135] e1000e 0000:00:1f.6: Interrupt Throttling Rate (ints/sec) set to dynamic conservative mode
[    4.490893] e1000e 0000:00:1f.6 0000:00:1f.6 (uninitialized): registered PHC clock
[    4.562339] e1000e 0000:00:1f.6 eth0: (PCI Express:2.5GT/s:Width x1) 18:c0:4d:26:c8:6e
[    4.562342] e1000e 0000:00:1f.6 eth0: Intel(R) PRO/1000 Network Connection
[    4.562448] e1000e 0000:00:1f.6 eth0: MAC: 13, PHY: 12, PBA No: FFFFFF-0FF
[   10.871151] e1000e 0000:00:1f.6 eno1: renamed from eth0
[   17.135885] e1000e 0000:00:1f.6 eno1: NIC Link is Up 1000 Mbps Full Duplex, Flow Control: Rx/Tx


lscpi
> 00:00.0 Host bridge: Intel Corporation Device 9b43 (rev 05)
00:02.0 VGA compatible controller: Intel Corporation CometLake-S GT2 [UHD Graphics 630] (rev 05)
00:12.0 Signal processing controller: Intel Corporation Comet Lake PCH Thermal Controller
00:14.0 USB controller: Intel Corporation Comet Lake USB 3.1 xHCI Host Controller
00:14.2 RAM memory: Intel Corporation Comet Lake PCH Shared SRAM
00:16.0 Communication controller: Intel Corporation Comet Lake HECI Controller
00:17.0 RAID bus controller: Intel Corporation SATA Controller [RAID mode]
00:1b.0 PCI bridge: Intel Corporation Comet Lake PCI Express Root Port #17 (rev f0)
00:1b.4 PCI bridge: Intel Corporation Comet Lake PCI Express Root Port #21 (rev f0)
00:1c.0 PCI bridge: Intel Corporation Device 06b8 (rev f0)
00:1c.4 PCI bridge: Intel Corporation Device 06bc (rev f0)
00:1d.0 PCI bridge: Intel Corporation Comet Lake PCI Express Root Port #9 (rev f0)
00:1d.4 PCI bridge: Intel Corporation Device 06b4 (rev f0)
00:1f.0 ISA bridge: Intel Corporation Device 0685
00:1f.3 Audio device: Intel Corporation Comet Lake PCH cAVS
00:1f.4 SMBus: Intel Corporation Comet Lake PCH SMBus Controller
00:1f.5 Serial bus controller: Intel Corporation Comet Lake PCH SPI Controller
**00:1f.6 Ethernet controller: Intel Corporation Ethernet Connection (11) I219-V**
02:00.0 RAID bus controller: Broadcom / LSI SAS2008 PCI-Express Fusion-MPT SAS-2 [Falcon] (rev 03)
05:00.0 Non-Volatile memory controller: Sandisk Corp WD Blue SN550 NVMe SSD (rev 01)



modinfo
> filename:       /lib/modules/5.15.0-47-generic/kernel/drivers/net/ethernet/intel/e1000e/e1000e.ko
license:        GPL v2
description:    Intel(R) PRO/1000 Network Driver
author:         Intel Corporation, <linux.nics@intel.com>
srcversion:     BEA03E38C3E041502C42552
alias:          pci:v00008086d00005511sv*sd*bc*sc*i*
alias:          pci:v00008086d00005510sv*sd*bc*sc*i*
alias:          pci:v00008086d0000550Fsv*sd*bc*sc*i*
alias:          pci:v00008086d0000550Esv*sd*bc*sc*i*
alias:          pci:v00008086d0000550Dsv*sd*bc*sc*i*
alias:          pci:v00008086d0000550Csv*sd*bc*sc*i*
alias:          pci:v00008086d0000550Bsv*sd*bc*sc*i*
alias:          pci:v00008086d0000550Asv*sd*bc*sc*i*
alias:          pci:v00008086d00000DC8sv*sd*bc*sc*i*
alias:          pci:v00008086d00000DC7sv*sd*bc*sc*i*
alias:          pci:v00008086d00001A1Dsv*sd*bc*sc*i*
alias:          pci:v00008086d00001A1Csv*sd*bc*sc*i*
alias:          pci:v00008086d00001A1Fsv*sd*bc*sc*i*
alias:          pci:v00008086d00001A1Esv*sd*bc*sc*i*
alias:          pci:v00008086d00000DC6sv*sd*bc*sc*i*
alias:          pci:v00008086d00000DC5sv*sd*bc*sc*i*
alias:          pci:v00008086d000015F5sv*sd*bc*sc*i*
alias:          pci:v00008086d000015F4sv*sd*bc*sc*i*
alias:          pci:v00008086d000015FAsv*sd*bc*sc*i*
alias:          pci:v00008086d000015F9sv*sd*bc*sc*i*
alias:          pci:v00008086d000015FCsv*sd*bc*sc*i*
alias:          pci:v00008086d000015FBsv*sd*bc*sc*i*
alias:          pci:v00008086d00000D55sv*sd*bc*sc*i*
alias:          pci:v00008086d00000D53sv*sd*bc*sc*i*
alias:          pci:v00008086d00000D4Dsv*sd*bc*sc*i*
alias:          pci:v00008086d00000D4Csv*sd*bc*sc*i*
alias:          pci:v00008086d00000D4Fsv*sd*bc*sc*i*
alias:          pci:v00008086d00000D4Esv*sd*bc*sc*i*
alias:          pci:v00008086d000015E2sv*sd*bc*sc*i*
alias:          pci:v00008086d000015E1sv*sd*bc*sc*i*
alias:          pci:v00008086d000015E0sv*sd*bc*sc*i*
alias:          pci:v00008086d000015DFsv*sd*bc*sc*i*
alias:          pci:v00008086d000015BCsv*sd*bc*sc*i*
alias:          pci:v00008086d000015BBsv*sd*bc*sc*i*
alias:          pci:v00008086d000015BEsv*sd*bc*sc*i*
alias:          pci:v00008086d000015BDsv*sd*bc*sc*i*
alias:          pci:v00008086d000015D6sv*sd*bc*sc*i*
alias:          pci:v00008086d000015E3sv*sd*bc*sc*i*
alias:          pci:v00008086d000015D8sv*sd*bc*sc*i*
alias:          pci:v00008086d000015D7sv*sd*bc*sc*i*
alias:          pci:v00008086d000015B9sv*sd*bc*sc*i*
alias:          pci:v00008086d000015B8sv*sd*bc*sc*i*
alias:          pci:v00008086d000015B7sv*sd*bc*sc*i*
alias:          pci:v00008086d00001570sv*sd*bc*sc*i*
alias:          pci:v00008086d0000156Fsv*sd*bc*sc*i*
alias:          pci:v00008086d000015A3sv*sd*bc*sc*i*
alias:          pci:v00008086d000015A2sv*sd*bc*sc*i*
alias:          pci:v00008086d000015A1sv*sd*bc*sc*i*
alias:          pci:v00008086d000015A0sv*sd*bc*sc*i*
alias:          pci:v00008086d00001559sv*sd*bc*sc*i*
alias:          pci:v00008086d0000155Asv*sd*bc*sc*i*
alias:          pci:v00008086d0000153Bsv*sd*bc*sc*i*
alias:          pci:v00008086d0000153Asv*sd*bc*sc*i*
alias:          pci:v00008086d00001503sv*sd*bc*sc*i*
alias:          pci:v00008086d00001502sv*sd*bc*sc*i*
alias:          pci:v00008086d000010F0sv*sd*bc*sc*i*
alias:          pci:v00008086d000010EFsv*sd*bc*sc*i*
alias:          pci:v00008086d000010EBsv*sd*bc*sc*i*
alias:          pci:v00008086d000010EAsv*sd*bc*sc*i*
alias:          pci:v00008086d00001525sv*sd*bc*sc*i*
alias:          pci:v00008086d000010DFsv*sd*bc*sc*i*
alias:          pci:v00008086d000010DEsv*sd*bc*sc*i*
alias:          pci:v00008086d000010CEsv*sd*bc*sc*i*
alias:          pci:v00008086d000010CDsv*sd*bc*sc*i*
alias:          pci:v00008086d000010CCsv*sd*bc*sc*i*
alias:          pci:v00008086d000010CBsv*sd*bc*sc*i*
alias:          pci:v00008086d000010F5sv*sd*bc*sc*i*
alias:          pci:v00008086d000010BFsv*sd*bc*sc*i*
alias:          pci:v00008086d000010E5sv*sd*bc*sc*i*
alias:          pci:v00008086d0000294Csv*sd*bc*sc*i*
alias:          pci:v00008086d000010BDsv*sd*bc*sc*i*
alias:          pci:v00008086d000010C3sv*sd*bc*sc*i*
alias:          pci:v00008086d000010C2sv*sd*bc*sc*i*
alias:          pci:v00008086d000010C0sv*sd*bc*sc*i*
alias:          pci:v00008086d00001501sv*sd*bc*sc*i*
alias:          pci:v00008086d00001049sv*sd*bc*sc*i*
alias:          pci:v00008086d0000104Dsv*sd*bc*sc*i*
alias:          pci:v00008086d0000104Bsv*sd*bc*sc*i*
alias:          pci:v00008086d0000104Asv*sd*bc*sc*i*
alias:          pci:v00008086d000010C4sv*sd*bc*sc*i*
alias:          pci:v00008086d000010C5sv*sd*bc*sc*i*
alias:          pci:v00008086d0000104Csv*sd*bc*sc*i*
alias:          pci:v00008086d000010BBsv*sd*bc*sc*i*
alias:          pci:v00008086d00001098sv*sd*bc*sc*i*
alias:          pci:v00008086d000010BAsv*sd*bc*sc*i*
alias:          pci:v00008086d00001096sv*sd*bc*sc*i*
alias:          pci:v00008086d0000150Csv*sd*bc*sc*i*
alias:          pci:v00008086d000010F6sv*sd*bc*sc*i*
alias:          pci:v00008086d000010D3sv*sd*bc*sc*i*
alias:          pci:v00008086d0000109Asv*sd*bc*sc*i*
alias:          pci:v00008086d0000108Csv*sd*bc*sc*i*
alias:          pci:v00008086d0000108Bsv*sd*bc*sc*i*
alias:          pci:v00008086d0000107Fsv*sd*bc*sc*i*
alias:          pci:v00008086d0000107Esv*sd*bc*sc*i*
alias:          pci:v00008086d0000107Dsv*sd*bc*sc*i*
alias:          pci:v00008086d000010B9sv*sd*bc*sc*i*
alias:          pci:v00008086d000010D5sv*sd*bc*sc*i*
alias:          pci:v00008086d000010DAsv*sd*bc*sc*i*
alias:          pci:v00008086d000010D9sv*sd*bc*sc*i*
alias:          pci:v00008086d00001060sv*sd*bc*sc*i*
alias:          pci:v00008086d000010A5sv*sd*bc*sc*i*
alias:          pci:v00008086d000010BCsv*sd*bc*sc*i*
alias:          pci:v00008086d000010A4sv*sd*bc*sc*i*
alias:          pci:v00008086d0000105Fsv*sd*bc*sc*i*
alias:          pci:v00008086d0000105Esv*sd*bc*sc*i*
depends:
retpoline:      Y
intree:         Y
name:           e1000e
vermagic:       5.15.0-47-generic SMP mod_unload modversions
sig_id:         PKCS#7
signer:         Build time autogenerated kernel key
sig_key: xx:xx
sig_hashalgo:   sha512
signature: *xxxxToo many emoticons!!xxxxx*
parm:           debug:Debug level (0=none,...,16=all) (int)
parm:           copybreak:Maximum size of packet that is copied to a new buffer on receive (uint)
parm:           TxIntDelay:Transmit Interrupt Delay (array of int)
parm:           TxAbsIntDelay:Transmit Absolute Interrupt Delay (array of int)
parm:           RxIntDelay:Receive Interrupt Delay (array of int)
parm:           RxAbsIntDelay:Receive Absolute Interrupt Delay (array of int)
parm:           InterruptThrottleRate:Interrupt Throttling Rate (array of int)
parm:           IntMode:Interrupt Mode (array of int)
parm:           SmartPowerDownEnable:Enable PHY smart power down (array of int)
parm:           KumeranLockLoss:Enable Kumeran lock loss workaround (array of int)
parm:           WriteProtectNVM:Write-protect NVM [WARNING: disabling this can lead to corrupted NVM] (array of int)
parm:           CrcStripping:Enable CRC Stripping, disable if your BMC needs the CRC (array of int)


---

### Post by TheFu on 2022-09-10
Please use "code tags", not quote tags, when posting terminal output.  This will keep the columns.

I don't have any v-219 Intel NICs, but all the others get 920-940 Mbps connections, including those using the e1000e driver. I've never had to do anything on Linux to get that performance.
I suspect the issue is with the switch/router or cables.  It is unclear what you mean by "switched" cables. Please clarify.

4MBps is nothing and shouldn't be a goal.  If you connect between 2 system on your LAN and transfer files, assuming both are GigE connected with CAT5e or better cables, those transfers would be limited by the speed of storage, not the NICs.  Typically 650+ Mbps.  Use ssh/scp/sftp ... or iperf3.

1 MBps == 8 Mbps.
Network transfers and disk transfers are always in Mbps/Gbps, so be consistent and very careful with the units.

If there is any wifi involved anywhere, all bets are off. Too much interference, bad wifi settings, and other environmental problems to troubleshoot wifi.

---

### Post by pook2022 on 2022-09-10
Found it.
Was just a Filezilla issue.
Should have tested it more.

[https://forum.filezilla-project.org/viewtopic.php?t=40513](https://forum.filezilla-project.org/viewtopic.php?t=40513)

sysctl -w net.ipv4.tcp_rmem="40960 873800 62914560"
sysctl -w net.core.rmem_max=16000000

---

### Post by TheFu on 2022-09-10
Thanks for letting us know you found the problem.

Please help others NOT waste their time by using the "Thread Tools" button/link at the top and mark this thread as SOLVED.

---

