---
title: "Trying to understand Linux"
date: 2018-10-11
forum: General Help
---

### Post by meiselstein on 2018-10-11
I really like Ubuntu. To me, I just feel comfortable whenever I use it. However, I continue to have this screen tear and flickering problem at the top of my screen (it happens randomly and is quite annoying). So, I tried Fedora and the screen tear and flicker does not happen. But, I am not really a huge fan of Fedora (couldn’t tell you why....just doesn’t feel as comfortable to me as Ubuntu) and I want to use Ubuntu.

I have tried everything to get rid of the screen tear in Ubuntu. So, I did a little test: I installed Ubuntu, updated everything and installed Ukuu and kernel 4.18.12. Still have the screen tear. I do the same thing with Fedora (update to kernel 4.18.12) and no tearing whatsoever.

To get to my question: what is different about Ubuntu 18.04.1 and Fedora 28 when they are both using GNOME and the same kernel? What is it about Ubuntu that causes this screen tear but Fedora doesn’t? I don’t mean that in a sarcastic way, I’m just genuinely trying to understand how Linux works.

Thanks in advance for any help that you can provide.

---

### Post by Autodave on 2018-10-11
Why it works in one and not the other: I have no idea.  Let's start with some specs on you machine, especially the video card.  Desktop or laptop?  How is mon itor connected: VGA, DVI, etc.  Have you installed a video driver?  If so, what on e and where did you get it from?

---

### Post by deadflowr on 2018-10-11
Post back
```
inxi -F
```
that'll output the basic machine specs.
(Including the graphics card info, which is what most likely is the issue.)

---

### Post by meiselstein on 2018-10-11
Hi AutoDave and Deadflowr, here are the results of my inxi -F:

```
System:    Host: moo Kernel: 4.18.13-041813-generic x86_64 bits: 64
           Desktop: Gnome 3.28.3 Distro: Ubuntu 18.04.1 LTS
Machine:   Device: laptop System: ASUSTeK product: VivoBook 14_ASUS Laptop X407MA_X407MA v: 1.0 serial: N/A
           Mobo: ASUSTeK model: X407MA v: 1.0 serial: N/A
           UEFI: American Megatrends v: X407MA.204 date: 03/07/2018
Battery    BAT0: charge: 24.5 Wh 72.2% condition: 33.9/33.2 Wh (102%)
CPU:       Dual core Intel Celeron N4000 (-MCP-) cache: 4096 KB
           clock speeds: max: 2600 MHz 1: 876 MHz 2: 909 MHz
Graphics:  Card: Intel Device 3185
           Display Server: x11 (X.Org 1.19.6 ) driver: i915
           Resolution: 1366x768@60.00hz
           OpenGL: renderer: Mesa DRI Intel UHD Graphics 600 (Geminilake 2x6)
           version: 4.5 Mesa 18.0.5
Audio:     Card Intel Device 3198 driver: snd_hda_intel
           Sound: ALSA v: k4.18.13-041813-generic
Network:   Card: Realtek RTL8723BE PCIe Wireless Network Adapter
           driver: rtl8723be
           IF: wlo1 state: up mac: 70:c9:4e:2c:66:45
Drives:    HDD Total Size: 120.0GB (6.6% used)
           ID-1: /dev/sda model: KINGSTON_SA400S3 size: 120.0GB
Partition: ID-1: / size: 110G used: 7.4G (8%) fs: ext4 dev: /dev/sda2
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 48.0C mobo: N/A
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 231 Uptime: 1 min Memory: 861.4/3768.2MB
           Client: Shell (bash) inxi: 2.3.56
```

---

### Post by SagaciousKJB on 2018-10-11
> **meiselstein said:**
> Hi AutoDave and Deadflowr, here are the results of my inxi -F:

```
System:    Host: moo Kernel: 4.18.13-041813-generic x86_64 bits: 64
           Desktop: Gnome 3.28.3 Distro: Ubuntu 18.04.1 LTS
Machine:   Device: laptop System: ASUSTeK product: VivoBook 14_ASUS Laptop X407MA_X407MA v: 1.0 serial: N/A
           Mobo: ASUSTeK model: X407MA v: 1.0 serial: N/A
           UEFI: American Megatrends v: X407MA.204 date: 03/07/2018
Battery    BAT0: charge: 24.5 Wh 72.2% condition: 33.9/33.2 Wh (102%)
CPU:       Dual core Intel Celeron N4000 (-MCP-) cache: 4096 KB
           clock speeds: max: 2600 MHz 1: 876 MHz 2: 909 MHz
Graphics:  Card: Intel Device 3185
           Display Server: x11 (X.Org 1.19.6 ) driver: i915
           Resolution: 1366x768@60.00hz
           OpenGL: renderer: Mesa DRI Intel UHD Graphics 600 (Geminilake 2x6)
           version: 4.5 Mesa 18.0.5
Audio:     Card Intel Device 3198 driver: snd_hda_intel
           Sound: ALSA v: k4.18.13-041813-generic
Network:   Card: Realtek RTL8723BE PCIe Wireless Network Adapter
           driver: rtl8723be
           IF: wlo1 state: up mac: 70:c9:4e:2c:66:45
Drives:    HDD Total Size: 120.0GB (6.6% used)
           ID-1: /dev/sda model: KINGSTON_SA400S3 size: 120.0GB
Partition: ID-1: / size: 110G used: 7.4G (8%) fs: ext4 dev: /dev/sda2
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 48.0C mobo: N/A
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 231 Uptime: 1 min Memory: 861.4/3768.2MB
           Client: Shell (bash) inxi: 2.3.56
```

If you do this command from Fedora as welll and look at the differences it might shed some light.  Could be using something besides XOrg, or a different driver than mesa, etc.

---

### Post by meiselstein on 2018-10-12
> **SagaciousKJB said:**
> If you do this command from Fedora as welll and look at the differences it might shed some light.  Could be using something besides XOrg, or a different driver than mesa, etc.

Good idea:

```
Host: localhost.localdomain Kernel: 4.18.5-300.fc29.x86_64 x86_64 bits: 64 
  Desktop: Gnome 3.30.1 Distro: Fedora release 29 (Twenty Nine) 
Machine:
  Type: Laptop System: ASUSTeK 
  product: VivoBook 14_ASUS Laptop X407MA_X407MA v: 1.0 
  serial: <root required> 
  Mobo: ASUSTeK model: X407MA v: 1.0 serial: <root required> 
  UEFI: American Megatrends v: X407MA.204 date: 03/07/2018 
Battery:
  ID-1: BAT0 charge: 28.4 Wh condition: 33.9/33.2 Wh (102%) 
CPU:
  Topology: Dual Core model: Intel Celeron N4000 bits: 64 type: MCP 
  L2 cache: 4096 KiB 
  Speed: 796 MHz min/max: 800/2600 MHz Core speeds (MHz): 1: 796 2: 796 
Graphics:
  Device-1: Intel driver: i915 v: kernel 
  Display: wayland server: Fedora Project X.org 1.20.1 driver: i915 
  resolution: 1366x768~60Hz 
  OpenGL: renderer: Mesa DRI Intel UHD Graphics 600 (Geminilake 2x6) 
  v: 4.5 Mesa 18.2.2 
Audio:
  Device-1: Intel driver: snd_hda_intel 
  Sound Server: ALSA v: k4.18.5-300.fc29.x86_64 
Network:
  Device-1: Realtek RTL8723BE PCIe Wireless Network Adapter 
  driver: rtl8723be 
  IF: wlo1 state: up mac: 70:c9:4e:2c:66:45 
  IF-ID-1: virbr0 state: down mac: 52:54:00:7c:d3:a2 
  IF-ID-2: virbr0-nic state: down mac: 52:54:00:7c:d3:a2 
Drives:
  Local Storage: total: 111.79 GiB used: 7.04 GiB (6.3%) 
  ID-1: /dev/sda vendor: Kingston model: SA400S37120G size: 111.79 GiB 
Partition:
  ID-1: / size: 48.97 GiB used: 6.71 GiB (13.7%) fs: ext4 dev: /dev/dm-0 
  ID-2: /boot size: 975.9 MiB used: 158.4 MiB (16.2%) fs: ext4 
  dev: /dev/sda2 
  ID-3: /home size: 55.64 GiB used: 133.0 MiB (0.2%) fs: ext4 dev: /dev/dm-2 
  ID-4: swap-1 size: 3.80 GiB used: 29.8 MiB (0.8%) fs: swap dev: /dev/dm-1 
Sensors:
  System Temperatures: cpu: 47.0 C mobo: N/A 
  Fan Speeds (RPM): N/A 
Info:
  Processes: 193 Uptime: 28m Memory: 3.68 GiB used: 2.08 GiB (56.6%) 
  Shell: bash inxi: 3.0.26
```

---

### Post by NM5TF on 2018-10-12
you might find an answer here [http://https://wiki.archlinux.org/index.php/intel_graphics#Tear-free_video]("http://https://wiki.archlinux.org/index.php/intel_graphics#Tear-free_video")

tommy

---

### Post by meiselstein on 2018-10-12
> **NM5TF said:**
> you might find an answer here [http://https://wiki.archlinux.org/index.php/intel_graphics#Tear-free_video](http://https://wiki.archlinux.org/index.php/intel_graphics#Tear-free_video)

tommy
Thanks, Tommy. But, I have already tried the tear free video fix in the link that you provided.

---

### Post by NM5TF on 2018-10-12
bummer.....from the output of inxi, you seem to already have the latest drivers...

have seen suggestion to switch to wayland....have not tried/verified it myself...

are you using a compositer by chance ??? check this out from the Linux Manual page...

```
Option "TearFree" "boolean"
    Disable or enable TearFree updates. This option forces X to perform all rendering to a backbuffer prior to updating the actual display. It requires an extra memory allocation the same size as a framebuffer, the occasional extra copy, and requires Damage tracking. Thus enabling TearFree requires more memory and is slower (reduced throughput) and introduces a small amount of output latency, but it should not impact input latency. However, the update to the screen is then performed synchronously with the vertical refresh of the display so that the entire update is completed before the display starts its refresh. That is only one frame is ever visible, preventing an unsightly tear between two visible and differing frames. Note that this replicates what the compositing manager should be doing, however TearFree will redirect the compositor updates (and those of fullscreen games) directly on to the scanout thus incurring no additional overhead in the composited case. Also note that not all compositing managers prevent tearing, and if the outputs are rotated, there will still be tearing without TearFree enabled. 
    Default: TearFree is disabled. 
```

might be worth turning compositor off if using one...

---

### Post by deadflowr on 2018-10-12
You can try update drivers from here:
[https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers]("https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers")
Read it through.
Also note that the drivers from there will probably make there way into Ubuntu's 18.04.2 or 18.04.3 [hardware stack enablements]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack") when they are released.

---

