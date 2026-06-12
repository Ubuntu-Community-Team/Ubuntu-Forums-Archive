---
title: "HP 255 G5 laptop with Ubuntu 16.04.1 - fan always on"
date: 2017-01-14
forum: General Help
---

### Post by slobodan-covek on 2017-01-14
I have bought a new laptop (HP 255 G5) with AMD A6-7310 APU. I have installed Ubuntu 16.04.1 (64 bit) and I have been using it for a week now.

The fan is noisy and it is always on. Either on full speed or on some lower speed. Only for a very short periods, the fan is off (I think, anyway).

In BIOS, there is an option "Fan always on". I have turned it off (disable). But no change.

I have installed Laptop Made Tools, restarted laptop couple of times after that and situation is the same.

APU is not overheating. CPU cores are at around 50 oC, and laptop is cool.

Video drivers are Radeon. 
Gallium 0.4 on AMD MULLINS (DRM 2.43.0 / 4.4.0-59-generic, LLVM 3.9.1).

Stock Kernel.


Please help me fix this.

---

### Post by ik-0 on 2017-01-14
CPU temp is high for idle even for an AMD. Make sure that the OnDemand CPU governor is set. In laptop mode, you can set it for when it's on battery and when it's on AC power.


Also, install power top to see if any applications are consuming resources, waking up the CPU/GPU, and what sleep States your CPU is in most of the time.

---

### Post by slobodan-covek on 2017-01-15
That is the temperature under use. On idle it is a bit over 40 oC (which is high for idle). If it reads temperatures correctly. Can you recommend me a good program for that?

I don't know how to set OnDemand CPU governer.

Here are the screenshots:

Top: [https://s29.postimg.org/5vecpjwon/2017_01_15_10_05_08.png](https://s29.postimg.org/5vecpjwon/2017_01_15_10_05_08.png)

PowerTop:

[https://s24.postimg.org/q75mzcxqt/2017_01_15_10_11_38.png](https://s24.postimg.org/q75mzcxqt/2017_01_15_10_11_38.png)
[https://s24.postimg.org/ybdr43k5x/2017_01_15_10_11_58.png](https://s24.postimg.org/ybdr43k5x/2017_01_15_10_11_58.png)
[https://s24.postimg.org/rv4se0bmd/2017_01_15_10_12_16.png](https://s24.postimg.org/rv4se0bmd/2017_01_15_10_12_16.png)
[https://s24.postimg.org/tbgaw5ej9/2017_01_15_10_12_33.png](https://s24.postimg.org/tbgaw5ej9/2017_01_15_10_12_33.png)
[https://s24.postimg.org/lsx5nin6d/2017_01_15_10_12_53.png](https://s24.postimg.org/lsx5nin6d/2017_01_15_10_12_53.png)

---

### Post by slobodan-covek on 2017-01-15
Ah, there is loads more when I scroll down. :/

[https://s23.postimg.org/psq5m5wy3/image.png](https://s23.postimg.org/psq5m5wy3/image.png)
[https://s23.postimg.org/caj99vksr/image.png](https://s23.postimg.org/caj99vksr/image.png)
[https://s23.postimg.org/dbjhz01sb/image.png](https://s23.postimg.org/dbjhz01sb/image.png)
[https://s23.postimg.org/lsj09x6h7/image.png](https://s23.postimg.org/lsj09x6h7/image.png)
[https://s23.postimg.org/6ij52qayz/image.png](https://s23.postimg.org/6ij52qayz/image.png)
[https://s23.postimg.org/rcvhkk5cb/image.png](https://s23.postimg.org/rcvhkk5cb/image.png)
[https://s23.postimg.org/galt8dlvv/image.png](https://s23.postimg.org/galt8dlvv/image.png)
[https://s23.postimg.org/8ykygkt1n/image.png](https://s23.postimg.org/8ykygkt1n/image.png)
[https://s23.postimg.org/gorqlpvd7/image.png](https://s23.postimg.org/gorqlpvd7/image.png)

---

### Post by ik-0 on 2017-01-15
It looks like you're using the Radeon open source driver which can sometimes be behind for new video cards.  If you open the drivers tool it will scan for proprietary drivers to use like fglrx, which can have better thermal management of your video card.

Post the output of 
$ sudo service laptop-mode status

---

### Post by slobodan-covek on 2017-01-15
There are no AMD proprietary drivers fr 16.04. Only open source ones. And I have updated them.

Here is the output:

```

laptop-mode.service - Laptop Mode Tools
   Loaded: loaded (/lib/systemd/system/laptop-mode.service; enabled; vendor pres
   Active: active (exited) since &#1089;&#1091;&#1073; 2017-01-14 20:14:02 CET; 17h ago
     Docs: man:laptop_mode(8)
           man:laptop-mode.conf(8)
           http://samwel.tk/laptop_mode
  Process: 12189 ExecReload=auto (code=exited, status=0/SUCCESS)
  Process: 1124 ExecStart=init auto (code=exited, status=0/SUCCESS)
 Main PID: 1124 (code=exited, status=0/SUCCESS)

&#1112;&#1072;&#1085; 15 13:11:28 sloba-hp-255-g5 laptop_mode[12052]: enabled, not active [unchang
&#1112;&#1072;&#1085; 15 13:11:28 sloba-hp-255-g5 systemd[1]: Reloaded Laptop Mode Tools.
&#1112;&#1072;&#1085; 15 13:14:56 sloba-hp-255-g5 systemd[1]: Reloading Laptop Mode Tools.
&#1112;&#1072;&#1085; 15 13:14:56 sloba-hp-255-g5 laptop_mode[12119]: Laptop mode
&#1112;&#1072;&#1085; 15 13:14:56 sloba-hp-255-g5 laptop_mode[12119]: enabled, not active [unchang
&#1112;&#1072;&#1085; 15 13:14:56 sloba-hp-255-g5 systemd[1]: Reloaded Laptop Mode Tools.
&#1112;&#1072;&#1085; 15 13:17:56 sloba-hp-255-g5 systemd[1]: Reloading Laptop Mode Tools.
&#1112;&#1072;&#1085; 15 13:17:56 sloba-hp-255-g5 laptop_mode[12189]: Laptop mode
&#1112;&#1072;&#1085; 15 13:17:56 sloba-hp-255-g5 laptop_mode[12189]: enabled, not active [unchang
&#1112;&#1072;&#1085; 15 13:17:56 sloba-hp-255-g5 systemd[1]: Reloaded Laptop Mode Tools.

```

---

### Post by ik-0 on 2017-01-15
Also see Ati fan control http://askubuntu.com/a/116045/26198

---

### Post by ik-0 on 2017-01-15
> **slobodan-covek said:**
> There are no AMD proprietary drivers fr 16.04. Only open source ones. And I have updated them.

Here is the output:

```

laptop-mode.service - Laptop Mode Tools
   Loaded: loaded (/lib/systemd/system/laptop-mode.service; enabled; vendor pres
   Active: active (exited) since &#1089;&#1091;&#1073; 2017-01-14 20:14:02 CET; 17h ago
     Docs: man:laptop_mode(8)
           man:laptop-mode.conf(8)
           http://samwel.tk/laptop_mode
  Process: 12189 ExecReload=auto (code=exited, status=0/SUCCESS)
  Process: 1124 ExecStart=init auto (code=exited, status=0/SUCCESS)
 Main PID: 1124 (code=exited, status=0/SUCCESS)

&#1112;&#1072;&#1085; 15 13:11:28 sloba-hp-255-g5 laptop_mode[12052]: enabled, not active [unchang
&#1112;&#1072;&#1085; 15 13:11:28 sloba-hp-255-g5 systemd[1]: Reloaded Laptop Mode Tools.
&#1112;&#1072;&#1085; 15 13:14:56 sloba-hp-255-g5 systemd[1]: Reloading Laptop Mode Tools.
&#1112;&#1072;&#1085; 15 13:14:56 sloba-hp-255-g5 laptop_mode[12119]: Laptop mode
&#1112;&#1072;&#1085; 15 13:14:56 sloba-hp-255-g5 laptop_mode[12119]: enabled, not active [unchang
&#1112;&#1072;&#1085; 15 13:14:56 sloba-hp-255-g5 systemd[1]: Reloaded Laptop Mode Tools.
&#1112;&#1072;&#1085; 15 13:17:56 sloba-hp-255-g5 systemd[1]: Reloading Laptop Mode Tools.
&#1112;&#1072;&#1085; 15 13:17:56 sloba-hp-255-g5 laptop_mode[12189]: Laptop mode
&#1112;&#1072;&#1085; 15 13:17:56 sloba-hp-255-g5 laptop_mode[12189]: enabled, not active [unchang
&#1112;&#1072;&#1085; 15 13:17:56 sloba-hp-255-g5 systemd[1]: Reloaded Laptop Mode Tools.

```

There used to be a print out that shows what governor is set but you can use the following to set the governor. Some CPUs only have power save and performance.
sudo cpufreq-set -r -g performance

---

### Post by slobodan-covek on 2017-01-15
I tried this:

```
sudo gedit /usr/lib/pm-utils/power.d/radeon-power_profile
```

Then in a text editor that appeared (empty) I put this and saved:

```
#!/bin/sh

echo profile > /sys/class/drm/card0/device/power_method
echo auto > /sys/class/drm/card0/device/power_profile

exit 0
```

and then in Terminal:

```
sudo chmod +x /usr/lib/pm-utils/power.d/radeon-power_profile
```

Reboted.

Behaves the same. :/

---

### Post by slobodan-covek on 2017-01-16
Please help.

---

### Post by slobodan-covek on 2017-01-18
I have deleted Laptop Made Tools and installed LTP. Started LTP. It said that it has now started in AC mode (because laptop is pluged in). And no change. :(

What else can I try?

---

### Post by slobodan-covek on 2017-01-24
So... No solution? :(

---

### Post by mastablasta on 2017-01-24
TLP ?

lmsensors? psensort to see the temp?

some fan control?

anyway the fan is likely from GPU or GPU on CPU. what is your GPU chip? maybe you need correct drivers or you need to use a correct driver parameter.

---

### Post by slobodan-covek on 2017-01-24
Yes, TLP. [http://linrunner.de/en/tlp/tlp.html](http://linrunner.de/en/tlp/tlp.html)

Temperatures are about 42oC on idle for CPU, around 45oC for GPU. On load (VLC video playback, and Firefox with multiple tabs open) it goes up to 52oC for the CPU and I think at about 55oC for GPU.

GPU is integrated, R4 Radeon. It is AMD APU.

Drivers are open source AMD ones. There are no other drivers aveliable.

---

### Post by mastablasta on 2017-01-24
official documentation (KMS module): [SIZE=2]https://www.x.org/wiki/RadeonFeature/
[/SIZE]
ubuntu documentation (enabling dpm - see under Power Management): [SIZE=2]https://help.ubuntu.com/community/RadeonDriver
[/SIZE]
another option would be to go with 14.04 and then install catalyst driver. you need ot install the old version of 14.04 not 14.04.3 or later. it is supported until April 2019.

---

### Post by slobodan-covek on 2017-01-29
I can't change power profile (/sys/class/drm/card0/device/power_profile). I delete "default" and write "auto" and then try to save and it says "invalid agrument".

I have run Nautilus as root.

Plus, there is infinite amount of "card0-VGA-1" folders. I can go to like:

/sys/class/drm/card0-VGA-1/device/card0-VGA-1/device/card0-VGA-1/device/card0-VGA-1/device/card0-VGA-1/device/card0-VGA-1/device/...

---

### Post by slobodan-covek on 2017-01-29
Here is the output of ```
dmesg | egrep 'drm|radeon'
```


```
[    1.654376] [drm] Initialized drm 1.1.0 20060810
[    1.711317] [drm] radeon kernel modesetting enabled.
[    1.720807] fb: switching to radeondrmfb from EFI VGA
[    1.721901] [drm] initializing kernel modesetting (MULLINS 0x1002:0x9851 0x103C:0x82F6).
[    1.721926] [drm] register mmio base: 0xF0C00000
[    1.721928] [drm] register mmio size: 262144
[    1.721936] [drm] doorbell mmio base: 0xF0000000
[    1.721938] [drm] doorbell mmio size: 8388608
[    1.723261] radeon 0000:00:01.0: VRAM: 512M 0x0000000000000000 - 0x000000001FFFFFFF (512M used)
[    1.723265] radeon 0000:00:01.0: GTT: 2048M 0x0000000020000000 - 0x000000009FFFFFFF
[    1.723268] [drm] Detected VRAM RAM=512M, BAR=256M
[    1.723269] [drm] RAM width 128bits DDR
[    1.723403] [drm] radeon: 512M of VRAM memory ready
[    1.723406] [drm] radeon: 2048M of GTT memory ready.
[    1.723422] [drm] Loading mullins Microcode
[    1.723607] [drm] Internal thermal controller without fan control
[    1.725175] [drm] radeon: dpm initialized
[    1.727424] [drm] Found VCE firmware/feedback version 40.2.2 / 15!
[    1.727442] [drm] GART: num cpu pages 524288, num gpu pages 524288
[    1.772531] [drm] PCIE GART of 2048M enabled (table at 0x0000000000324000).
[    1.772733] radeon 0000:00:01.0: WB enabled
[    1.772762] radeon 0000:00:01.0: fence driver on ring 0 use gpu addr 0x0000000020000c00 and cpu addr 0xffff880034e99c00
[    1.772767] radeon 0000:00:01.0: fence driver on ring 1 use gpu addr 0x0000000020000c04 and cpu addr 0xffff880034e99c04
[    1.772771] radeon 0000:00:01.0: fence driver on ring 2 use gpu addr 0x0000000020000c08 and cpu addr 0xffff880034e99c08
[    1.772774] radeon 0000:00:01.0: fence driver on ring 3 use gpu addr 0x0000000020000c0c and cpu addr 0xffff880034e99c0c
[    1.772778] radeon 0000:00:01.0: fence driver on ring 4 use gpu addr 0x0000000020000c10 and cpu addr 0xffff880034e99c10
[    1.773383] radeon 0000:00:01.0: fence driver on ring 5 use gpu addr 0x0000000000076c98 and cpu addr 0xffffc90001436c98
[    1.773612] radeon 0000:00:01.0: fence driver on ring 6 use gpu addr 0x0000000020000c18 and cpu addr 0xffff880034e99c18
[    1.773615] radeon 0000:00:01.0: fence driver on ring 7 use gpu addr 0x0000000020000c1c and cpu addr 0xffff880034e99c1c
[    1.773620] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[    1.773622] [drm] Driver supports precise vblank timestamp query.
[    1.773675] radeon 0000:00:01.0: radeon: using MSI.
[    1.773711] [drm] radeon: irq initialized.
[    1.777448] [drm] ring test on 0 succeeded in 2 usecs
[    1.777534] [drm] ring test on 1 succeeded in 2 usecs
[    1.777551] [drm] ring test on 2 succeeded in 2 usecs
[    1.777747] [drm] ring test on 3 succeeded in 4 usecs
[    1.777754] [drm] ring test on 4 succeeded in 3 usecs
[    1.803596] [drm] ring test on 5 succeeded in 2 usecs
[    1.803610] [drm] UVD initialized successfully.
[    1.912810] [drm] ring test on 6 succeeded in 13 usecs
[    1.912819] [drm] ring test on 7 succeeded in 2 usecs
[    1.912821] [drm] VCE initialized successfully.
[    1.915562] [drm] ib test on ring 0 succeeded in 0 usecs
[    2.412106] [drm] ib test on ring 1 succeeded in 0 usecs
[    2.912250] [drm] ib test on ring 2 succeeded in 0 usecs
[    2.912322] [drm] ib test on ring 3 succeeded in 0 usecs
[    2.912378] [drm] ib test on ring 4 succeeded in 0 usecs
[    3.412301] [drm] ib test on ring 5 succeeded
[    3.412827] [drm] ib test on ring 6 succeeded
[    3.413218] [drm] ib test on ring 7 succeeded
[    3.418052] [drm] radeon atom DIG backlight initialized
[    3.418056] [drm] Radeon Display Connectors
[    3.418059] [drm] Connector 0:
[    3.418060] [drm]   eDP-1
[    3.418062] [drm]   HPD1
[    3.418066] [drm]   DDC: 0x6530 0x6530 0x6534 0x6534 0x6538 0x6538 0x653c 0x653c
[    3.418067] [drm]   Encoders:
[    3.418069] [drm]     LCD1: INTERNAL_UNIPHY
[    3.418070] [drm] Connector 1:
[    3.418072] [drm]   HDMI-A-1
[    3.418073] [drm]   HPD2
[    3.418076] [drm]   DDC: 0x6540 0x6540 0x6544 0x6544 0x6548 0x6548 0x654c 0x654c
[    3.418077] [drm]   Encoders:
[    3.418079] [drm]     DFP1: INTERNAL_UNIPHY
[    3.418080] [drm] Connector 2:
[    3.418082] [drm]   VGA-1
[    3.418084] [drm]   DDC: 0x65c0 0x65c0 0x65c4 0x65c4 0x65c8 0x65c8 0x65cc 0x65cc
[    3.418086] [drm]   Encoders:
[    3.418087] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
[    4.058552] [drm] fb mappable at 0xE0728000
[    4.058557] [drm] vram apper at 0xE0000000
[    4.058559] [drm] size 8294400
[    4.058560] [drm] fb depth is 24
[    4.058562] [drm]    pitch is 7680
[    4.058783] fbcon: radeondrmfb (fb0) is primary device
[    4.058955] radeon 0000:00:01.0: fb0: radeondrmfb frame buffer device
[    4.076169] [drm] Initialized radeon 2.43.0 20080528 for 0000:00:01.0 on minor 0
[ 4516.780974] radeon 0000:00:01.0: couldn't schedule ib
[ 4516.781062] [drm:radeon_uvd_suspend [radeon]] *ERROR* Error destroying UVD (-22)!
[ 4517.361939] [drm] PCIE GART of 2048M enabled (table at 0x0000000000324000).
[ 4517.362072] radeon 0000:00:01.0: WB enabled
[ 4517.362079] radeon 0000:00:01.0: fence driver on ring 0 use gpu addr 0x0000000020000c00 and cpu addr 0xffff880034e99c00
[ 4517.362082] radeon 0000:00:01.0: fence driver on ring 1 use gpu addr 0x0000000020000c04 and cpu addr 0xffff880034e99c04
[ 4517.362084] radeon 0000:00:01.0: fence driver on ring 2 use gpu addr 0x0000000020000c08 and cpu addr 0xffff880034e99c08
[ 4517.362086] radeon 0000:00:01.0: fence driver on ring 3 use gpu addr 0x0000000020000c0c and cpu addr 0xffff880034e99c0c
[ 4517.362089] radeon 0000:00:01.0: fence driver on ring 4 use gpu addr 0x0000000020000c10 and cpu addr 0xffff880034e99c10
[ 4517.362594] radeon 0000:00:01.0: fence driver on ring 5 use gpu addr 0x0000000000076c98 and cpu addr 0xffffc90001436c98
[ 4517.362786] radeon 0000:00:01.0: fence driver on ring 6 use gpu addr 0x0000000020000c18 and cpu addr 0xffff880034e99c18
[ 4517.362788] radeon 0000:00:01.0: fence driver on ring 7 use gpu addr 0x0000000020000c1c and cpu addr 0xffff880034e99c1c
[ 4517.365001] [drm] ring test on 0 succeeded in 3 usecs
[ 4517.365078] [drm] ring test on 1 succeeded in 2 usecs
[ 4517.365088] [drm] ring test on 2 succeeded in 2 usecs
[ 4517.365284] [drm] ring test on 3 succeeded in 3 usecs
[ 4517.365291] [drm] ring test on 4 succeeded in 3 usecs
[ 4517.391125] [drm] ring test on 5 succeeded in 1 usecs
[ 4517.391139] [drm] UVD initialized successfully.
[ 4517.500329] [drm] ring test on 6 succeeded in 5 usecs
[ 4517.500337] [drm] ring test on 7 succeeded in 2 usecs
[ 4517.500337] [drm] VCE initialized successfully.
[ 4517.500374] [drm] ib test on ring 0 succeeded in 0 usecs
[ 4517.998570] [drm] ib test on ring 1 succeeded in 0 usecs
[ 4518.498725] [drm] ib test on ring 2 succeeded in 0 usecs
[ 4518.498818] [drm] ib test on ring 3 succeeded in 0 usecs
[ 4518.498868] [drm] ib test on ring 4 succeeded in 0 usecs
[ 4518.998833] [drm] ib test on ring 5 succeeded
[ 4518.999381] [drm] ib test on ring 6 succeeded
[ 4518.999779] [drm] ib test on ring 7 succeeded
[16149.102375] [drm] PCIE GART of 2048M enabled (table at 0x0000000000324000).
[16149.102497] radeon 0000:00:01.0: WB enabled
[16149.102503] radeon 0000:00:01.0: fence driver on ring 0 use gpu addr 0x0000000020000c00 and cpu addr 0xffff880034e99c00
[16149.102506] radeon 0000:00:01.0: fence driver on ring 1 use gpu addr 0x0000000020000c04 and cpu addr 0xffff880034e99c04
[16149.102509] radeon 0000:00:01.0: fence driver on ring 2 use gpu addr 0x0000000020000c08 and cpu addr 0xffff880034e99c08
[16149.102511] radeon 0000:00:01.0: fence driver on ring 3 use gpu addr 0x0000000020000c0c and cpu addr 0xffff880034e99c0c
[16149.102513] radeon 0000:00:01.0: fence driver on ring 4 use gpu addr 0x0000000020000c10 and cpu addr 0xffff880034e99c10
[16149.102987] radeon 0000:00:01.0: fence driver on ring 5 use gpu addr 0x0000000000076c98 and cpu addr 0xffffc90001436c98
[16149.103185] radeon 0000:00:01.0: fence driver on ring 6 use gpu addr 0x0000000020000c18 and cpu addr 0xffff880034e99c18
[16149.103187] radeon 0000:00:01.0: fence driver on ring 7 use gpu addr 0x0000000020000c1c and cpu addr 0xffff880034e99c1c
[16149.105363] [drm] ring test on 0 succeeded in 3 usecs
[16149.105440] [drm] ring test on 1 succeeded in 2 usecs
[16149.105451] [drm] ring test on 2 succeeded in 2 usecs
[16149.105647] [drm] ring test on 3 succeeded in 3 usecs
[16149.105653] [drm] ring test on 4 succeeded in 3 usecs
[16149.131516] [drm] ring test on 5 succeeded in 1 usecs
[16149.131532] [drm] UVD initialized successfully.
[16149.240718] [drm] ring test on 6 succeeded in 6 usecs
[16149.240730] [drm] ring test on 7 succeeded in 2 usecs
[16149.240731] [drm] VCE initialized successfully.
[16149.240768] [drm] ib test on ring 0 succeeded in 0 usecs
[16149.240794] [drm] ib test on ring 1 succeeded in 0 usecs
[16149.738171] [drm] ib test on ring 2 succeeded in 0 usecs
[16149.738240] [drm] ib test on ring 3 succeeded in 0 usecs
[16149.738292] [drm] ib test on ring 4 succeeded in 0 usecs
[16150.238185] [drm] ib test on ring 5 succeeded
[16150.238741] [drm] ib test on ring 6 succeeded
[16150.239131] [drm] ib test on ring 7 succeeded
[22163.986445] [drm] PCIE GART of 2048M enabled (table at 0x0000000000324000).
[22163.986575] radeon 0000:00:01.0: WB enabled
[22163.986582] radeon 0000:00:01.0: fence driver on ring 0 use gpu addr 0x0000000020000c00 and cpu addr 0xffff880034e99c00
[22163.986585] radeon 0000:00:01.0: fence driver on ring 1 use gpu addr 0x0000000020000c04 and cpu addr 0xffff880034e99c04
[22163.986587] radeon 0000:00:01.0: fence driver on ring 2 use gpu addr 0x0000000020000c08 and cpu addr 0xffff880034e99c08
[22163.986590] radeon 0000:00:01.0: fence driver on ring 3 use gpu addr 0x0000000020000c0c and cpu addr 0xffff880034e99c0c
[22163.986592] radeon 0000:00:01.0: fence driver on ring 4 use gpu addr 0x0000000020000c10 and cpu addr 0xffff880034e99c10
[22163.987092] radeon 0000:00:01.0: fence driver on ring 5 use gpu addr 0x0000000000076c98 and cpu addr 0xffffc90001436c98
[22163.987283] radeon 0000:00:01.0: fence driver on ring 6 use gpu addr 0x0000000020000c18 and cpu addr 0xffff880034e99c18
[22163.987285] radeon 0000:00:01.0: fence driver on ring 7 use gpu addr 0x0000000020000c1c and cpu addr 0xffff880034e99c1c
[22163.989457] [drm] ring test on 0 succeeded in 2 usecs
[22163.989535] [drm] ring test on 1 succeeded in 2 usecs
[22163.989545] [drm] ring test on 2 succeeded in 2 usecs
[22163.989741] [drm] ring test on 3 succeeded in 3 usecs
[22163.989747] [drm] ring test on 4 succeeded in 3 usecs
[22164.015580] [drm] ring test on 5 succeeded in 1 usecs
[22164.015592] [drm] UVD initialized successfully.
[22164.124755] [drm] ring test on 6 succeeded in 7 usecs
[22164.124762] [drm] ring test on 7 succeeded in 2 usecs
[22164.124763] [drm] VCE initialized successfully.
[22164.124798] [drm] ib test on ring 0 succeeded in 0 usecs
[22164.623027] [drm] ib test on ring 1 succeeded in 0 usecs
[22165.123266] [drm] ib test on ring 2 succeeded in 0 usecs
[22165.123352] [drm] ib test on ring 3 succeeded in 0 usecs
[22165.123403] [drm] ib test on ring 4 succeeded in 0 usecs
[22165.623308] [drm] ib test on ring 5 succeeded
[22165.623822] [drm] ib test on ring 6 succeeded
[22165.624208] [drm] ib test on ring 7 succeeded
[30185.530444] [drm] PCIE GART of 2048M enabled (table at 0x0000000000324000).
[30185.530568] radeon 0000:00:01.0: WB enabled
[30185.530575] radeon 0000:00:01.0: fence driver on ring 0 use gpu addr 0x0000000020000c00 and cpu addr 0xffff880034e99c00
[30185.530578] radeon 0000:00:01.0: fence driver on ring 1 use gpu addr 0x0000000020000c04 and cpu addr 0xffff880034e99c04
[30185.530580] radeon 0000:00:01.0: fence driver on ring 2 use gpu addr 0x0000000020000c08 and cpu addr 0xffff880034e99c08
[30185.530583] radeon 0000:00:01.0: fence driver on ring 3 use gpu addr 0x0000000020000c0c and cpu addr 0xffff880034e99c0c
[30185.530585] radeon 0000:00:01.0: fence driver on ring 4 use gpu addr 0x0000000020000c10 and cpu addr 0xffff880034e99c10
[30185.531089] radeon 0000:00:01.0: fence driver on ring 5 use gpu addr 0x0000000000076c98 and cpu addr 0xffffc90001436c98
[30185.531286] radeon 0000:00:01.0: fence driver on ring 6 use gpu addr 0x0000000020000c18 and cpu addr 0xffff880034e99c18
[30185.531288] radeon 0000:00:01.0: fence driver on ring 7 use gpu addr 0x0000000020000c1c and cpu addr 0xffff880034e99c1c
[30185.533434] [drm] ring test on 0 succeeded in 2 usecs
[30185.533511] [drm] ring test on 1 succeeded in 2 usecs
[30185.533521] [drm] ring test on 2 succeeded in 2 usecs
[30185.533713] [drm] ring test on 3 succeeded in 3 usecs
[30185.533719] [drm] ring test on 4 succeeded in 3 usecs
[30185.559576] [drm] ring test on 5 succeeded in 1 usecs
[30185.559592] [drm] UVD initialized successfully.
[30185.668780] [drm] ring test on 6 succeeded in 6 usecs
[30185.668787] [drm] ring test on 7 succeeded in 2 usecs
[30185.668788] [drm] VCE initialized successfully.
[30185.668825] [drm] ib test on ring 0 succeeded in 0 usecs
[30186.166927] [drm] ib test on ring 1 succeeded in 0 usecs
[30186.667132] [drm] ib test on ring 2 succeeded in 0 usecs
[30186.667198] [drm] ib test on ring 3 succeeded in 0 usecs
[30186.667245] [drm] ib test on ring 4 succeeded in 0 usecs
[30187.167215] [drm] ib test on ring 5 succeeded
[30187.167769] [drm] ib test on ring 6 succeeded
[30187.168187] [drm] ib test on ring 7 succeeded
```

---

### Post by slobodan-covek on 2017-02-09
Bump

---

