---
title: "Ubuntu 12.04 freezes daily"
date: 2014-04-14
forum: General Help
---

### Post by schowell on 2014-04-14
Greetings,

If this is a duplicate problem, you are better at searching forums than I am and I am sincerely sorry for the duplicate.  Please direct me to the original post and I will remove this.  

My Ubuntu 12.04 desktop has been freezing daily and I am not sure the cause or how to fix it.  It often occurs within an hour of booting it and logging in.  My mouse and keyboard get locked out and I cannot get any response.  As recommended in this post, [http://askubuntu.com/questions/4408/what-should-i-do-when-ubuntu-freezes](http://askubuntu.com/questions/4408/what-should-i-do-when-ubuntu-freezes), I tried killing the X-server (yes I turned it on so that Ctrl-Alt-Backspace will do this).  I also tried dropping to a tty terminal using Ctrl-Alt-F1 but I cannot get it to respond.  I did not try recently but a believe I also tried using Alt-PrintScreen-REISUB with that not working either.  I end up trying the restart button on the case or if that doesn't work, holding down the power button.

Sometime it will work for hours and then I leave it on while away for an hour or more and come back to a black screen with no response to pressing any keys or the mouse.  This happened just now and I had to reboot it by pressing the restart button on the case.

Other times, it will just reboot unexpectedly.

As recommended in this post, [https://help.ubuntu.com/community/DebuggingSystemCrash](https://help.ubuntu.com/community/DebuggingSystemCrash), I checked the memory for error but it passed 3 full tests.  

My suspicion is that the problem is a hardware issue.  I have several other Ubuntu machines with a similar OS and software configuration with no such problems. If needed, I am fine replacing a part but not every part (e.g. replace a bad motherboard, video card, etc.) and I am not really sure how to determine what is causing the problem.
Here are my hardware specs:
Gigabyte GA-770TA-UD3 AM3 Motherboard ([http://www.gigabyte.com/products/product-page.aspx?pid=3272#ov](http://www.gigabyte.com/products/product-page.aspx?pid=3272#ov))
AMD Phenom II X4 965 Processor HDZ965FBGMBOX ([http://products.amd.com/en-us/DesktopCPUDetail.aspx?id=617&f1=&f2=&f3=&f4=&f5=&f6=&f7=&f8=&f9=&f10=&f11=&f12=](http://products.amd.com/en-us/DesktopCPUDetail.aspx?id=617&f1=&f2=&f3=&f4=&f5=&f6=&f7=&f8=&f9=&f10=&f11=&f12=))
Gigabyte GV-N240D5-512I Nvidia GeForce GT 240 video card ([http://www.nvidia.com/object/product_geforce_gt_240_us.html](http://www.nvidia.com/object/product_geforce_gt_240_us.html))
Patriot Gamer 2 Series 8GB (2 x 4GB) 240-Pin DDR3 SDRAM DDR3 1600 Desktop Memory Model PGD38G1600ELK

I have several hard drives, maybe 5 or 6; I can get all the models if necessary.  I installed Ubuntu using a software raid 0.  

I recently replaced the video card with an old one I had lying around.  I removed all the nvidia drives using these commands:
```

sudo apt-get remove --purge nvidia-*
sudo apt-get install ubuntu-desktop
sudo rm /etc/X11/xorg.confThe machine still froze.

```

I since reistalled my Nvidia GT 240 and am using the NVIDIA version 331-updates driver.

I update packages frequently so it should not be from old software.

output from 
```

>uname -a
Linux beowulf 3.8.0-38-generic #56~precise1-Ubuntu SMP Thu Mar 13 16:22:48 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

>sudo lspci
00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD/ATI] RX780/RX790 Host Bridge
00:02.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RX780/RD790 PCI to PCI bridge (external gfx0 port A)
00:06.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RD790 PCI to PCI bridge (PCI express gpp port C)
00:07.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RX780/RD790 PCI to PCI bridge (PCI express gpp port D)
00:09.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RD790 PCI to PCI bridge (PCI express gpp port E)
00:0a.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RD790 PCI to PCI bridge (PCI express gpp port F)
00:11.0 SATA controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 SATA Controller [IDE mode]
00:12.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.1 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0 USB OHCI1 Controller
00:12.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.1 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0 USB OHCI1 Controller
00:13.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 SMBus Controller (rev 3c)
00:14.1 IDE interface: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 IDE Controller
00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 LPC host controller
00:14.4 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 PCI to PCI Bridge
00:14.5 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 10h Processor Link Control
01:00.0 VGA compatible controller: NVIDIA Corporation GT215 [GeForce GT 240] (rev a2)
01:00.1 Audio device: NVIDIA Corporation High Definition Audio Controller (rev a1)
02:00.0 SATA controller: JMicron Technology Corp. JMB363 SATA/IDE Controller (rev 03)
02:00.1 IDE interface: JMicron Technology Corp. JMB363 SATA/IDE Controller (rev 03)
03:00.0 SATA controller: Marvell Technology Group Ltd. 88SE9128 PCIe SATA 6 Gb/s RAID controller (rev 11)
04:00.0 USB controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 03)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 03)
06:0e.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)

```
I am not sure where crash/freeze reports are logged but I can upload any that would be helpful.  \

Thank you for any help with this.

---

### Post by sam_baker2 on 2014-04-14
I have xubuntu 12.04 and my system locked up today as well as yesterday, and I can't recall it doing that in a long long time. I think it must have something to do with the recent updates. I have a Gigabyte MB and a Nvidia GeForce 650 vid card. I am going to reinstall with 14.04 in a few weeks and I hope that will solve it.

---

### Post by sam_baker2 on 2014-04-14
also ~ a year or so ago, I got a lock up, and I set the persistence mode on my Nvidia card to "1".  It seemed to work for a while. You may want to try that if you haven't already:    ```
  /usr/bin/nvidia-smi -pm 1 
``` If it does any good, you may want to put it in your rc.local file so you won't have to type it in every time you boot up.

---

### Post by schowell on 2014-04-14
My issue has been happening for the last 3 or 4 months so I doubt it is recent updates.

---

### Post by schowell on 2014-04-14
> **sam_baker2 said:**
> also ~ a year or so ago, I got a lock up, and I set the persistence mode on my Nvidia card to "1".  It seemed to work for a while. You may want to try that if you haven't already:    ```
  /usr/bin/nvidia-smi -pm 1 
``` 

I have not modified the persistence mode for nvidia-smi previously.  I just read on [https://developer.nvidia.com/nvidia-management-library-nvml](https://developer.nvidia.com/nvidia-management-library-nvml) about it[INDENT]Persistence mode: Control whether the NVIDIA driver stays loaded when no active clients are connected to the GPU. 
[/INDENT]

I would expect this to be the default behavior for a primary video card.  I understand for the dual graphics, disabling the NVIDIA driver/card (would these be the same?) but shouldn't this already be the case?  I guess I am wondering if there any reason I would not want to make this the default behavior?

---

