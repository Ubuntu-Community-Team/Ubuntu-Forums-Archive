---
title: "System Freezes while transferring large files"
date: 2016-12-24
forum: General Help
---

### Post by orestis-0 on 2016-12-24
Good morning guys, 


So after many "experiments" I concluded that: When I move a 40gb folder from my HDD to my SSD(where Ubuntu 16.10 is installed) the transfer is slow and the laptop might freeze up to 10 minutes. On the other hand when I move the same folder from my SSD to my HDD it is much faster and there is no lagging, everything is smooth. What can be the problem? 

Thanks

---

### Post by TheFu on 2016-12-24
SATA or eSATA connected?  I don't know.

USB connected?  UAS seems to be a common issue with USB storage.  Some people have blacklisted the UAS module from their USB storage and found it worked better.  That "fix" didn't work for me, sadly.

---

### Post by orestis-0 on 2016-12-24
Both of the hardrives are in my laptop and both are Ext4. I don't know if the connection is SATA or eSATA, how do I check?

---

### Post by orestis-0 on 2016-12-24
So I tried the same operation with my external hard drive and it works fine. So it looks like there is something wrong with my laptop's HDD. I run HDSentinel and it says that both SSD and HDD are ok. My laptop is 1 month old so that's pretty weird....

---

### Post by TheFu on 2016-12-24
lspci
lsusb

Where are the storage devices seen? If in the USB parts, run **sudo lshw -c storage** and look at the storage drivers - uas ... or usb-storage?

---

### Post by orestis-0 on 2016-12-25
```
orestis@orestis-Aspire-F5-573G:~$ lspci00:00.0 Host bridge: Intel Corporation Device 5904 (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Device 5916 (rev 02)
00:14.0 USB controller: Intel Corporation Sunrise Point-LP USB 3.0 xHCI Controller (rev 21)
00:14.2 Signal processing controller: Intel Corporation Sunrise Point-LP Thermal subsystem (rev 21)
00:15.0 Signal processing controller: Intel Corporation Sunrise Point-LP Serial IO I2C Controller #0 (rev 21)
00:16.0 Communication controller: Intel Corporation Sunrise Point-LP CSME HECI #1 (rev 21)
00:17.0 SATA controller: Intel Corporation Sunrise Point-LP SATA Controller [AHCI mode] (rev 21)
00:1c.0 PCI bridge: Intel Corporation Device 9d10 (rev f1)
00:1d.0 PCI bridge: Intel Corporation Sunrise Point-LP PCI Express Root Port #9 (rev f1)
00:1d.2 PCI bridge: Intel Corporation Device 9d1a (rev f1)
00:1d.3 PCI bridge: Intel Corporation Device 9d1b (rev f1)
00:1f.0 ISA bridge: Intel Corporation Device 9d58 (rev 21)
00:1f.2 Memory controller: Intel Corporation Sunrise Point-LP PMC (rev 21)
00:1f.3 Audio device: Intel Corporation Device 9d71 (rev 21)
00:1f.4 SMBus: Intel Corporation Sunrise Point-LP SMBus (rev 21)
01:00.0 3D controller: NVIDIA Corporation Device 179c (rev ff)
03:00.0 Network controller: Qualcomm Atheros QCA9377 802.11ac Wireless Network Adapter (rev 31)
04:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTL8411B PCI Express Card Reader (rev 01)
04:00.1 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 12)
orestis@orestis-Aspire-F5-573G:~$ lsusb
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 0bda:57f2 Realtek Semiconductor Corp. 
Bus 001 Device 002: ID 0489:e0a3 Foxconn / Hon Hai 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub



```

This is what I got from the commands I don't see the storage devices....

---

### Post by orestis-0 on 2016-12-28
Any ideas?

---

### Post by TheFu on 2016-12-28
Did the last cmd suggested provide any leads?

When there are slowdowns, I use a systematic method of working through all the layers of hardware, drivers, software to determine the root cause. Sometimes there isn't any solution when it is a hardware limitation. 

Start by looking at every piece of hardware involved. Chips used along the way - southbridge/northbridge, disk controllers, etc. Design specifications for the USB-bus, PCI-bus, motherboard, cache lanes, cabling, disk controller, and physical disk performance limitations, etc.  Do this for every part of the HW used. 2 systems?  Then 2x the work, plus all the networking equipment. Look at backplane limitations. Sometimes different ports connect to different internal channels. Sometimes different switch ports have different bandwidth speeds.  If the switch backplane only supports 200Mbps, don't expect to get more just because the NICs are GigE, for example.  Same applies to motherboard channels.

Learned that one of my motherboards was poorly designed and couldn't support USB3 speeds. They never expected someone to want that sort of PCIe bandwidth, in fairness. All the PCI and PCIe devices were connected to the same backplane. SATA was on a different channel. Great, except the PCI/PCIe/USB parts weren't capable of handling enough total bandwidth, so 1 USB3 SATA device flooded the entire machine, effectively blocking all other I/O inside the system.  Design flaw, at least for my needs.  No way to move the USB3 connection to the SATA channel, plus all 6 SATA ports already had disks.  Getting a new disk controller wouldn't help. Nothing I could do would help the 2010 motherboard handle more I/O except to replace the motherboard ... and if doing that, probably need to replace the CPU too,  getting more I/O capacity in the motherboard.

Sometimes the motherboard vendor doesn't provide internal system diagrams, so going back the the reference designs based on the chipset(s) used is all we can do.  The motherboard model usually references some AMD/Intel reference design.

Almost every technical term you come across will have a wikipedia article explaining it. Best not to assume what something does. Look it up. That should get you started.

But don't overlook the simple things like a bad cable or failing disk.  The log files should have something about that if the HW is failing.

---

