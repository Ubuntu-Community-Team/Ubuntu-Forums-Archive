---
title: "Ubuntu stopped booting"
date: 2020-12-14
forum: General Help
---

### Post by MrSums on 2020-12-14
Hi all,

Ubuntu just stopped booting. I can boot into recovery mode, but not standard. At first I suspected a hardware fault and stripped the machine down and gave it a good clean. I have also tried an Ubuntu Live disc, but same thing - it hangs when booting normally, but will boot into safe video mode.

So I then thought it might be my Nvidia driver which got upgraded recently - didn't notice whether this was the cause as I didn't immediately reboot the machine.

Checking dmesg for a bad boot and a safe boot, the bad boot seems to hang after wireless ethernet, but straight after the nvida drivers:
> [    7.618276] kernel: IPv6: ADDRCONF(NETDEV_CHANGE): enp3s0: link becomes ready
[    7.644199] kernel: input: HDA NVidia HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card2/input35
[    7.644558] kernel: input: HDA NVidia HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card2/input36
[    7.644599] kernel: input: HDA NVidia HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card2/input37
[    7.644687] kernel: input: HDA NVidia HDMI/DP,pcm=9 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card2/input38
[    7.644736] kernel: input: HDA NVidia HDMI/DP,pcm=10 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card2/input39
[    7.644781] kernel: input: HDA NVidia HDMI/DP,pcm=11 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card2/input40
[    7.644823] kernel: input: HDA NVidia HDMI/DP,pcm=12 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card2/input41
[   11.097281] kernel: wlp4s0: authenticate with e4:c3:2a:f1:4f:87
[   11.099367] kernel: wlp4s0: send auth to e4:c3:2a:f1:4f:87 (try 1/3)
[   11.103120] kernel: wlp4s0: authenticated
[   11.103554] kernel: wlp4s0: associate with e4:c3:2a:f1:4f:87 (try 1/3)
[   11.207590] kernel: wlp4s0: associate with e4:c3:2a:f1:4f:87 (try 2/3)
[   11.266624] kernel: wlp4s0: RX AssocResp from e4:c3:2a:f1:4f:87 (capab=0x1411 status=0 aid=1)
[   11.268126] kernel: wlp4s0: associated
[   11.306645] kernel: IPv6: ADDRCONF(NETDEV_CHANGE): wlp4s0: link becomes ready
[   11.307907] kernel: wlp4s0: Limiting TX power to 23 (23 - 0) dBm as advertised by e4:c3:2a:f1:4f:87

How do I check what is wrong please? If I remove the nvidia drivers whilst in safe mode, would that help?

CPU: i5-4670
M'board: GA-Z97N_WIFI
Graphics: GTX750Ti

Many thanks

Robert

---

### Post by ActionParsnip on 2020-12-14
What happened on the system prior to the issue? Updates? Power loss? Dropped laptop? Feline attack?

---

### Post by MrSums on 2020-12-14
All operating normally, but when I rebooted after a kernel upgrade, it just hung. So I booted into the last working kernel and all well for a time, but the next time I rebooted, none of the kernels worked so I tried the safe boot and that worked.

Thinking about my previous comment, as the Live disc doesn't work either, it is unlikely to be the drivers and more likely a hardware issue?

---

### Post by ajgreeny on 2020-12-14
> so I tried the safe boot and that worked.
What do you mean by safe boot; are you talking about recovery mode from the grub menu?

Tell us in more detail please all about your system.  Assuming you can get it to boot show us the output of terminal command ```
inxi -Fzx
``` which will show us a lot of detail of both hardware and software in use.

---

### Post by grahammechanical on 2020-12-14
Did you install the Nvidia driver through Software & Updates>Additional drivers or by downloading the driver from Nvidia? If you are loading Ubuntu from the recovery mode menu using the Resume option, then open Software & Updates>Additional Drivers tab and deactivate the Nvidia driver. A reboot will have Ubuntu loading with an open source video driver that will have been matched to the Linux kernel by the Ubuntu developers. They cannot do that with proprietary drivers. It has to be done by Nvidia.

This command will list appropriate proprietary video drivers

```
ubuntu-drivers list
```

You will need to wait to get a result

This command will install the most current proprietary video driver

```
sudo ubuntu-drivers autoinstall
```

Again you will need to wait and should also be connected to the internet. These commands can also be run from recovery mode with the Root shell prompt option. In this case you will not need to put the word sudo in the command. But first run the Network option to set up an internet connection. To get back to the recovery menu type

```
exit
```

Regards

---

### Post by MrSums on 2020-12-15
Thanks. Again, not convinced it is software-related, given the Live DVD doesn't boot either, but some interesting results from your guide:

I looked at Software & Updates>Additional drivers, and although the nvidia drivers are there (as below), it is the nouveau driver current in use.

Additional drivers:
> robert@lounge-lizard:~/Desktop$ ubuntu-drivers list
nvidia-driver-418-server, (kernel modules provided by linux-modules-nvidia-418-server-generic-hwe-20.04)
nvidia-driver-455, (kernel modules provided by linux-modules-nvidia-455-generic-hwe-20.04)
nvidia-driver-450-server, (kernel modules provided by linux-modules-nvidia-450-server-generic-hwe-20.04)
nvidia-340
nvidia-driver-440-server, (kernel modules provided by linux-modules-nvidia-440-server-generic-hwe-20.04)
nvidia-driver-450, (kernel modules provided by linux-modules-nvidia-450-generic-hwe-20.04)
nvidia-driver-390, (kernel modules provided by linux-modules-nvidia-390-generic-hwe-20.04)


And then running autoinstall, I get:

> robert@lounge-lizard:~/Desktop$ sudo ubuntu-drivers autoinstall
[sudo] password for robert: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 linux-modules-nvidia-455-generic-hwe-20.04 : Depends: nvidia-kernel-common-455 (<= 455.38-1) but 455.45.01-0ubuntu0.20.04.1 is to be installed
E: Unable to correct problems, you have held broken packages.


Cheers

Robert

---

### Post by MrSums on 2020-12-15
> **ajgreeny said:**
> What do you mean by safe boot; are you talking about recovery mode from the grub menu?

Tell us in more detail please all about your system.  Assuming you can get it to boot show us the output of terminal command ```
inxi -Fzx
``` which will show us a lot of detail of both hardware and software in use.

Thanks. Safe boot, yes I mean recovery mode.

Results from inxi:
> System:    Kernel: 5.4.0-58-generic x86_64 bits: 64 compiler: gcc v: 9.3.0 Desktop: MATE 1.24.0 
           Distro: Ubuntu 20.04.1 LTS (Focal Fossa) 
Machine:   Type: Desktop System: Gigabyte product: Z97N-WIFI v: N/A serial: <filter> 
           Mobo: Gigabyte model: Z97N-WIFI v: x.x serial: <filter> BIOS: American Megatrends v: F4 
           date: 05/30/2014 
Battery:   Device-1: hidpp_battery_0 model: Logitech Wireless Keyboard charge: 55% (should be ignored) 
           status: Discharging 
           Device-2: hidpp_battery_1 model: Logitech Wireless Mouse charge: 55% (should be ignored) 
           status: Discharging 
CPU:       Topology: Quad Core model: Intel Core i5-4670 bits: 64 type: MCP arch: Haswell rev: 3 
           L2 cache: 6144 KiB 
           flags: avx avx2 lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx bogomips: 27199 
           Speed: 800 MHz min/max: 800/3800 MHz Core speeds (MHz): 1: 800 2: 800 3: 800 4: 800 
Graphics:  Device-1: Intel Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics vendor: Gigabyte 
           driver: N/A bus ID: 00:02.0 
           Device-2: NVIDIA GM107 [GeForce GTX 750 Ti] vendor: Gigabyte driver: N/A bus ID: 01:00.0 
           Display: x11 server: X.Org 1.20.8 driver: nouveau,vesa unloaded: fbdev,modesetting 
           resolution: 1280x1024~N/A 
           OpenGL: renderer: llvmpipe (LLVM 10.0.0 256 bits) v: 3.3 Mesa 20.0.8 direct render: Yes 
Audio:     Device-1: Intel Xeon E3-1200 v3/4th Gen Core Processor HD Audio driver: snd_hda_intel 
           v: kernel bus ID: 00:03.0 
           Device-2: Intel 9 Series Family HD Audio vendor: Gigabyte driver: snd_hda_intel v: kernel 
           bus ID: 00:1b.0 
           Device-3: NVIDIA GM107 High Definition Audio [GeForce 940MX] vendor: Gigabyte 
           driver: snd_hda_intel v: kernel bus ID: 01:00.1 
           Sound Server: ALSA v: k5.4.0-58-generic 
Network:   Device-1: Intel Ethernet I217-V vendor: Gigabyte driver: e1000e v: 3.2.6-k port: f080 
           bus ID: 00:19.0 
           IF: eno1 state: down mac: <filter> 
           Device-2: Qualcomm Atheros AR8161 Gigabit Ethernet vendor: Gigabyte driver: alx v: kernel 
           port: d000 bus ID: 03:00.0 
           IF: enp3s0 state: up speed: 1000 Mbps duplex: full mac: <filter> 
           Device-3: Intel Wireless 7260 driver: iwlwifi v: kernel port: d000 bus ID: 04:00.0 
           IF: wlp4s0 state: up mac: <filter> 
Drives:    Local Storage: total: 2.05 TiB used: 599.17 GiB (28.6%) 
           ID-1: /dev/sda vendor: Samsung model: SSD 840 EVO 250GB size: 232.89 GiB 
           ID-2: /dev/sdb vendor: Crucial model: CT2000MX500SSD1 size: 1.82 TiB temp: 25 C 
Partition: ID-1: / size: 208.45 GiB used: 192.50 GiB (92.3%) fs: ext4 dev: /dev/sda1 
           ID-2: swap-1 size: 1.91 GiB used: 0 KiB (0.0%) fs: swap dev: /dev/sda5 
Sensors:   System Temperatures: cpu: 29.8 C mobo: 27.8 C 
           Fan Speeds (RPM): N/A 
Info:      Processes: 287 Uptime: 17h 26m Memory: 15.22 GiB used: 3.40 GiB (22.3%) Init: systemd 
           runlevel: 5 Compilers: gcc: 9.3.0 Shell: bash v: 5.0.17 inxi: 3.0.38 


Cheers

Robert

---

### Post by MrSums on 2020-12-15
So: thinking it might be a hardware problem with the video card, rather than software I plugged in to the onboard graphics rather than the external card and it booted normally :-)

Question is now, can I run checks on the video card or should I simply toss it and get another?

---

