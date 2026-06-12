---
title: "Can't get new video card going....get xorg login"
date: 2018-08-13
forum: General Help
---

### Post by iscariot on 2018-08-13
I recently upgraded my video card...I went from an NVIDIA to a newer NVIDIA.  Now, I only get 1024x768 video on my main monitor.  Are there directions on how to fix this?  When I run xrandr, I don't get any real info that looks to help.

---

### Post by NM5TF on 2018-08-13
> **iscariot said:**
> I recently upgraded my video card..[COLOR="#FF0000"].I went from an NVIDIA to a newer NVIDIA[/COLOR].  Now, I only get 1024x768 video on my main monitor.  Are there directions on how to fix this?  When I run xrandr, I don't get any real info that looks to help.

you also didn't post any real helpful info.....such as OS, hardware specs, etc.....

the output of inxi would be real helpful...

```
inxi -F
```

tommy

---

### Post by iscariot on 2018-08-13
Sorry, total brainfart on that one.  Here's the output:

```

[1;34mCPU:      [0;37m [1;34mOcta core[0;37m AMD FX-8320E Eight-Core (-MCP-)[0;37m [1;34mcache:[0;37m 16384 KB[0;37m 
[1;34m          [0;37m [1;34mClock Speeds:[0;37m [1;34m1:[0;37m 1400.00 MHz[0;37m [1;34m2:[0;37m 1400.00 MHz[0;37m [1;34m3:[0;37m 1400.00 MHz[0;37m [1;34m4:[0;37m 1800.00 MHz[0;37m [1;34m5:[0;37m 1400.00 MHz[0;37m [1;34m6:[0;37m 1800.00 MHz[0;37m [1;34m7:[0;37m 1400.00 MHz[0;37m [1;34m8:[0;37m 1400.00 MHz[0;37m
[1;34m          [0;37m [1;34mCPU Flags:[0;37m 3dnowprefetch abm aes aperfmperf apic arat avx bmi1 clflush cmov cmp_legacy 
[1;34m          [0;37m constant_tsc cpb cr8_legacy cx16 cx8 de decodeassists extapic extd_apicid f16c flushbyasid 
[1;34m          [0;37m fma fma4 fpu fxsr fxsr_opt ht hw_pstate ibs lahf_lm lbrv lm lwp mca mce misalignsse mmx 
[1;34m          [0;37m mmxext monitor msr mtrr nodeid_msr nonstop_tsc nopl npt nrip_save nx osvw pae pat pausefilter 
[1;34m          [0;37m pclmulqdq pdpe1gb perfctr_core perfctr_nb pfthreshold pge pni popcnt pse pse36 rdtscp 
[1;34m          [0;37m rep_good sep skinit sse sse2 sse4_1 sse4_2 sse4a ssse3 svm svm_lock syscall tbm tce topoext 
[1;34m          [0;37m tsc tsc_scale vmcb_clean vme vmmcall wdt xop xsave 
[0m

```

As for the computer, here are the specs:

MOBO: ASROCK 970 Extreme3
Memory: 32GB
CPU: AMD FX-8320
Video: Geforce GTX 1060 3GB

---

### Post by NM5TF on 2018-08-13
I asked for the output of [COLOR="#FF0000"]inxi -F[/COLOR] for a reason....all info to possibly help you would be there....

do you know what nvidia driver  & Xorg-server you have ???

OS & kernel version ???

inxi -F gives all information in 1 window like this:

```
[tommy@tommy ~]$ inxi -F
System:    Host: tommy Kernel: 4.17.14-arch1-1-ARCH x86_64 bits: 64
           Desktop: Xfce 4.12.4 Distro: Arch Linux
Machine:   Device: desktop System: Dell product: Inspiron 531s v: 00 serial: N/A
           Mobo: Dell model: 0RY206 v: &#65533;&#65533;&#65533; serial: N/A
           BIOS: Dell v: 1.0.7 date: 11/09/2007
CPU:       Dual core AMD Athlon 64 X2 4000+ (-MCP-) cache: 1024 KB
           clock speeds: max: 2100 MHz 1: 2000 MHz 2: 2000 MHz
Graphics:  Card: NVIDIA C61 [GeForce 6150SE nForce 430]
           Display Server: X.Org 1.20.0
           drivers: nouveau (unloaded: modesetting,fbdev,vesa)
           Resolution: 1920x1080@60.00hz
           OpenGL: renderer: N/A version: N/A
Audio:     Card NVIDIA MCP61 High Def. Audio driver: snd_hda_intel
           Sound: Advanced Linux Sound Architecture v: k4.17.14-arch1-1-ARCH
Network:   Card: Edimax EW-7811Un 802.11n Wireless Adapter [Realtek RTL8188CUS]
           driver: rtl8192cu
           IF: wlp0s2f1u9 state: up mac: 80:1f:02:b6:d2:ce
Drives:    HDD Total Size: 250.0GB (42.4% used)
           ID-1: /dev/sda model: ST3250820AS size: 250.0GB
Partition: ID-1: / size: 80G used: 61G (81%) fs: ext4 dev: /dev/sda10
           ID-2: swap-1 size: 2.25GB used: 0.00GB (0%)
           fs: swap dev: /dev/sda6
Sensors:   System Temperatures: cpu: 74.0C mobo: 41.0C
           Fan Speeds (in rpm): cpu: 1766 fan-2: 2202 fan-3: 0 fan-4: 0
Info:      Processes: 139 Uptime: 7:36 Memory: 1075.4/3443.6MB
           Client: Shell (bash) inxi: 2.3.56 

```

tommy

---

### Post by iscariot on 2018-08-13
My mistake.  I typed the wrong switch.  Here's the output from inxi -F

```

[1;34mSystem:   [0;37m [1;34mHost:[0;37m xi-desktop [1;34mKernel:[0;37m 4.2.0-34-generic x86_64 (64 bit) [1;34mConsole:[0;37m tty 2 [1;34mDistro:[0;37m Ubuntu 14.04 trusty
[1;34mMachine:  [0;37m [1;34mMobo:[0;37m ASRock [1;34mmodel:[0;37m 970 Extreme3 [1;34mBios:[0;37m American Megatrends [1;34mversion:[0;37m P1.60 [1;34mdate:[0;37m 06/26/2012
[1;34mCPU:      [0;37m [1;34mOcta core[0;37m AMD FX-8320E Eight-Core (-MCP-)[0;37m [1;34mcache:[0;37m 16384 KB [1;34mflags:[0;37m (lm nx sse sse2 sse3 sse4_1 sse4_2 sse4a ssse3 svm)[0;37m 
[1;34m          [0;37m [1;34mClock Speeds:[0;37m [1;34m1:[0;37m 1400.00 MHz[0;37m [1;34m2:[0;37m 3200.00 MHz[0;37m [1;34m3:[0;37m 1400.00 MHz[0;37m [1;34m4:[0;37m 2800.00 MHz[0;37m [1;34m5:[0;37m 1800.00 MHz[0;37m [1;34m6:[0;37m 1800.00 MHz[0;37m [1;34m7:[0;37m 1400.00 MHz[0;37m [1;34m8:[0;37m 1800.00 MHz[0;37m
[1;34mGraphics: [0;37m [1;34mCard:[0;37m NVIDIA Device 1c02 
[1;34m          [0;37m [1;34mX.org:[0;37m 1.17.2 [1;34mdrivers:[0;37m vesa [1;31mFAILED:[0;37m nvidia,fbdev,nouveau [1;34mtty size:[0;37m 80x25 [1;34mAdvanced Data:[0;37m N/A for root out of X
[1;34mAudio:    [0;37m [1;34mCard-1:[0;37m NVIDIA Device 10f1 [1;34mdriver:[0;37m snd_hda_intel [1;34mSound:[0;37m ALSA [1;34mver:[0;37m k4.2.0-34-generic
[1;34m          [0;37m [1;34mCard-2:[0;37m Advanced Micro Devices [AMD/ATI] SBx00 Azalia (Intel HDA) [1;34mdriver:[0;37m snd_hda_intel 
[1;34mNetwork:  [0;37m [1;34mCard-1:[0;37m Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [1;34mdriver:[0;37m r8169 
[1;34m          [0;37m [1;34mIF:[0;37m eth0 [1;34mstate:[0;37m up [1;34mspeed:[0;37m 1000 Mbps [1;34mduplex:[0;37m full [1;34mmac:[0;37m bc:5f:f4:1d:41:be
[1;34m          [0;37m [1;34mCard-2:[0;37m Ralink RT2760 Wireless 802.11n 1T/2R [1;34mdriver:[0;37m rt2800pci 
[1;34m          [0;37m [1;34mIF:[0;37m wlan0 [1;34mstate:[0;37m down [1;34mmac:[0;37m 00:1d:6a:3a:4f:e7
[1;34mDrives:   [0;37m [1;34mHDD Total Size:[0;37m 4272.3GB (3.9% used) [1;34m1:[0;37m [1;34mid:[0;37m /dev/sda [1;34mmodel:[0;37m WDC_WD20EZRZ [1;34msize:[0;37m 2000.4GB 
[1;34m          [0;37m [1;34m2:[0;37m [1;34mid:[0;37m /dev/sdb [1;34mmodel:[0;37m WDC_WD20EZRZ [1;34msize:[0;37m 2000.4GB [1;34m3:[0;37m [1;34mid:[0;37m /dev/sdc [1;34mmodel:[0;37m PNY_CS1311_240GB [1;34msize:[0;37m 240.1GB [0;37m
[1;34m          [0;37m [1;34m4:[0;37m USB [1;34mid:[0;37m /dev/sdf [1;34mmodel:[0;37m iPod [1;34msize:[0;37m 31.4GB [0;37m
[1;34mPartition:[0;37m [1;34mID:[0;37m / [1;34msize:[0;37m 293G [1;34mused:[0;37m 38G (14%) [1;34mfs:[0;37m ext4 [1;34mID:[0;37m /boot [1;34msize:[0;37m 7.8G [1;34mused:[0;37m 85M (2%) [1;34mfs:[0;37m ext4 
[1;34m          [0;37m [1;34mID:[0;37m swap-1 [1;34msize:[0;37m 16.38GB [1;34mused:[0;37m 0.00GB (0%) [1;34mfs:[0;37m swap 
[1;34mRAID:     [0;37m No RAID devices detected - /proc/mdstat and md_mod kernel raid module present
[1;34mSensors:  [0;37m [1;34mSystem Temperatures: cpu:[0;37m 16.6C [1;34mmobo:[0;37m N/A 
[1;34m          [0;37m [1;34mFan Speeds (in rpm): cpu:[0;37m N/A 
[1;34mInfo:     [0;37m [1;34mProcesses:[0;37m 234 [1;34mUptime:[0;37m 2 min [1;34mMemory:[0;37m 236.2/15960.8MB[0;37m [1;34mRunlevel:[0;37m 2 [1;34mClient:[0;37m Shell (bash) [1;34minxi:[0;37m 1.9.17[0;37m [0;37m
[0m

```

---

### Post by NM5TF on 2018-08-13
that is REALLY  difficult to read with all the extra [COLOR="#FF0000"]1;34m 0;37m[/COLOR] characters strewn throughout.....

---

### Post by iscariot on 2018-08-14
Sorry about that.  Here is the file with the values fixed:

```

System:    Host: xi-desktop Kernel: 4.2.0-34-generic x86_64 (64 bit) Console: tty 2 Distro: Ubuntu 14.04 trusty
Machine:   Mobo: ASRock model: 970 Extreme3 Bios: American Megatrends version: P1.60 date: 06/26/2012
CPU:       Octa core AMD FX-8320E Eight-Core (-MCP-) cache: 16384 KB flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 sse4a ssse3 svm) 
           Clock Speeds: 1: 1400.00 MHz 2: 3200.00 MHz 3: 1400.00 MHz 4: 2800.00 MHz 5: 1800.00 MHz 6: 1800.00 MHz 7: 1400.00 MHz 8: 1800.00 MHz
Graphics:  Card: NVIDIA Device 1c02 
           X.org: 1.17.2 drivers: vesa FAILED: nvidia,fbdev,nouveau tty size: 80x25 Advanced Data: N/A for root out of X
Audio:     Card-1: NVIDIA Device 10f1 driver: snd_hda_intel Sound: ALSA ver: k4.2.0-34-generic
           Card-2: Advanced Micro Devices [AMD/ATI] SBx00 Azalia (Intel HDA) driver: snd_hda_intel 
Network:   Card-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller driver: r8169 
           IF: eth0 state: up speed: 1000 Mbps duplex: full mac: bc:5f:f4:1d:41:be
           Card-2: Ralink RT2760 Wireless 802.11n 1T/2R driver: rt2800pci 
           IF: wlan0 state: down mac: 00:1d:6a:3a:4f:e7
Drives:    HDD Total Size: 4272.3GB (3.9% used) 1: id: /dev/sda model: WDC_WD20EZRZ size: 2000.4GB 
           2: id: /dev/sdb model: WDC_WD20EZRZ size: 2000.4GB 3: id: /dev/sdc model: PNY_CS1311_240GB size: 240.1GB 
           4: USB id: /dev/sdf model: iPod size: 31.4GB 
Partition: ID: / size: 293G used: 38G (14%) fs: ext4 ID: /boot size: 7.8G used: 85M (2%) fs: ext4 
           ID: swap-1 size: 16.38GB used: 0.00GB (0%) fs: swap 
RAID:      No RAID devices detected - /proc/mdstat and md_mod kernel raid module present
Sensors:   System Temperatures: cpu: 16.6C mobo: N/A 
           Fan Speeds (in rpm): cpu: N/A 
Info:      Processes: 234 Uptime: 2 min Memory: 236.2/15960.8MB Runlevel: 2 Client: Shell (bash) inxi: 1.9.17 

```

---

### Post by NM5TF on 2018-08-14
according to the nvidia web site, your graphics should be using this driver

[https://www.geforce.com/drivers/results/136120]("https://www.geforce.com/drivers/results/136120")

install this driver & reboot.....

if it's fixed, great.....if not, have you tried the nouveau driver yet ???

---

### Post by iscariot on 2018-08-15
Ok I couldn't get it to install, broken dependency, but I did an upgrade to 16, and now X will start, however, once it starts it immediately boots me back to the login prompt.

---

### Post by iscariot on 2018-08-20
OK.  Now I'm getting a new one.  I sign in, and it immediately signs me out.  Something about GLX not being there.  Getting closer.....

---

