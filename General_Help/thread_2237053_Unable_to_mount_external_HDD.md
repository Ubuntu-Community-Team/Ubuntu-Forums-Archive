---
title: "Unable to mount external HDD"
date: 2014-07-30
forum: General Help
---

### Post by Roberto_Pacilio on 2014-07-30
Hello everyone.

I know the question sounds familiar, but my issue is very peculiar.

I have two laptops running Ubuntu 14.04 LTS.

The external HDD that I'm trying to mount works just fine with one of them (USB 2.0 connection). When I plug it in the other laptop (through USB 3.0) I cannot mount it. Issuing the **lsusb** command actually lists my device, but neither **gparted** nor **fdisk** show me my hard drive. I tried to look for **/dev/sdbX** with no luck. **dmesg | tail** shows me as last messages 
> [ 2976.134051] scsi75 : usb-storage 2-2:1.0[ 2977.132540] scsi 75:0:0:0: Direct-Access     MCBQE32G 5MPP             0000 PQ: 0 ANSI: 0
[ 2977.132941] sd 75:0:0:0: Attached scsi generic sg1 type 0
[ 2977.133097] sd 75:0:0:0: [sdb] 62533296 512-byte logical blocks: (32.0 GB/29.8 GiB)
[ 2977.133651] sd 75:0:0:0: [sdb] Write Protect is off
[ 2977.133653] sd 75:0:0:0: [sdb] Mode Sense: 33 00 00 00
[ 2977.134197] sd 75:0:0:0: [sdb] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[ 2977.137175]  sdb: sdb1 sdb2
[ 2977.140192] sd 75:0:0:0: [sdb] Attached SCSI disk
[ 2977.155006] usb 2-2: USB disconnect, device number 79 (number 79 is because it has been connected for a long time and I guess it tries to remount itself).

The two laptops are running the same version of ubuntu with the same kernel. What differs is the type of connection port (USB2.0 the one working, USB 3.0 the one not working) and the one who's not mounting the HDD has a flag libata.force=noncq in the GRUB_CONFIG (I guess it has nothing to do with all this stuff, but for the sake of completeness I should mention it).

Any help will be much appreciated.

Thank you

---

