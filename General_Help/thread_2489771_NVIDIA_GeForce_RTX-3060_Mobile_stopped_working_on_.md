---
title: "NVIDIA GeForce RTX-3060 Mobile stopped working on Ubuntu 22.04; Nvidia drivers not de"
date: 2023-08-10
forum: General Help
---

### Post by sitethief on 2023-08-10
System Specifications:



[LIST]
[*]Laptop: [Clevo NP50PNH]("https://laptopwithlinux.com/product/clevo-np50pnh-np50pnk-np50pnp/")
[*]Ubuntu Version: 22.04
[*]Kernel: 6.2.0-26-generic
[*]Display server: Wayland
[*]Graphics card: NVIDIA GeForce RTX-3060 – 6 GB DDR6 Video Memory – DirectX 12.1 – 115W TDP
[/LIST]


About a day ago my NVIDIA GeForce RTX-3060 card in my work laptop stopped working. This resulted in no longer being able to use the HDMI port, The USB-C Thunderbolt was still available though.
I found out the laptop switched back to the onboard Intel iRISxe graphics. When I try to see if there are any additional drivers it tells me that there a not additional drivers available, where previously I had a host of choices. Previously I was using the nouveau driver for a month or so since the proprietary Nvidia drivers where giving me a number of problems. And since this is a work laptop used for programming I don't need very much fancy graphics, just be able to use the HDMI.


My apt is up to date atm. The Bios of this laptop is very very limited so I'm not sure of going there would help at all so I haven't tried that yet. 


I tried

[LIST]
[*]apt-update & apt-upgrade
[*]Checked for additional drivers.
[*]tried to switch Nvidia using prime-select.
[*]Reboot
[/LIST]


Relevant output of `lspci`
```

00:00.0 Host bridge: Intel Corporation 12th Gen Core Processor Host Bridge/DRAM Registers (rev 02)
00:01.0 PCI bridge: Intel Corporation 12th Gen Core Processor PCI Express x16 Controller #1 (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Alder Lake-P Integrated Graphics Controller (rev 0c)
00:04.0 Signal processing controller: Intel Corporation Alder Lake Innovation Platform Framework Processor Participant (rev 02)
00:06.0 PCI bridge: Intel Corporation 12th Gen Core Processor PCI Express x4 Controller #0 (rev 02)
00:07.0 PCI bridge: Intel Corporation Alder Lake-P Thunderbolt 4 PCI Express Root Port #0 (rev 02)
00:08.0 System peripheral: Intel Corporation 12th Gen Core Processor Gaussian & Neural Accelerator (rev 02)
00:0a.0 Signal processing controller: Intel Corporation Platform Monitoring Technology (rev 01)
00:0d.0 USB controller: Intel Corporation Alder Lake-P Thunderbolt 4 USB Controller (rev 02)
00:0d.2 USB controller: Intel Corporation Alder Lake-P Thunderbolt 4 NHI #0 (rev 02)
00:14.0 USB controller: Intel Corporation Alder Lake PCH USB 3.2 xHCI Host Controller (rev 01)
00:14.2 RAM memory: Intel Corporation Alder Lake PCH Shared SRAM (rev 01)
00:14.3 Network controller: Intel Corporation Alder Lake-P PCH CNVi WiFi (rev 01)
00:15.0 Serial bus controller: Intel Corporation Alder Lake PCH Serial IO I2C Controller #0 (rev 01)
00:15.1 Serial bus controller: Intel Corporation Alder Lake PCH Serial IO I2C Controller #1 (rev 01)
00:16.0 Communication controller: Intel Corporation Alder Lake PCH HECI Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation Device 51bd (rev 01)
00:1f.0 ISA bridge: Intel Corporation Alder Lake PCH eSPI Controller (rev 01)
00:1f.3 Audio device: Intel Corporation Alder Lake PCH-P High Definition Audio Controller (rev 01)
00:1f.4 SMBus: Intel Corporation Alder Lake PCH-P SMBus Host Controller (rev 01)
00:1f.5 Serial bus controller: Intel Corporation Alder Lake-P PCH SPI Controller (rev 01)
00:1f.6 Ethernet controller: Intel Corporation Ethernet Connection (16) I219-V (rev 01)
01:00.0 VGA compatible controller: NVIDIA Corporation GA106M [GeForce RTX 3060 Mobile / Max-Q] (rev a1)
01:00.1 Audio device: NVIDIA Corporation GA106 High Definition Audio Controller (rev a1)
02:00.0 Non-Volatile memory controller: Samsung Electronics Co Ltd NVMe SSD Controller PM9A1/PM9A3/980PRO
2c:00.0 SD Host controller: O2 Micro, Inc. SD/MMC Card Reader Controller (rev 01)
```



This clearly shows the card is still present


sudo prime-select nvidia gives me this:

```

Info: selecting the nvidia profile
Deleting /lib/modprobe.d/nvidia-runtimepm.conf
Updating the initramfs. Please wait for the operation to complete:
-W: Possible missing firmware /lib/firmware/nvidia/ga107/acr/ucode_ahesasc.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/ga106/acr/ucode_ahesasc.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/ga104/acr/ucode_ahesasc.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/ga103/acr/ucode_ahesasc.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/ga102/acr/ucode_ahesasc.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/ga107/acr/ucode_asb.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/ga106/acr/ucode_asb.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/ga104/acr/ucode_asb.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/ga103/acr/ucode_asb.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/ga102/acr/ucode_asb.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/ga107/acr/ucode_unload.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/ga106/acr/ucode_unload.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/ga104/acr/ucode_unload.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/ga103/acr/ucode_unload.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/ga102/acr/ucode_unload.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/ga107/nvdec/scrubber.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/ga106/nvdec/scrubber.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/ga104/nvdec/scrubber.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/ga103/nvdec/scrubber.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/ga102/nvdec/scrubber.bin for module nouveau
|W: Possible missing firmware /lib/firmware/nvidia/ga107/gr/NET_img.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/ga107/gr/gpccs_sig.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/ga107/gr/gpccs_bl.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/ga107/gr/fecs_sig.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/ga107/gr/fecs_bl.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/ga106/gr/NET_img.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/ga106/gr/gpccs_sig.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/ga106/gr/gpccs_bl.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/ga106/gr/fecs_sig.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/ga106/gr/fecs_bl.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/ga104/gr/NET_img.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/ga104/gr/gpccs_sig.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/ga104/gr/gpccs_bl.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/ga104/gr/fecs_sig.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/ga104/gr/fecs_bl.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/ga103/gr/NET_img.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/ga103/gr/gpccs_sig.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/ga103/gr/gpccs_bl.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/ga103/gr/fecs_sig.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/ga103/gr/fecs_bl.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/ga102/gr/NET_img.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/ga102/gr/gpccs_sig.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/ga102/gr/gpccs_bl.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/ga102/gr/fecs_sig.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/ga102/gr/fecs_bl.bin for module nouveau
\W: Possible missing firmware /lib/firmware/nvidia/ga107/sec2/hs_bl_sig.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/ga107/sec2/sig.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/ga107/sec2/image.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/ga107/sec2/desc.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/ga106/sec2/hs_bl_sig.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/ga106/sec2/sig.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/ga106/sec2/image.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/ga106/sec2/desc.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/ga104/sec2/hs_bl_sig.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/ga104/sec2/sig.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/ga104/sec2/image.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/ga104/sec2/desc.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/ga103/sec2/hs_bl_sig.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/ga103/sec2/sig.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/ga103/sec2/image.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/ga103/sec2/desc.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/ga102/sec2/hs_bl_sig.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/ga102/sec2/sig.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/ga102/sec2/image.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/ga102/sec2/desc.bin for module nouveau
W: Possible missing firmware /lib/firmware/i915/dg2_huc_gsc.bin for module i915
Done

```


But rebooting after sudo prime-select nvidia does nothing. 
Btw, reboot/power off seems to get stuck when powering down, even when I wait a couple of minutesm and I need to do a 5 second button press to actually shut the system down atm.  Not sure if this is related or not.


Output of journalctl -b -1 -r  is
```

 aug 09 09:12:46 michel-linux-laptop systemd-journald[914]: Journal stopped
aug 09 09:12:46 michel-linux-laptop systemd-shutdown[1]: Sending SIGTERM to remaining processes...
aug 09 09:12:46 michel-linux-laptop systemd-shutdown[1]: Syncing filesystems and block devices.
aug 09 09:12:46 michel-linux-laptop systemd[1]: Shutting down.
aug 09 09:12:46 michel-linux-laptop systemd[1]: Reached target System Power Off.
aug 09 09:12:46 michel-linux-laptop systemd[1]: Finished System Power Off.
aug 09 09:12:46 michel-linux-laptop systemd[1]: systemd-poweroff.service: Deactivated successfully.
aug 09 09:12:46 michel-linux-laptop systemd[1]: Reached target Late Shutdown Services.
aug 09 09:12:46 michel-linux-laptop systemd[1]: Reached target System Shutdown.
aug 09 09:12:46 michel-linux-laptop systemd[1]: Stopped Monitoring of LVM2 mirrors, snapshots etc. using dmeventd or progress polling.
aug 09 09:12:46 michel-linux-laptop systemd[1]: lvm2-monitor.service: Deactivated successfully.
aug 09 09:12:46 michel-linux-laptop lvm[78362]:   2 logical volume(s) in volume group "vgubuntu" unmonitored
aug 09 09:12:46 michel-linux-laptop systemd[1]: Stopped Remount Root and Kernel File Systems.
aug 09 09:12:46 michel-linux-laptop systemd[1]: systemd-remount-fs.service: Deactivated successfully.
aug 09 09:12:46 michel-linux-laptop systemd[1]: Stopped Create System Users.
aug 09 09:12:46 michel-linux-laptop systemd[1]: systemd-sysusers.service: Deactivated successfully.
aug 09 09:12:46 michel-linux-laptop systemd[1]: Stopped Create Static Device Nodes in /dev.
aug 09 09:12:46 michel-linux-laptop systemd[1]: systemd-tmpfiles-setup-dev.service: Deactivated successfully.
aug 09 09:12:46 michel-linux-laptop systemd[1]: Stopping Monitoring of LVM2 mirrors, snapshots etc. using dmeventd or progress polling.>
aug 09 09:12:46 michel-linux-laptop systemd[1]: Stopped target Preparation for Local File Systems.
aug 09 09:12:46 michel-linux-laptop systemd[1]: Removed slice Slice /system/systemd-fsck.
aug 09 09:12:46 michel-linux-laptop systemd[1]: Stopped File System Check on /dev/disk/by-uuid/e1bce27a-a986-49e3-bb2c-a3e736585fe4.
aug 09 09:12:46 michel-linux-laptop systemd[1]: [EMAIL="systemd-fsck@dev-disk-by\x2duuid-e1bce27a\x2da986\x2d49e3\x2dbb2c\x2da3e736585fe4.servi"]systemd-fsck@dev-disk-by\x2duuid-e1bce27a\x2da986\x2d49e3\x2dbb2c\x2da3e736585fe4.servi[/EMAIL]>
aug 09 09:12:46 michel-linux-laptop systemd[1]: Reached target Unmount All Filesystems.
aug 09 09:12:46 michel-linux-laptop systemd[1]: Unmounted /boot.
aug 09 09:12:46 michel-linux-laptop systemd[1]: boot.mount: Deactivated successfully.
aug 09 09:12:46 michel-linux-laptop systemd[1]: Deactivated swap /dev/mapper/vgubuntu-swap_1.
aug 09 09:12:46 michel-linux-laptop systemd[1]: dev-mapper-vgubuntu\x2dswap_1.swap: Deactivated successfully.
aug 09 09:12:46 michel-linux-laptop systemd[1]: Deactivated swap /dev/dm-2.
aug 09 09:12:46 michel-linux-laptop systemd[1]: dev-dm\x2d2.swap: Deactivated successfully.
aug 09 09:12:46 michel-linux-laptop systemd[1]: Deactivated swap /dev/disk/by-id/dm-uuid-LVM-OvXIAKj2mAprMp7xlc862ptZi0ZX9D3Lumy4AVs3ty>

```

Conclusion: I'm trying to restore the functionality of my Nvidia card and HDMI. Any help or pointers would be greatly appreciated.

---

### Post by Autodave on 2023-08-10
What nVidia driver are you using now?  I would be using the 525 driver, not nouveau or the 535 driver.

---

### Post by sitethief on 2023-08-10
> **Autodave said:**
> What nVidia driver are you using now?  I would be using the 525 driver, not nouveau or the 535 driver.

I am not using any NVIDIA drivers, or rather I don't know what driver I am using atm, since there are at the moment none available to me. That is the whole problem atm.
I was using the noveau driver, since that one gave me less trouble when switching from home office to office screens out of suspend.
But the whole problem is that I have the feeling that the laptop switched to the onboard Intel Iris Xe Graphics earlier this week.
This prevents me from using the HDMI port, and limits my external screen options to Thunderbolt.

This is how my drivers selection looks like right now
[IMG]https://i.ibb.co/SrnBCYv/Unsaved-Image-1.jpg[/IMG]


the "ubuntu-drivers devices" command gives no output at all

"prime-select query" give me the output of "nvidia", but I would expect to be able to select a NVIDIA driver and use my HDMI port if that was the case

lshw -numeric -C display gives 
```

*-display                 
       description: VGA compatible controller
       product: GA106M [GeForce RTX 3060 Mobile / Max-Q] [10DE:2520]
       vendor: NVIDIA Corporation [10DE]
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: /dev/fb0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom fb
       configuration: depth=32 driver=nouveau latency=0 mode=1920x1080 visual=truecolor xres=1920 yres=1080
       resources: iomemory:600-5ff iomemory:620-61f irq:167 memory:83000000-83ffffff memory:6000000000-61ffffffff memory:6200000000-6201ffffff ioport:3000(size=128) memory:84080000-840fffff
  *-display
       description: VGA compatible controller
       product: Alder Lake-P Integrated Graphics Controller [8086:4626]
       vendor: Intel Corporation [8086]
       physical id: 2
       bus info: pci@0000:00:02.0
       logical name: /dev/fb0
       version: 0c
       width: 64 bits
       clock: 33MHz
       capabilities: pciexpress msi pm vga_controller bus_master cap_list rom fb
       configuration: depth=32 driver=i915 latency=0 resolution=1920,1080
       resources: iomemory:620-61f iomemory:400-3ff irq:168 memory:6202000000-6202ffffff memory:4000000000-400fffffff ioport:4000(size=64) memory:c0000-dffff memory:4010000000-4016ffffff memory:4020000000-40ffffffff


```


sudo lspci -vnn | grep VGA gives
```

00:02.0 VGA compatible controller [0300]: Intel Corporation Alder Lake-P Integrated Graphics Controller [8086:4626] (rev 0c) (prog-if 00 [VGA controller])
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GA106M [GeForce RTX 3060 Mobile / Max-Q] [10de:2520] (rev a1) (prog-if 00 [VGA controller])
```

---

### Post by #&amp;thj^% on 2023-08-10
What shows with:
```
apt policy nvidia-driver-470 nvidia-dkms-470 
```

---

### Post by sitethief on 2023-08-11
> **1fallen said:**
> What shows with:
```
apt policy nvidia-driver-470 nvidia-dkms-470 
```


```
nvidia-driver-470:
  Installed: (none)
  Candidate: 470.199.02-0ubuntu0.22.04.1
  Version table:
     470.199.02-0ubuntu0.22.04.1 500
        500 http://nl.archive.ubuntu.com/ubuntu jammy-updates/restricted amd64 Packages
        500 http://security.ubuntu.com/ubuntu jammy-security/restricted amd64 Packages
     470.103.01-0ubuntu2 500
        500 http://nl.archive.ubuntu.com/ubuntu jammy/restricted amd64 Packages
nvidia-dkms-470:
  Installed: (none)
  Candidate: 470.199.02-0ubuntu0.22.04.1
  Version table:
     470.199.02-0ubuntu0.22.04.1 500
        500 http://nl.archive.ubuntu.com/ubuntu jammy-updates/restricted amd64 Packages
        500 http://security.ubuntu.com/ubuntu jammy-security/restricted amd64 Packages
     470.103.01-0ubuntu2 500
        500 http://nl.archive.ubuntu.com/ubuntu jammy/restricted amd64 Packages


```

---

### Post by ajgreeny on 2023-08-11
Can you boot to a previous 5.19.0-# kernel from grub to see if that helps in any way with this problem.
I am aware that the newer 6 kernel se ries has caused some problems for some hardware; perhaps that is your situation.

---

### Post by sitethief on 2023-08-11
> **ajgreeny said:**
> Can you boot to a previous 5.19.0-# kernel from grub to see if that helps in any way with this problem.
I am aware that the newer 6 kernel se ries has caused some problems for some hardware; perhaps that is your situation.

That does solve it, I went back to 5.19.0-50-generic.
i can now see all my available drivers and HDMI is working again.

---

### Post by prcowley on 2023-08-11
I had somewhat of a similar problem with kernel  6.2.0-26 (and 27)where it lost the Nvidia drivers because and update didn't download the header files that Linux needs to compile the DKMS modules. (known bug not yet fixed)
After a LOT of searching the answer was : sudo apt install linux-headers-6.2.0-26-generic  it downloaded the headers and compiled the DKMS modules and after a reboot it all came right.
Just in the last few hours kernel 6.2.0-27 came down the wire and although it didn't mess with the Nvidia driver, I had to download the headers again to stop the error message every time I tried to do the most minor update.

Hopefully this might help and certainly wont hurt anything

Cheers
Pete

---

### Post by sitethief on 2023-08-11
> **prcowley said:**
> I had somewhat of a similar problem with kernel  6.2.0-26 (and 27)where it lost the Nvidia drivers because and update didn't download the header files that Linux needs to compile the DKMS modules. (known bug not yet fixed)
After a LOT of searching the answer was : sudo apt install linux-headers-6.2.0-26-generic  it downloaded the headers and compiled the DKMS modules and after a reboot it all came right.
Just in the last few hours kernel 6.2.0-27 came down the wire and although it didn't mess with the Nvidia driver, I had to download the headers again to stop the error message every time I tried to do the most minor update.

Hopefully this might help and certainly wont hurt anything

Cheers
Pete

Thanks, sadly I got "linux-headers-6.2.0-26-generic is already the newest version (6.2.0-26.26~22.04.1)."

---

### Post by #&amp;thj^% on 2023-08-11
> **sitethief said:**
> Thanks, sadly I got "linux-headers-6.2.0-26-generic is already the newest version (6.2.0-26.26~22.04.1)."
Can you show me this please:
```
inxi -G | grep API
```

---

### Post by ccerrillo on 2023-08-14
> **1fallen said:**
> Can you show me this please:
```
inxi -G | grep API
```
I have the exact same issue. I also have the 6.2.0-26 headers installed, and the problem is only fixed by booting into the 5.19.x kernel. The command doesn't return anything, the full output is:

```
Graphics:
  Device-1: Intel Alder Lake-P Integrated Graphics driver: i915 v: kernel
  Device-2: NVIDIA GA106M [GeForce RTX 3060 Mobile / Max-Q] driver: nouveau
    v: kernel
  Device-3: Acer HD Webcam type: USB driver: uvcvideo
  Display: wayland server: X.Org v: 1.22.1.1 with: Xwayland v: 22.1.1
    compositor: gnome-shell v: 42.9 driver: gpu: i915
    resolution: 1920x1080~60Hz
  OpenGL: renderer: Mesa Intel Graphics (ADL GT2)
    v: 4.6 Mesa 23.0.4-0ubuntu1~22.04.1

```

---

### Post by MAFoElffen on 2023-08-14
I use nvidia-driver-535, Linux kernel 6.2, with no issues.

I just read an article where the nouveau drivers were broken in Kernels 6.3... And the fix applied to 6.4, backported to 6.3: [https://www.phoronix.com/news/Nouveau-Use-After-Free-Fixed](https://www.phoronix.com/news/Nouveau-Use-After-Free-Fixed)

I do not see the 'ga10X' directory structure under </usr>/lib/firmware/nvidia/ (these come from package linux-firmware)
```

mafoelffen@msi-ubuntu:~$ ls -lah /usr/lib/firmware/nvidia
total 74K
drwxr-xr-x 26 root root  26 Aug  4 23:57 .
drwxr-xr-x 90 root root 454 Aug  5 00:09 ..
drwxr-xr-x  2 root root   4 Aug  4 15:37 535.86.05
drwxr-xr-x  2 root root  10 Aug  5 00:09 gk20a
drwxr-xr-x  4 root root   4 Sep 18  2022 gm200
drwxr-xr-x  4 root root   4 Sep 18  2022 gm204
drwxr-xr-x  4 root root   4 Sep 18  2022 gm206
drwxr-xr-x  5 root root   5 Sep 18  2022 gm20b
drwxr-xr-x  4 root root   4 Sep 18  2022 gp100
drwxr-xr-x  6 root root   6 Sep 18  2022 gp102
drwxr-xr-x  6 root root   6 Sep 18  2022 gp104
drwxr-xr-x  6 root root   6 Sep 18  2022 gp106
drwxr-xr-x  6 root root   6 Sep 18  2022 gp107
drwxr-xr-x  6 root root   6 Sep 18  2022 gp108
drwxr-xr-x  5 root root   5 Sep 18  2022 gp10b
drwxr-xr-x  6 root root   6 Sep 18  2022 gv100
drwxr-xr-x  2 root root   5 Aug  5 00:09 tegra124
drwxr-xr-x  2 root root   5 Aug  5 00:09 tegra186
drwxr-xr-x  2 root root   4 Aug  5 00:09 tegra194
drwxr-xr-x  2 root root   5 Aug  5 00:09 tegra210
drwxr-xr-x  6 root root   6 Sep 18  2022 tu102
drwxr-xr-x  6 root root   6 Sep 18  2022 tu104
drwxr-xr-x  6 root root   6 Sep 18  2022 tu106
drwxr-xr-x  3 root root   3 Sep 18  2022 tu10x
drwxr-xr-x  6 root root   6 Sep 18  2022 tu116
drwxr-xr-x  6 root root   6 Sep 18  2022 tu117
mafoelffen@msi-ubuntu:~$ ls -lah /lib/firmware/nvidia
total 74K
drwxr-xr-x 26 root root  26 Aug  4 23:57 .
drwxr-xr-x 90 root root 454 Aug  5 00:09 ..
drwxr-xr-x  2 root root   4 Aug  4 15:37 535.86.05
drwxr-xr-x  2 root root  10 Aug  5 00:09 gk20a
drwxr-xr-x  4 root root   4 Sep 18  2022 gm200
drwxr-xr-x  4 root root   4 Sep 18  2022 gm204
drwxr-xr-x  4 root root   4 Sep 18  2022 gm206
drwxr-xr-x  5 root root   5 Sep 18  2022 gm20b
drwxr-xr-x  4 root root   4 Sep 18  2022 gp100
drwxr-xr-x  6 root root   6 Sep 18  2022 gp102
drwxr-xr-x  6 root root   6 Sep 18  2022 gp104
drwxr-xr-x  6 root root   6 Sep 18  2022 gp106
drwxr-xr-x  6 root root   6 Sep 18  2022 gp107
drwxr-xr-x  6 root root   6 Sep 18  2022 gp108
drwxr-xr-x  5 root root   5 Sep 18  2022 gp10b
drwxr-xr-x  6 root root   6 Sep 18  2022 gv100
drwxr-xr-x  2 root root   5 Aug  5 00:09 tegra124
drwxr-xr-x  2 root root   5 Aug  5 00:09 tegra186
drwxr-xr-x  2 root root   4 Aug  5 00:09 tegra194
drwxr-xr-x  2 root root   5 Aug  5 00:09 tegra210
drwxr-xr-x  6 root root   6 Sep 18  2022 tu102
drwxr-xr-x  6 root root   6 Sep 18  2022 tu104
drwxr-xr-x  6 root root   6 Sep 18  2022 tu106
drwxr-xr-x  3 root root   3 Sep 18  2022 tu10x
drwxr-xr-x  6 root root   6 Sep 18  2022 tu116
drwxr-xr-x  6 root root   6 Sep 18  2022 tu117

```
But I do see those files elsewhere...
```

mafoelffen@msi-ubuntu:~$ find /lib/firmware -name ucode_ahesasc.bin
/lib/firmware/nvidia/tu104/acr/ucode_ahesasc.bin
/lib/firmware/nvidia/tu117/acr/ucode_ahesasc.bin
/lib/firmware/nvidia/tu102/acr/ucode_ahesasc.bin
/lib/firmware/nvidia/tu116/acr/ucode_ahesasc.bin
/lib/firmware/nvidia/tu106/acr/ucode_ahesasc.bin
mafoelffen@msi-ubuntu:~$ find /lib/firmware -name ucode_asb.bin
/lib/firmware/nvidia/tu104/acr/ucode_asb.bin
/lib/firmware/nvidia/tu117/acr/ucode_asb.bin
/lib/firmware/nvidia/tu102/acr/ucode_asb.bin
/lib/firmware/nvidia/tu116/acr/ucode_asb.bin
/lib/firmware/nvidia/tu106/acr/ucode_asb.bin

```

---

### Post by #&amp;thj^% on 2023-08-15
> **ccerrillo said:**
>  The command doesn't return anything, the full output is:


Interesting return>>Nothing?
```
inxi -G | grep API
  API: OpenGL v: 4.6.0 NVIDIA 535.98 renderer: NVIDIA GeForce GTX 1650

```
I'm now on kernel 6.4 and still no issues, It's hard to fix something we can't find the problem on.
And i too have read the nouveau drivers were broken in Kernels 6.3 just not on my machine....
Any rate good luck to both of you.
Nothing more for me to offer.

---

### Post by MAFoElffen on 2023-08-15
I'm reaching for explainations for answers on the nouveau driver and if it actually supported GTX 3xxxx and GTX4xxx GPU's. We know it was broken for kernels 6.3.0.x. The problem started back in 6.2.0.x.

It had limited support for 3060 and did not support anything above or newer GPU's RTX 3070, 3080 & 3090, nor any in the RTX 4xxx series) for kernel 6.2...

RE: [https://www.phoronix.com/review/linux-62-rtx30/2](https://www.phoronix.com/review/linux-62-rtx30/2)

I know they just backported the nouveau fixes in 6.4 to 6.3... But I find nothing about them backporting anything to 6.2, nor if they have any plans to.

The work-around for this may be to just install 6.4 and manually dl the firmware blob from linux.org to populate /lib/firmware with the latest firmware. Or to just do the later first, with the firmware...
```

wget -N -t 5 -T 10 https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git/snapshot/linux-firmware-20230804.tar.gz

```
I had to do the manual firmware update on my new workstation, as it is 13th Gen iCore, and PCIe Gen 5, for it to work right on the newest firmware for the new Z790 chipsets, and i915.

Since the syslog messages seem to all relate to firmware, that is where I would start. Like I said, there are no directory branches in /lib/firmware/nvidia/ on any of my machines here that match your syslog messages. And all those machines are running Linux kernel 6.2.0-26, and 3 of the 5 are nVidia, but using Ubuntu repo nVidia drivers, not nouveau...

EDIT:
I use the repo nvidia drivers. (Almost Exclusively). I am a "Drivers Tester" for the Edge PPA. The nouveau drivers do not work for my nVidia GPU. They render the wrong colors and make it unreadable. I, honestly have not tried to make them work, as I usually "use" the nvidia-driver-XXX from the repo's. They are usually stable. Now on Windows (they are all dual-boot), I use the newest, latest, game-ready nVidia drivers...

---

### Post by sitethief on 2023-09-06
> **1fallen said:**
> Can you show me this please:
```
inxi -G | grep API
```

That gives me no output at all right now

---

### Post by sitethief on 2023-09-13
[https://askubuntu.com/questions/1481694/nvidia-geforce-rtx-3060-mobile-stopped-working-on-ubuntu-22-04-nvidia-drivers-n](https://askubuntu.com/questions/1481694/nvidia-geforce-rtx-3060-mobile-stopped-working-on-ubuntu-22-04-nvidia-drivers-n)
In there I got my problem solved, granted, could also be one of the many updates I ran since then solved it unknowingly.
Fact is, for me this is now solved on my work laptop. Still has other ongoing issues, but that's besides the point.

---

### Post by MAFoElffen on 2023-09-13
Looked at the solution there.

LOL... Yup. Thought so. (Post early in thread here.)
> **MAFoElffen said:**
> I use nvidia-driver-535, Linux kernel 6.2, with no issues.

But you told us you were apposed to using NVidia's drivers...

---

### Post by sitethief on 2023-09-17
> **MAFoElffen said:**
> Looked at the solution there.

LOL... Yup. Thought so. (Post early in thread here.)

But you told us you were apposed to using NVidia's drivers...

No, I said I had problems with a few of their drivers in their usage, not that I'm against using them per se.

But this problem I had was also that none of those were available to me at all.

---

### Post by luuquanghung on 2023-10-30
I got exactly the same problem with my ASUS RTX3060 and Ubuntu 22.04. The PC failed to restart whenever I tried the Additional Drivers with

+ NVIDIA open kernel 535 server (proprietary, tested)
+ NVIDIA open kernel 525 open (proprietary)
+ NVIDIA 525 (proprietary) 

The only version that works is NVIDA server 535 (proprietary).

---

