---
title: "udev timeout after rebooting into kernel 3.2.0-45-generic"
date: 2013-05-31
forum: General Help
---

### Post by CharlesA on 2013-05-31
Hello,

I experienced the same thing after the kernel update to 3.2.0-44-generic about a week ago and "fixed it" by rebooting into 3.2.0-43. My system is running 12.04.2. I will add in the hardware specs in a little bit, but I was able to get some pictures of the looping message that shows up.

It looks very similar to the issues experienced in these threads:
[http://askubuntu.com/questions/293032/boot-problems-on-ubuntu13-04-recursive-fault-timeout-killing-sbin-modprobe](http://askubuntu.com/questions/293032/boot-problems-on-ubuntu13-04-recursive-fault-timeout-killing-sbin-modprobe)
[https://bugs.launchpad.net/ubuntu/+source/udev/+bug/1092102](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/1092102)

Any ideas how to troubleshoot this? As far as I can tell, /dev/sda1 isn't mounted, so no log files are written, but I can check from a livecd to see for sure.

I have attached some screenshots of the looping error messages.

EDIT: System specs:
i7 2600K 3.4GHz
Gigabyte Z68XP-UD3 BIOS F9
16GB DDR3
500GB OS drive
4TB hardware RAID array.

---

### Post by Doug S on 2013-05-31
I would (and this could end up taking a lot of time and tie up the computer as well): Have a look at the [change notes for the .44 kernel]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.2.44-precise/CHANGES") to see if something obvious is listed (I looked and didn't see anything obvious); Set up an environment to build the kernel (build 3.2.0.43-generic as your starting point kernel), and test it without making any changes, then start [a bisection]("https://wiki.ubuntu.com/Kernel/KernelBisection") with the objective of isolating the exact change that causes the issue (I think you will want this area: "Commit bisecting Ubuntu kernel versions" to break the .43 to .44 releases into the various commit steps); Meanwhile, test the [latest kernel PPAs]("http://kernel.ubuntu.com/~kernel-ppa/mainline/") to make sure the issue isn't fixed during this saga (I see a .46 kernel there).

You might be reluctant to do this stuff if your computer is a production server or similar, understandably.

Disclaimer note: myself, I have had limited success (read: always failed) completing a kernel bisection to an endpoint conclusion.

---

### Post by CharlesA on 2013-05-31
Thanks for the ideas Doug. I'm pretty hesitant to start messing around with different kernels as this is a production machine. I'll look into it further.

EDIT: I think this started happening -44 kernel too. Very, very strange.

---

### Post by Doug S on 2013-05-31
Charles, I see that you had said it had started happening with the .43 kernel also, which would tend to suggest some subtle timing issue that might have been there for some time, and came to the fore due to recent changes or ways of executing stuff. However, I see you edited that to say the .44 kernel, which would then be consistent with your original post, that the issue is not present in the .43 kernel, but present in the .44 kernel.
 
I understand your reluctance to start messing around with your production server. My best computer was bought with the intent of making it the main server for my LAN, but it never made it that far as I found it just to useful to have a test server where it doesn't matter if I mess it up.

---

### Post by CharlesA on 2013-05-31
Yeah, I'm booted into:

```
charles@Thor:~$ uname -r
3.2.0-43-generic

```

Now, but -44 and -45 have had issues for whatever reason. I'm going to be installing the 3.5 kernel tonight.

```
sudo apt-get install linux-image-generic-lts-quantal linux-headers-generic-lts-quantal
```

Hopefully it'll survive the reboot, but if not, I'll just stick with -43 and deal with it...

EDIT: I checked for logs when I rebooted into -43 but there were none, so I'm guessing it didn't even get to the point where it mounted /dev/sda1. I tried to google the PCI code thing in the above screenshot, but nothing turned up. Is there any way to find that "PCI ID"?

---

### Post by CharlesA on 2013-06-01
I had some help from matt_symes and it looks like something is wrong with the RAID module after booting into the new kernel.

```
00:00.0 Host bridge [0600]: Intel Corporation 2nd Generation Core Processor Family DRAM Controller [8086:0100] (rev 09)
00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0122] (rev 09)
00:16.0 Communication controller [0780]: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 [8086:1c3a] (rev 04)
00:1a.0 USB controller [0c03]: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 [8086:1c2d] (rev 05)
00:1b.0 Audio device [0403]: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller [8086:1c20] (rev 05)
00:1c.0 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 [8086:1c10] (rev b5)
00:1c.2 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 3 [8086:1c14] (rev b5)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev b5)
00:1c.4 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 5 [8086:1c18] (rev b5)
00:1c.5 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 6 [8086:1c1a] (rev b5)
00:1c.6 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 7 [8086:1c1c] (rev b5)
00:1c.7 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 8 [8086:1c1e] (rev b5)
00:1d.0 USB controller [0c03]: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 [8086:1c26] (rev 05)
00:1f.0 ISA bridge [0601]: Intel Corporation Z68 Express Chipset Family LPC Controller [8086:1c44] (rev 05)
00:1f.2 SATA controller [0106]: Intel Corporation 6 Series/C200 Series Chipset Family SATA AHCI Controller [8086:1c02] (rev 05)
00:1f.3 SMBus [0c05]: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller [8086:1c22] (rev 05)
[COLOR="#FF0000"]02:00.0 RAID bus controller [0104]: HighPoint Technologies, Inc. RocketRAID 2640 SAS/SATA Controller [1103:2640] (rev 02)[/COLOR]
03:00.0 PCI bridge [0604]: Integrated Technology Express, Inc. Device [1283:8892] (rev 30)
05:00.0 USB controller [0c03]: Etron Technology, Inc. EJ168 USB 3.0 Host Controller [1b6f:7023] (rev 01)
06:00.0 USB controller [0c03]: Etron Technology, Inc. EJ168 USB 3.0 Host Controller [1b6f:7023] (rev 01)
07:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
08:00.0 SATA controller [0106]: Marvell Technology Group Ltd. 88SE9172 SATA 6Gb/s Controller [1b4b:9172] (rev 11)
```

[https://bugs.launchpad.net/ubuntu/+source/udev/+bug/1092102](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/1092102)

I wonder if DKMS messed up the module again - even if I haven't seen the OS completely fail to boot when that module isn't working.

---

### Post by CharlesA on 2013-06-01
Alright, so I rebooted into the 3.5.x kernel pulled in from the linux-image-generic-lts-quantal metapackage and found out that the raid array was not seen even thought DKMS compiled the kernel modules.

I had to remove the modules from the DKMS tree, readd it, build and then install it and now it is working ok. I guess I will know if this worked for sure after the next kernel update.

As it stands, the 3.5 kernel did not freak out when it tried to access the RAID card even when the module for it failed to load.

---

