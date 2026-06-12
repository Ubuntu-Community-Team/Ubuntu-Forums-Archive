---
title: "Could SUSPEND work on Ubuntu with AMD Ryzen 5 4500U + Radeon graphics?"
date: 2020-12-22
forum: General Help
---

### Post by pittaway on 2020-12-22
Long time Linux user here who knows only the basics!


My go-to Linux OS is up and running on my new Asus S15 Vivobook, AMD Ryzen 4500U, Radeon graphics.


Only problem is, suspend does not actually suspend the system, and battery drains as usual.


Suspend is an essential part of my work flow, hence my continued quest to see if I can solve the issue. So far, no luck. I tested some other distros and suspend does not shut down the machine properly (though I tested via usb installation media).


I have confirmed that this is not fixable with my current OS via a 43 post forum process.


I have turned up here because I found this [https://www.amd.com/en/support/kb/release-notes/rn-amdgpu-unified-linux-20-20](https://www.amd.com/en/support/kb/release-notes/rn-amdgpu-unified-linux-20-20)


Does anyone think that installing Ubuntu 20.04 on my laptop, and then doing the AMD Radeon software update, would get suspend working on my laptop?


I'm doubtful - I don't think my issue is with Radeon, I think it is with the Ryzen 4500U processor. However, the CPU info does state "AMD Ryzen 5 4500U with Radeon Graphics bits", so I am a bit unsure of what appears to be the combo. 


I found the linked page, became excited and downloaded Ubuntu 20.04 and planned to install it and do the AMD software update process, but then realised it's specifically for AMD graphics, which might mean that the suspend issue will remain unchanged.


Any thoughts would be much appreciated.


Here are my laptop's specs:


```
System:    Host: <filter> Kernel: 5.9.0-4mx-amd64 x86_64 bits: 64 compiler: N/A 
           parameters: BOOT_IMAGE=/boot/vmlinuz-5.9.0-4mx-amd64 
           root=UUID=<filter> ro quiet splash acpi_backlight=vendor 
           "acpi_osi=!Windows 2013" "acpi_osi=!Windows 2012" 
           Desktop: Xfce 4.14.2 tk: Gtk 3.24.5 info: xfce4-panel wm: xfwm4 dm: LightDM 1.26.0 
           Distro: MX-19.3_ahs_x64 patito feo November 11  2020 
           base: Debian GNU/Linux 10 (buster) 
Machine:   Type: Laptop System: ASUSTeK product: VivoBook_ASUSLaptop X521IA_M533IA v: 1.0 
           serial: <filter> 
           Mobo: ASUSTeK model: X521IA v: 1.0 serial: <filter> UEFI: American Megatrends 
           v: X521IA.303 date: 07/31/2020 
Battery:   ID-1: BAT0 charge: 26.3 Wh condition: 50.9/50.0 Wh (102%) volts: 11.9/11.9 
           model: ASUSTeK ASUS Battery type: Li-ion serial: <filter> status: Charging cycles: 5 
CPU:       Topology: 6-Core model: AMD Ryzen 5 4500U with Radeon Graphics bits: 64 type: MCP 
           arch: Zen family: 17 (23) model-id: 60 (96) stepping: 1 microcode: 8600106 
           L2 cache: 3072 KiB 
           flags: avx avx2 lm nx pae sse sse2 sse3 sse4_1 sse4_2 sse4a ssse3 svm bogomips: 28444 
           Speed: 1300 MHz min/max: 1400/2375 MHz boost: enabled Core speeds (MHz): 1: 1381 
           2: 1413 3: 1331 4: 1397 5: 1397 6: 1397 
           Vulnerabilities: Type: itlb_multihit status: Not affected 
           Type: l1tf status: Not affected 
           Type: mds status: Not affected 
           Type: meltdown status: Not affected 
           Type: spec_store_bypass 
           mitigation: Speculative Store Bypass disabled via prctl and seccomp 
           Type: spectre_v1 mitigation: usercopy/swapgs barriers and __user pointer sanitization 
           Type: spectre_v2 mitigation: Full AMD retpoline, IBPB: conditional, IBRS_FW, STIBP: 
           disabled, RSB filling 
           Type: srbds status: Not affected 
           Type: tsx_async_abort status: Not affected 
Graphics:  Device-1: AMD Renoir vendor: ASUSTeK driver: amdgpu v: kernel bus ID: 03:00.0 
           chip ID: 1002:1636 
           Display: x11 server: X.Org 1.20.9 driver: amdgpu,ati unloaded: fbdev,modesetting,vesa 
           resolution: 1920x1080~60Hz 
           OpenGL: renderer: AMD RENOIR (DRM 3.39.0 5.9.0-4mx-amd64 LLVM 10.0.0) 
           v: 4.6 Mesa 20.1.8 direct render: Yes 
Audio:     Device-1: AMD driver: snd_hda_intel v: kernel bus ID: 03:00.1 chip ID: 1002:1637 
           Device-2: AMD Family 17h HD Audio vendor: ASUSTeK driver: snd_hda_intel v: kernel 
           bus ID: 03:00.6 chip ID: 1022:15e3 
           Sound Server: ALSA v: k5.9.0-4mx-amd64 
Network:   Device-1: Intel driver: iwlwifi v: kernel port: N/A bus ID: 01:00.0 
           chip ID: 8086:2723 
           IF: wlan0 state: up mac: <filter> 
Drives:    Local Storage: total: 238.47 GiB used: 13.44 GiB (5.6%) 
           ID-1: /dev/nvme0n1 vendor: SK Hynix model: HFM256GDJTNG-8310A size: 238.47 GiB 
           block size: physical: 512 B logical: 512 B speed: 15.8 Gb/s lanes: 2 serial: <filter> 
           rev: 80001C00 scheme: GPT 
Partition: ID-1: / raw size: 198.78 GiB size: 194.66 GiB (97.93%) used: 13.44 GiB (6.9%) 
           fs: ext4 dev: /dev/nvme0n1p5 
Sensors:   System Temperatures: cpu: 46.1 C mobo: N/A gpu: amdgpu temp: 40 C 
           Fan Speeds (RPM): cpu: 2700 
Repos:     No active apt repos in: /etc/apt/sources.list 
           Active apt repos in: /etc/apt/sources.list.d/debian-stable-updates.list 
           1: deb http://deb.debian.org/debian buster-updates main contrib non-free
           Active apt repos in: /etc/apt/sources.list.d/debian.list 
           1: deb http://deb.debian.org/debian buster main contrib non-free
           2: deb http://deb.debian.org/debian-security buster/updates main contrib non-free
           Active apt repos in: /etc/apt/sources.list.d/mx.list 
           1: deb https://ftp.saix.net/pub/linux/distributions/mxlinux/mx/repo/ buster main non-free
           2: deb https://ftp.saix.net/pub/linux/distributions/mxlinux/mx/testrepo/ buster test
           3: deb https://ftp.saix.net/pub/linux/distributions/mxlinux/mx/repo/ buster ahs
           No active apt repos in: /etc/apt/sources.list.d/various.list 
Info:      Processes: 275 Uptime: 1h 01m Memory: 7.27 GiB used: 2.84 GiB (39.1%) Init: SysVinit 
           v: 2.93 runlevel: 5 default: 5 Compilers: gcc: 8.3.0 alt: 8 Shell: quick-system-in 
           running in: quick-system-in inxi: 3.0.36 






```

---

### Post by mrdc76 on 2020-12-22
The kernel on 20.04 might not be new enough, but you could install linux-generic-hwe-20.04-edge for a newer kernel if you'd want to stay in LTS. Otherwise you could install 20.10.

---

### Post by QIII on 2020-12-22
Would you please post the output of the two following commands:

```
lsmod | grep radeon
```

and 

```
lsmod | grep amdgpu
```

It appears you are running amdgpu, so I suspect that is where you will get results.  You are also running mesa.

Although it might certainly be helpful in your case, please be very careful when people recommend installing new kernels if you are not very familiar with the potential results and possible breakage.

---

### Post by pittaway on 2020-12-23
Thanks Qlll

Output for [COLOR=#000000][FONT=&amp]lsmod | grep radeon [/FONT][/COLOR]came up with nothing!

Output for [COLOR=#000000][FONT=&amp]lsmod | grep amdgpu:[/FONT][/COLOR]

```
[COLOR=#000000]amdgpu 5865472 17[/COLOR]
[COLOR=#000000]gpu_sched 40960 1 amdgpu[/COLOR]
[COLOR=#000000]i2c_algo_bit 16384 1 amdgpu[/COLOR]
[COLOR=#000000]ttm 122880 1 amdgpu[/COLOR]
[COLOR=#000000]drm_kms_helper 258048 1 amdgpu[/COLOR]
[COLOR=#000000]drm 565248 13 gpu_sched,drm_kms_helper,amdgpu,ttm[/COLOR]
```

---

### Post by QIII on 2020-12-26
No results from looking for radeon means that module is not loaded.  Looking for amdgpu, we found that module, the correct one for your hardware, is loaded and running.

There are two possible drivers for AMD graphics units and each module is present in the kernel to be activated at install time.  For hardware requiring the radeon, that module is active.  For hardware supported by amdgpu, that module is active.

That is the way it is in Linux now.  There are no other drivers to install or upgrade to.  AMD is all open source -- except for the AMDGPU-PRO overlay, which the vast majority of users generally do not need.

I believe your solution lies elsewhere.

---

### Post by jay-eich on 2020-12-27
Greetings,

It looks like you are running Debian, and that should allow suspend.
I am runninng two machinne, one with Ubuntu 20.04, and the other with 20.10
I have an AMD GPU, and am running AMD drivers.
BUT, I did not install directly from AMD but used the 'mesa' package for OCL.
Both my machines will suspend.
I agree with QIII. it may be something else.
Could it be as simple as a mouse,or keypad wiggle? That can terminate the suspend on my machines. 
Maybe amd Microcode?

Here are what I have installed... (
 apt list | grep ^mesa
WARNING: apt does not have a stable CLI interface. Use with caution in scripts.
mesa-common-dev/groovy,now 20.2.1-1 amd64 [installed]
mesa-common-dev/groovy 20.2.1-1 i386
mesa-opencl-icd/groovy,now 20.2.1-1 amd64 [installed]
mesa-opencl-icd/groovy 20.2.1-1 i386
mesa-utils-extra/groovy,now 8.4.0-1build1 amd64 [installed]
mesa-utils/groovy,now 8.4.0-1build1 amd64 [installed,automatic]
mesa-va-drivers/groovy,now 20.2.1-1 amd64 [installed,automatic]
mesa-va-drivers/groovy 20.2.1-1 i386
mesa-vdpau-drivers/groovy,now 20.2.1-1 amd64 [installed,automatic]
mesa-vdpau-drivers/groovy 20.2.1-1 i386
mesa-vulkan-drivers/groovy,now 20.2.1-1 amd64 [installed,automatic]
mesa-vulkan-drivers/groovy 20.2.1-1 i386


and
 apt list | grep ^amd
WARNING: apt does not have a stable CLI interface. Use with caution in scripts.

amd64-microcode/groovy,now 3.20191218.1ubuntu1 amd64 [installed,automatic]
---

Do you have the "amd64-microcode" package installed?

I have the power management on my laptop configured to suspend when the lid closes;
and on the desktop, I can use the 'suspend' option when powering down.
Does either of these work for you?

Have you been doing ann update and upgrage to get new  and replaced packages?

Fingers crossed,
 jay

PS, I have also used the Debian releases (on an older i-386) and they suspended as well. (without manually loading drivers.)

---

### Post by mathieu-tarral on 2021-03-29
Hi,

I saw this post as I had a similar suspend/resume issue on my Thinkpad laptop based on AMD.
I managed to find the [solution]("https://ubuntuforums.org/showthread.php?t=2459895&p=14028901#post14028901")

I hope this helps !

---

