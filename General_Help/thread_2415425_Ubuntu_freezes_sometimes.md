---
title: "Ubuntu freezes sometimes"
date: 2019-03-25
forum: General Help
---

### Post by gipsyshadow on 2019-03-25
I'm experiencing some freezes during ubuntu 18.04.2lts sessions and I'd like to understand the reason(s).

This is my cfg both HW and SW:
- amd ryzen 2200g with Vega 8 integrated graphics;
- msi b450-a pro with latest bios release (7B86vA7 2019-03-07) ;
- 2x4gb hyperx predator @3200 cl16 (I let them work @2400 by default);
- no dedicated graph card;
- 4.18.0-16 ubuntu kernel;
- mesa drivers upgraded to 18.3.3 release;
- dual boot with windows 10 enterprise

And the following is my inxi -Fz for deeper details:
```

~$ inxi -Fz
System:    Host: master Kernel: 4.18.0-16-generic x86_64 bits: 64
           Desktop: Gnome 3.28.3 Distro: Ubuntu 18.04.2 LTS
Machine:   Device: desktop Mobo: Micro-Star model: B450-A PRO (MS-7B86) v: 2.0 serial: N/A
           UEFI: American Megatrends v: A.70 date: 03/06/2019
CPU:       Quad core AMD Ryzen 3 2200G with Radeon Vega Graphics (-MCP-) 
           cache: 2048 KB
           clock speeds: max: 3500 MHz 1: 1452 MHz 2: 1419 MHz 3: 1572 MHz
           4: 1433 MHz
Graphics:  Card: Advanced Micro Devices [AMD/ATI] Raven Ridge [Radeon Vega Series / Radeon Vega Mobile Series]
           Display Server: x11 (X.Org 1.20.1 ) driver: amdgpu
           Resolution: 1440x900@74.98hz
           OpenGL: renderer: AMD RAVEN (DRM 3.26.0, 4.18.0-16-generic, LLVM 7.0.0)
           version: 4.5 Mesa 18.3.3
Audio:     Card-1 Advanced Micro Devices [AMD] Device 15e3
           driver: snd_hda_intel
           Card-2 Advanced Micro Devices [AMD/ATI] Device 15de
           driver: snd_hda_intel
           Sound: Advanced Linux Sound Architecture v: k4.18.0-16-generic
Network:   Card: Realtek RTL8111/8168/8411 PCIE Gigabit Ethernet Controller
           driver: r8169
           IF: enp24s0 state: down mac: <filter>
Drives:    HDD Total Size: 1000.2GB (7.7% used)
           ID-1: /dev/sda model: WDC_WD1003FZEX size: 1000.2GB
Partition: ID-1: / size: 48G used: 7.2G (16%) fs: ext4 dev: /dev/sda3
           ID-2: /home size: 9.6G used: 854M (10%) fs: ext4 dev: /dev/sda5
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: No active sensors found. Have you configured your sensors yet? mobo: N/A gpu: 23.0
Info:      Processes: 253 Uptime: 2:01 Memory: 1620.5/5968.5MB
           Client: Shell (bash) inxi: 2.3.56 

```

Freezes happened oftenly with the stock bios and 18.04.1lts but not now so I guess these 2 things are linked. I open Firefox during every ubuntu session and most of freezes occurs during FF browsing, only once a freeze occurred during a text editing within kate and FF was opened in background. I didn't know it wasn't a good idea to install kate in ubuntu because it's KDE's anyway I reinstalled ubuntu and nothing of kate is present. Due to that kate's freeze I guess the reason of these freezes doesn't rely (completely) on FF.
Afaik when ubuntu freezes I've to type alt+printscreen+risub and the system restarts properly. I do it every time therefore I guess it means the kernel is ok.

My questions are (basically) 2:
How to understand the reasons of these freezes?
What can I do apart waiting for new bios releases and ubuntu upgrades?

---

### Post by CatKiller on 2019-03-25
Your freezes don't have anything to do with using Kate or Firefox. It's simply a new platform, which came out after 18.04 was released. Development is progressing rapidly, on both the drivers and the Mesa stack. There are PPAs that will give you access to the newest versions, which might help.

---

### Post by gipsyshadow on 2019-03-25
I see. So what's the best thing I can do if any? You talked about "newest versions", did you mean it's better for me to use the latest ubuntu 18.10 instead of my current LTS?

---

### Post by CatKiller on 2019-03-25
I use Nvidia graphics, so everything that I know about AMD graphics I've just picked up through osmosis.

The AMD drivers and the Mesa stack are both open source and have a lot of people invested in their future together. They are currently under rapid development. I frequently hear about improvements or fixes to one or the other, or the pairing. Unfortunately, that means that if you want to benefit from those improvements you need to be on the later versions.

Whether it's better practically to be on the interim upgrade treadmill with 18.10 and then 19.04 and so on, or to use the LTS and PPAs that backport the newer versions, I couldn't say: I don't have experience of either. One may well turn out to be better than the other, but I couldn't say which.

---

### Post by gipsyshadow on 2019-03-29
Another freeze occurred. I saw I just have to wait and upgrade my sw but I'd like to ask if it's possibile to understand the cause so maybe it could be possible to get this situation better, I mean less freezes.
After ubuntu frozen I rebooted in recovery mode and start the shell then I gave
```

journalctl -p 3

```
I went at the end, I mean closer to reboot point and I saw these errors:
```

[...] kernel: amdgpu 0000:38:00.0: [gfxhub] VMC page fault (src_id:0 ring:56 vmid:1 pasid:32769)
[...] kernel: amdgpu 0000:38:00.0:   at page 0x0000000104a05000 from 27
[...] kernel: amdgpu 0000:38:00.0: VM_L2_PROTECTION_FAULT_STATUS:0x001C00071

```
this 3 lined scheme above repeated several times changing only addresses (0x....) but the beginning "amdgpu 0000:38:00.0" remained the same.
```

[...] kernel: [drm:amdgpu_job_timeout [amdgpu]] *ERROR* ring gfx timeout, last signaled seq=123572, last emitted seq=123575
[...] kernel: INFO: task kworker/u64:0:3582 blocked for more than 120 seconds.
[...] kernel:       Not tainted 4.18.0-16-generic #17~18.04.1-Ubuntu
[...] kernel: "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
-- Reboot --

```

I tried to search a bit and found [this [solved] thread](https://bbs.archlinux.org/viewtopic.php?id=244285). It's arab for me but I guess it could be usefull, anyway I post my "vainfo" and "dmesg | grep amdgpu" outputs:
```
~$ vainfo
libva info: VA-API version 1.1.0
libva info: va_getDriverName() returns 0
libva info: Trying to open /usr/lib/x86_64-linux-gnu/dri/radeonsi_drv_video.so
libva info: Found init function __vaDriverInit_1_1
libva info: va_openDriver() returns 0
vainfo: VA-API version: 1.1 (libva 2.1.0)
vainfo: Driver version: Mesa Gallium driver 18.3.3 for AMD RAVEN (DRM 3.26.0, 4.18.0-16-generic, LLVM 7.0.0)
vainfo: Supported profile and entrypoints
      VAProfileMPEG2Simple            :    VAEntrypointVLD
      VAProfileMPEG2Main              :    VAEntrypointVLD
      VAProfileVC1Simple              :    VAEntrypointVLD
      VAProfileVC1Main                :    VAEntrypointVLD
      VAProfileVC1Advanced            :    VAEntrypointVLD
      VAProfileH264ConstrainedBaseline:    VAEntrypointVLD
      VAProfileH264ConstrainedBaseline:    VAEntrypointEncSlice
      VAProfileH264Main               :    VAEntrypointVLD
      VAProfileH264Main               :    VAEntrypointEncSlice
      VAProfileH264High               :    VAEntrypointVLD
      VAProfileH264High               :    VAEntrypointEncSlice
      VAProfileHEVCMain               :    VAEntrypointVLD
      VAProfileHEVCMain               :    VAEntrypointEncSlice
      VAProfileHEVCMain10             :    VAEntrypointVLD
      VAProfileJPEGBaseline           :    VAEntrypointVLD
      VAProfileVP9Profile0            :    VAEntrypointVLD
      VAProfileVP9Profile2            :    VAEntrypointVLD
      VAProfileNone                   :    VAEntrypointVideoProc

```
```

~$ dmesg | grep amdgpu
[   11.812834] [drm] amdgpu kernel modesetting enabled.
[   11.818914] fb: switching to amdgpudrmfb from EFI VGA
[   11.866252] amdgpu 0000:38:00.0: VRAM: 2048M 0x000000F400000000 - 0x000000F47FFFFFFF (2048M used)
[   11.866253] amdgpu 0000:38:00.0: GTT: 1024M 0x000000F500000000 - 0x000000F53FFFFFFF
[   11.866384] [drm] amdgpu: 2048M of VRAM memory ready
[   11.866385] [drm] amdgpu: 3072M of GTT memory ready.
[   12.144775] amdgpu: [powerplay] dpm has been enabled
[   12.241342] fbcon: amdgpudrmfb (fb0) is primary device
[   12.241436] amdgpu 0000:38:00.0: fb0: amdgpudrmfb frame buffer device
[   12.260160] amdgpu 0000:38:00.0: ring 0(gfx) uses VM inv eng 4 on hub 0
[   12.260164] amdgpu 0000:38:00.0: ring 1(comp_1.0.0) uses VM inv eng 5 on hub 0
[   12.260166] amdgpu 0000:38:00.0: ring 2(comp_1.1.0) uses VM inv eng 6 on hub 0
[   12.260169] amdgpu 0000:38:00.0: ring 3(comp_1.2.0) uses VM inv eng 7 on hub 0
[   12.260171] amdgpu 0000:38:00.0: ring 4(comp_1.3.0) uses VM inv eng 8 on hub 0
[   12.260173] amdgpu 0000:38:00.0: ring 5(comp_1.0.1) uses VM inv eng 9 on hub 0
[   12.260176] amdgpu 0000:38:00.0: ring 6(comp_1.1.1) uses VM inv eng 10 on hub 0
[   12.260179] amdgpu 0000:38:00.0: ring 7(comp_1.2.1) uses VM inv eng 11 on hub 0
[   12.260181] amdgpu 0000:38:00.0: ring 8(comp_1.3.1) uses VM inv eng 12 on hub 0
[   12.260184] amdgpu 0000:38:00.0: ring 9(kiq_2.1.0) uses VM inv eng 13 on hub 0
[   12.260186] amdgpu 0000:38:00.0: ring 10(sdma0) uses VM inv eng 4 on hub 1
[   12.260189] amdgpu 0000:38:00.0: ring 11(vcn_dec) uses VM inv eng 5 on hub 1
[   12.260192] amdgpu 0000:38:00.0: ring 12(vcn_enc0) uses VM inv eng 6 on hub 1
[   12.260194] amdgpu 0000:38:00.0: ring 13(vcn_enc1) uses VM inv eng 7 on hub 1
[   12.264414] [drm] Initialized amdgpu 3.26.0 20150101 for 0000:38:00.0 on minor 0

```

Do you think it worths to do "something" about my errors right now or just wait ubuntu "big heads" solve all these issues?

---

### Post by CatKiller on 2019-03-29
> **gipsyshadow said:**
> Do you think it worths to do "something" about my errors right now or just wait ubuntu "big heads" solve all these issues?
If the issue is that you really need newer versions of the kernel and Mesa (and I'll remind you that I haven't used an AMD GPU) then waiting won't fix anything on its own. Each release of Ubuntu only generally gets security fixes rather than new versions of software with new features.

You could run 18.10 or the soon-to-be-released 19.04 from a live USB for a while to see if the newer versions fix your issue, or if it's something else. If they do stop the freezes you could install one of those, or use PPAs to get the same versions on 18.04.

---

### Post by gipsyshadow on 2019-03-30
Consider those above errors occurred when running latest mesa drivers (18.3.3).
Now what about kernels? I'm running 4.18.0-16 which I think it's the latest stable for my 18.04.2lts. When using 18.04.1lts I tried other kernels like 4.20.11-042011 installed via UKUU and I got freezes as well. Considering this experience do you think it can be usefull or useless to try the 18.10 or 19.04 with newer kernels anyhow?

Let's say the reason(s) of my freezes is caused only by my MB's bios. Is there anything I could do working just on ubuntu?

Maybe my questions are a bit silly but I'm a very newbie. Thanks for help anyway :)

---

### Post by CatKiller on 2019-03-30
> **gipsyshadow said:**
> Considering this experience do you think it can be usefull or useless to try the 18.10 or 19.04 with newer kernels anyhow?

It takes some small number of minutes to download the images, write them to a USB stick and reboot. 19.04 is going to come with version 19.0 of Mesa and version 5.0 of Linux. I know that there's been a lot of work on both of those for AMD graphics, so it might help. Or it might not. Either way, you've expended minimal effort to learn something useful.

> Let's say the reason(s) of my freezes is caused only by my MB's bios. Is there anything I could do working just on ubuntu?

Not really. If the freezes are caused entirely by the BIOS, you'd need the BIOS to stop causing the freezes before they'd stop. The motherboard manufacturers did seem to have been surprised by the requirement for high-quality BIOS software with the Ryzens: they had to scramble to get new versions of their BIOSes out because of crashes and freezes and the like. There may be a future version of your BIOS that stops the freezes. There may also be some settings in your BIOS that you could change to mitigate whatever aspect is triggering the issue.

However, BIOS implementations have always been a bit rubbish, so working around the quirks of particular ones is something that happens. It is possible that there will be a specific workaround that's identified at some point and implemented in software.

---

