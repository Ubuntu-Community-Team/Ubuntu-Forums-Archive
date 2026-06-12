---
title: "Ubuntu 17.10 Upgrade: GRUB issues"
date: 2017-11-01
forum: General Help
---

### Post by mrswadge on 2017-11-01
> **spencer2 said:**
> I ran a bunch of updates today, but acer still won't shut down. When i turn it off/reboot, it never actually shuts down & I have to do the manual button hold. 
Help please

I had a similar experience. I upgraded from 17.04 to 17.10 - it destroyed the bootloader configuration and so when rebooting it was going straight into windows and grub was not involved. I had to adjust my BIOS boot settings to use grub before windows to reinstate the bootloader. I had two entries for Ubuntu, one for grub and one for shim. I've moved the grub one up, but not the shim one as I don't really know what that is.

I now have the remaining problem that when I shutdown, it goes to a black console screen with no information, only a blinking cursor in the top left of the screen. I have to manually shutdown using the physical power button.

```

user@computer:~$ sudo bootctl
Using EFI System Partition at /boot/efi.
System:
     Firmware: n/a (n/a)
  Secure Boot: disabled
   Setup Mode: user


Current Loader:
      Product: n/a
          ESP: n/a
         File: âân/a


Boot Loader Binaries:
          ESP: /boot/efi (/dev/disk/by-partuuid/9a59fa7a-306f-47fe-88d3-886312cae760)
systemd-boot not installed in ESP.
         File: ââ/EFI/BOOT/bootx64.efi


Boot Loader Entries in EFI Variables:
        Title: Ubuntu
           ID: 0x0006
       Status: active, boot-order
    Partition: /dev/disk/by-partuuid/9a59fa7a-306f-47fe-88d3-886312cae760
         File: ââ/EFI/ubuntu/grubx64.efi


        Title: Windows Boot Manager
           ID: 0x0001
       Status: active, boot-order
    Partition: /dev/disk/by-partuuid/9a59fa7a-306f-47fe-88d3-886312cae760
         File: ââ/EFI/Microsoft/Boot/bootmgfw.efi


        Title: ubuntu
           ID: 0x0000
       Status: active, boot-order
    Partition: /dev/disk/by-partuuid/9a59fa7a-306f-47fe-88d3-886312cae760
         File: ââ/EFI/ubuntu/shimx64.efi

```

I tried setting acpi=force in [COLOR=#000000][FONT=&amp]/etc/default/grub[/FONT][/COLOR] but this did not make any difference. I'm trying to get into Linux and initially after installing 17.04 it was great, but this kind of problem is a huge disappointment. Is upgrading always this difficult?

Any ideas on how to debug this issue are very welcome, please bear in mind that I am capable, but not an expert Linux user.

Thanks,
Stuart

[FONT=Verdana]
[/FONT]

---

### Post by vasa1 on 2017-11-01
Moved to its own thread.

---

### Post by mrswadge on 2017-11-01
I have reverted the change to [COLOR=#000000]/etc/default/grub as it appeared to make no difference.
[/COLOR]
I've seen some posts regarding Nvidia display drivers and 'Wayland'. I found a way to disable Wayland via editing **/etc/gdm3/custom.conf** and uncomment the line**#WaylandEnable=false** by removing the **#** in front. I'll try this and report back my findings.

I thought it maybe useful to give a hardware summary. It's a Dell laptop, Alienware M14X R2.

```

user@computer:~# lspci -nnk
00:00.0 Host bridge [0600]: Intel Corporation 3rd Gen Core processor DRAM Controller [8086:0154] (rev 09)
        Subsystem: Dell 3rd Gen Core processor DRAM Controller [1028:0552]
        Kernel driver in use: ivb_uncore
00:01.0 PCI bridge [0604]: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port [8086:0151] (rev 09)
        Kernel driver in use: pcieport
        Kernel modules: shpchp
00:02.0 VGA compatible controller [0300]: Intel Corporation 3rd Gen Core processor Graphics Controller [8086:0166] (rev 09)
        Subsystem: Dell 3rd Gen Core processor Graphics Controller [1028:0552]
        Kernel driver in use: i915
        Kernel modules: i915
00:14.0 USB controller [0c03]: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller [8086:1e31] (rev 04)
        Subsystem: Dell 7 Series/C210 Series Chipset Family USB xHCI Host Controller [1028:0552]
        Kernel driver in use: xhci_hcd
00:16.0 Communication controller [0780]: Intel Corporation 7 Series/C216 Chipset Family MEI Controller #1 [8086:1e3a] (rev 04)
        Subsystem: Dell 7 Series/C216 Chipset Family MEI Controller [1028:0552]
        Kernel driver in use: mei_me
        Kernel modules: mei_me
00:1a.0 USB controller [0c03]: Intel Corporation 7 Series/C216 Chipset Family USB Enhanced Host Controller #2 [8086:1e2d] (rev 04)
        Subsystem: Dell 7 Series/C216 Chipset Family USB Enhanced Host Controller [1028:0552]
        Kernel driver in use: ehci-pci
00:1b.0 Audio device [0403]: Intel Corporation 7 Series/C216 Chipset Family High Definition Audio Controller [8086:1e20] (rev 04)
        Subsystem: Dell 7 Series/C216 Chipset Family High Definition Audio Controller [1028:0552]
        Kernel driver in use: snd_hda_intel
        Kernel modules: snd_hda_intel
00:1c.0 PCI bridge [0604]: Intel Corporation 7 Series/C216 Chipset Family PCI Express Root Port 1 [8086:1e10] (rev c4)
        Kernel driver in use: pcieport
        Kernel modules: shpchp
00:1c.2 PCI bridge [0604]: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 3 [8086:1e14] (rev c4)
        Kernel driver in use: pcieport
        Kernel modules: shpchp
00:1c.3 PCI bridge [0604]: Intel Corporation 7 Series/C216 Chipset Family PCI Express Root Port 4 [8086:1e16] (rev c4)
        Kernel driver in use: pcieport
        Kernel modules: shpchp
00:1d.0 USB controller [0c03]: Intel Corporation 7 Series/C216 Chipset Family USB Enhanced Host Controller #1 [8086:1e26] (rev 04)
        Subsystem: Dell 7 Series/C216 Chipset Family USB Enhanced Host Controller [1028:0552]
        Kernel driver in use: ehci-pci
00:1f.0 ISA bridge [0601]: Intel Corporation HM77 Express Chipset LPC Controller [8086:1e57] (rev 04)
        Subsystem: Dell HM77 Express Chipset LPC Controller [1028:0552]
        Kernel driver in use: lpc_ich
        Kernel modules: lpc_ich
00:1f.2 RAID bus controller [0104]: Intel Corporation 82801 Mobile SATA Controller [RAID mode] [8086:282a] (rev 04)
        Subsystem: Dell 82801 Mobile SATA Controller [RAID mode] [1028:0552]
        Kernel driver in use: ahci
        Kernel modules: ahci
00:1f.3 SMBus [0c05]: Intel Corporation 7 Series/C216 Chipset Family SMBus Controller [8086:1e22] (rev 04)
        Subsystem: Dell 7 Series/C216 Chipset Family SMBus Controller [1028:0552]
        Kernel modules: i2c_i801
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GK107M [GeForce GT 650M] [10de:0fd1] (rev a1)
        Subsystem: Dell GK107M [GeForce GT 650M] [1028:0552]
        Kernel driver in use: nouveau
        Kernel modules: nvidiafb, nouveau
01:00.1 Audio device [0403]: NVIDIA Corporation GK107 HDMI Audio Controller [10de:0e1b] (rev a1)
        Kernel driver in use: snd_hda_intel
        Kernel modules: snd_hda_intel
07:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8151 v2.0 Gigabit Ethernet [1969:1083] (rev c0)
        Subsystem: Dell AR8151 v2.0 Gigabit Ethernet [1028:0552]
        Kernel driver in use: atl1c
        Kernel modules: atl1c
08:00.0 Network controller [0280]: Qualcomm Atheros AR9462 Wireless Network Adapter [168c:0034] (rev 01)
        Subsystem: Bigfoot Networks, Inc. Killer Wireless-N 1202 Half-size Mini PCIe Card [1a56:2003]
        Kernel driver in use: ath9k
        Kernel modules: ath9k
09:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5209 PCI Express Card Reader [10ec:5209] (rev 01)
        Subsystem: Dell RTS5209 PCI Express Card Reader [1028:0552]
        Kernel driver in use: rtsx_pci
        Kernel modules: rtsx_pci
09:00.1 SD Host controller [0805]: Realtek Semiconductor Co., Ltd. RTS5209 PCI Express Card Reader [10ec:5209] (rev 01)
        Subsystem: Dell RTS5209 PCI Express Card Reader [1028:0552]
        Kernel driver in use: sdhci-pci
        Kernel modules: sdhci_pci

```

---

### Post by vasa1 on 2017-11-01
> **mrswadge said:**
> ...
I thought it maybe useful to give a hardware summary. It's a Dell laptop, Alienware M14X R2.
...
Another useful tool is *inxi* in the Universe repository. After installing it, run```
inxi -Fxzc0
```and post the output here. The output may help people guide you better.

---

### Post by oldfred on 2017-11-01
Shimx64.efi is the grub version for UEFI Secure boot. Or a shim between Secure boot & grub. Shim should work whether Secure boot is on or not.
But if you have nVidia or any other proprietary driver you cannot use UEFI Secure boot anyway.

My Dell Inspiron-3647 with Haswell i3 just works, but I have 16.04 on it, but it is my one Windows system to use with TV.

Have you updated UEFI to newest version?
If installed you must have AHCI mode on. Many newer Dell systems use RAID setting even if one drive.

Now older threads.
 Ubuntu 15.10 Dual Boot Win 10 Alienware 15 R2 Problem 
[http://ubuntuforums.org/showthread.php?t=2311390&p=13430555#post13430555](http://ubuntuforums.org/showthread.php?t=2311390&p=13430555#post13430555)
[http://ubuntuforums.org/showthread.php?t=2313054](http://ubuntuforums.org/showthread.php?t=2313054)
[http://askubuntu.com/questions/795755/grub-problems-on-dual-boot-windows-10-ubuntu-16-04-laptop-using-samsung-950-pr](http://askubuntu.com/questions/795755/grub-problems-on-dual-boot-windows-10-ubuntu-16-04-laptop-using-samsung-950-pr) 


Dell often has its own developed drivers, but they then are in later editions of Linux and then Linux distributions.
 Dell XPS 13 Developer Edition New Kaby Lake 16.04  Sputnik 
[http://news.softpedia.com/news/dell-launches-its-new-ubuntu-powered-xps-13-developer-edition-laptop-in-us-eu-509039.shtml](http://news.softpedia.com/news/dell-launches-its-new-ubuntu-powered-xps-13-developer-edition-laptop-in-us-eu-509039.shtml)
5th Generation Sputnik
[https://bartongeorge.io/2016/03/10/xps-13-developer-edition-launches-in-us-ubuntu-based-workstations-available-worldwide/](https://bartongeorge.io/2016/03/10/xps-13-developer-edition-launches-in-us-ubuntu-based-workstations-available-worldwide/)

---

### Post by mrswadge on 2017-11-01
> **vasa1 said:**
> Another useful tool is *inxi* in the Universe repository...

Thanks for the suggestions, here is the summary.

```

user@computer:~# inxi -Fxzc0
System:    Host: orc Kernel: 4.13.0-16-generic x86_64 bits: 64 gcc: 7.2.0 Console: tty 0 Distro: Ubuntu 17.10
Machine:   Device: portable System: Alienware product: M14xR2 v: A14 serial: <filter>
           Mobo: Alienware model: M14xR2 v: A14 serial: <filter> UEFI: Alienware v: A14 date: 09/13/2013
Battery    BAT1: charge: 49.0 Wh 100.0% condition: 49.0/64.5 Wh (76%) model: SDI PABAS0241231 status: Full
CPU:       Quad core Intel Core i7-3630QM (-HT-MCP-) arch: Ivy Bridge rev.9 cache: 6144 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 19156
           clock speeds: max: 3400 MHz 1: 2394 MHz 2: 2394 MHz 3: 2394 MHz 4: 2394 MHz 5: 2394 MHz 6: 2394 MHz
           7: 2394 MHz 8: 2394 MHz
Graphics:  Card-1: Intel 3rd Gen Core processor Graphics Controller bus-ID: 00:02.0
           Card-2: NVIDIA GK107M [GeForce GT 650M] bus-ID: 01:00.0
           Display Server: X.org 1.19.5 drivers: (unloaded: fbdev,vesa) FAILED: modesetting,nouveau
           tty size: 237x66 Advanced Data: N/A for root out of X
Audio:     Card-1 NVIDIA GK107 HDMI Audio Controller driver: snd_hda_intel bus-ID: 01:00.1
           Card-2 Intel 7 Series/C216 Family High Definition Audio Controller
           driver: snd_hda_intel bus-ID: 00:1b.0
           Sound: Advanced Linux Sound Architecture v: k4.13.0-16-generic
Network:   Card-1: Qualcomm Atheros AR8151 v2.0 Gigabit Ethernet
           driver: atl1c v: 1.0.1.1-NAPI port: 2000 bus-ID: 07:00.0
           IF: enp7s0 state: down mac: <filter>
           Card-2: Qualcomm Atheros AR9462 Wireless Network Adapter driver: ath9k bus-ID: 08:00.0
           IF: wlp8s0 state: up mac: <filter>
Drives:    HDD Total Size: 756.2GB (5.4% used)
           ID-1: /dev/sda model: WDC_WD5000BPKT size: 500.1GB temp: 34C
           ID-2: /dev/sdb model: M4 size: 256.1GB temp: 0C
Partition: ID-1: / size: 63G used: 33G (55%) fs: ext4 dev: /dev/sdb6
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 29.8C mobo: 27.8C gpu: 38.0
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 214 Uptime: 6:17 Memory: 1141.5/11891.5MB Init: systemd runlevel: 5 Gcc sys: 7.2.0
           Client: Shell (bash 4.4.121) inxi: 2.3.37

```

I also ran a command to see the reboot times, I noticed that it doesn't appear to be fully shutdown.

```

user@computer:~# last -x | grep reboot
reboot   system boot  4.13.0-16-generi Wed Nov  1 07:36   still running
reboot   system boot  4.13.0-16-generi Wed Nov  1 00:15   still running
reboot   system boot  4.13.0-16-generi Tue Oct 31 23:28   still running
reboot   system boot  4.13.0-16-generi Tue Oct 31 23:21   still running
reboot   system boot  4.10.0-38-generi Tue Oct 31 21:43 - 22:46  (01:03)
reboot   system boot  4.10.0-37-generi Tue Oct 31 20:41 - 21:42  (01:01)

```

The upgrade to ubuntu would have been done during the 1 hr 3 min session. Since then it seems to not have shutdown, is it suspending instead?

Would a grep matching ACPI from /var/log/kern.log* based around these periods be useful?

Thanks,
Stuart

---

### Post by oldfred on 2017-11-01
Have you reinstalled the nVidia driver from Ubuntu repository?

---

### Post by mrswadge on 2017-11-01
Thanks for the input oldfred.

> **oldfred said:**
> But if you have nVidia or any other proprietary driver you cannot use UEFI Secure boot anyway.

According to bootctl secure boot is disabled.

> **oldfred said:**
> Have you updated UEFI to newest version?

I have A14 BIOS installed, which is the latest and likely the last update from Dell.

> **oldfred said:**
> If installed you must have AHCI mode on. Many newer Dell systems use RAID setting even if one drive.

Based on the below, I believe AHCI is enabled.

```

user@computer:~# dmesg | grep -i ahci
[    2.094576] ahci 0000:00:1f.2: version 3.0
[    2.104821] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 6 Gbps 0x7 impl RAID mode
[    2.104823] ahci 0000:00:1f.2: flags: 64bit ncq pm led clo pio slum part ems apst
[    2.128627] scsi host0: ahci
[    2.128790] scsi host1: ahci
[    2.128994] scsi host2: ahci
[    2.129207] scsi host3: ahci
[    2.129343] scsi host4: ahci
[    2.129516] scsi host5: ahci

```

> **oldfred said:**
> Have you reinstalled the nVidia driver from Ubuntu repository?

No, I will try this. Is this a good method? I've not done this before (sorry!).
[http://www.linuxandubuntu.com/home/how-to-install-latest-nvidia-drivers-in-linux](http://www.linuxandubuntu.com/home/how-to-install-latest-nvidia-drivers-in-linux)

---

### Post by oldfred on 2017-11-01
Only if you have the very newest nVidia card, or are installing an older Ubuntu like 14.04 may the versions in the standard repository not be new enough.
You can normally just install from System Settings.
But if you want the very newest driver then you add ppa and newest it has. Link mentions one specific driver that was newest then.

       Updated driver search by nVidia model, do not download, just check correct driver version
[URL="http://www.geforce.com/drivers"]http://www.geforce.com/drivers
[/URL]
 # Shows standard repository versions, which is the same as
System Settings, Software & Updates icon, Additional drivers tab
ubuntu-drivers devices 


Info on ppa

 [https://askubuntu.com/questions/61396/how-do-i-install-the-nvidia-drivers](https://askubuntu.com/questions/61396/how-do-i-install-the-nvidia-drivers)
Instructions are newest driver for newest cards, must load legacy driver if old nVidia card.
[http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action](http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action)
Details on why and future incorporation to Ubuntu installer
[https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html](https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html)
[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)
sudo apt-add-repository ppa:graphics-drivers/ppa 

      
 If you have installed any version, you must purge first, old will conflict with new as new install does not overwrite old version.
sudo apt-get remove --purge nvidia-*
sudo apt-get purge nvidia* bumblebee primus bbswitch-dkms
This xorg file may not exist, so if error that would be ok
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup


 sudo ubuntu-drivers devices
If you just want default version - recommended one
sudo ubuntu-drivers autoinstall
Or you manually choose any in list.
sudo apt-get install nvidia-XXX  


 

    [URL="http://www.geforce.com/drivers"]
[/URL]

---

### Post by mrswadge on 2017-11-01
> **oldfred said:**
> 
 If you have installed any version, you must purge first, old will conflict with new as new install does not overwrite old version.
sudo apt-get remove --purge nvidia-*
sudo apt-get purge nvidia* bumblebee primus bbswitch-dkms
This xorg file may not exist, so if error that would be ok
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup


 sudo ubuntu-drivers devices
If you just want default version - recommended one
sudo ubuntu-drivers autoinstall


Thank you ever so much for your valuable input on these issues oldfred, it seems the graphics driver was the issue. I'm a little shocked as a windows user migrating to Ubuntu as I would have though a minor release upgrade of Ubuntu (17.04 to 17.10) would not require an re-install of a graphics driver and if it did, it ought to be automatically handled, surely? Is this normal when upgrading a linux distribution? Are upgrades between 17.04 to 17.10 considered major releases?

---

### Post by oldfred on 2017-11-02
Do not know latest info, but the rule has been to always un-install all proprietary drivers before upgrade and then reinstall after.
The proprietary drivers are integrated into the kernel, so with new kernel it has to know you have proprietary driver, but new install may not know that?

I always do new clean install as it avoids upgrade issues. Also then I test that my backups do let me restore to fully working system.
But I cheat and keep old install, so I can go back. I use 25GB for / (root) partition and have many of those for various installs. And I link data from one large data partition into my installs so same data is available everywhere.

---

### Post by markackerman8@gmail.com on 2017-11-08
I had very similar problems and re-installing did not help ...

Purging Nvidia*
> sudo apt-get purge nvidia*    and reinstalling the nvidia driver WORKED!

and on an aside.
Grub not appearing WOW ! Ubuntu now needs one to hold Shift Key while booting.
.. Great Idea but what a red herring for my troubleshooting.

Trying to help, Mark ;)

---

