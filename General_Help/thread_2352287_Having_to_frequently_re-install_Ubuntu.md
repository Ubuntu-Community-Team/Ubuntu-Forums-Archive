---
title: "Having to frequently re-install Ubuntu"
date: 2017-02-11
forum: General Help
---

### Post by raleigh3 on 2017-02-11
I am having a big problem having to re-install Ubuntu 16.04.

Had to re-install at least 3 times in a week.

It boots to a black screen.

I tried Enter, Ctrl D, systemctl, etc, but nothing helped.

I also used the repair option from a Boot Repair cd.

Can someone please help me diagnose this problem ?

Thanks a lot.

---

### Post by oldfred on 2017-02-11
What brand/model system. And what video card/chip(s)?

Does live installer work in live mode without issue?

Black screen is usually a video driver issue.
If live installer works ok.
 #To see video:
sudo lshw -c display
sudo lshw | grep -A 11 display
lspci | grep VGA

---

### Post by raleigh3 on 2017-02-11
Thanks. Live installer works o.k.

 ```
andy@7:~$ sudo lshw -c display
  *-display               
       description: VGA compatible controller
       product: Kaveri [Radeon R7 Graphics]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 1
       bus info: pci@0000:00:01.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:33 memory:c0000000-cfffffff memory:d0000000-d07fffff ioport:f000(size=256) memory:feb00000-feb3ffff memory:feb40000-feb5ffff
andy@7:~$ sudo lshw | grep -A 11 display
        *-display
             description: VGA compatible controller
             product: Kaveri [Radeon R7 Graphics]
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
             configuration: driver=radeon latency=0
             resources: irq:33 memory:c0000000-cfffffff memory:d0000000-d07fffff ioport:f000(size=256) memory:feb00000-feb3ffff memory:feb40000-feb5ffff
andy@7:~$ lspci | grep VGA 
00:01.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Kaveri [Radeon R7 Graphics]

```

---

### Post by ajgreeny on 2017-02-11
Command ```
lspci -k -s 00:01.0
``` should tell us what kernel driver is used at present by your system; I think it will say radeon, but let's see first.

---

### Post by raleigh3 on 2017-02-11
00:01.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Kaveri [Radeon R7 Graphics]
    Subsystem: Gigabyte Technology Co., Ltd Kaveri [Radeon R7 Graphics]
    Kernel driver in use: radeon
    Kernel modules: radeon

---

### Post by oldfred on 2017-02-11
I do not know where AMD is at, as I do not have AMD graphics.
They are converting from closed source to only open source, but not everything fully supported yet.

       [https://help.ubuntu.com/community/AMDGPU-PRO-Driver](https://help.ubuntu.com/community/AMDGPU-PRO-Driver)
AMDGPU & Radeon DDX Updated - Better 2D Performance, Tear Free, DRI3 Default Nov 2016
Also needs  X.Org Server 1.19
[http://www.phoronix.com/scan.php?page=news_item&px=Radeon-AMDGPU-1.19-Updates](http://www.phoronix.com/scan.php?page=news_item&px=Radeon-AMDGPU-1.19-Updates)
Ubuntu 16.04 How-To Install/Uninstall AMD Radeon&#8482; Software AMDGPU-PRO Driver
[https://support.amd.com/en-us/kb-articles/Pages/AMDGPU-PRO-Install.aspx](https://support.amd.com/en-us/kb-articles/Pages/AMDGPU-PRO-Install.aspx) 
   [https://wiki.ubuntu.com/XenialXerus/ReleaseNotes#fglrx](https://wiki.ubuntu.com/XenialXerus/ReleaseNotes#fglrx)

---

### Post by raleigh3 on 2017-02-13
I solved the problem by reinstalling Ubuntu.

---

