---
title: "Ubuntu 20.04 freeze"
date: 2020-07-23
forum: General Help
---

### Post by gabbello on 2020-07-23
Hello,

Sometimes my ubuntu freeze completely and it can't even by accessed over ssh. Most of the times it requires a restart, and only once it seems I captured  segfault (?) in syslog, see below:

I can't consitently link this to some specific action, but it seems to be linked to some video activity (eg. start vlc, access a webpage with a video player, share screen via hanghouts/zoom), maybe it is smth realted to video card drivers?

[https://pastebin.com/KGrJEmKR](https://pastebin.com/KGrJEmKR)

---

### Post by kc1di on 2020-07-24
Can you give us a little more info on your system?  which video card does it use?
if you do not know enter this command in a terminal and post the output.
```
sudo lshw -C video
```

Also I would suggest you install inxi  with this command ```
sudo apt install inxi
``` It is a good diagnostic tool. The run the command ```
inxi -Fxz
``` and post it's output also.

---

### Post by gabbello on 2020-07-24
Thank you,

Here you go:

```
sudo lshw -C video
[sudo] password for olga: 
  *-display                 
       description: VGA compatible controller
       product: Skylake GT2 [HD Graphics 520]
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: pciexpress msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:129 memory:92000000-92ffffff memory:a0000000-afffffff ioport:5000(size=64) memory:c0000-dffff
  *-display
       description: 3D controller
       product: GK208BM [GeForce 920M]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:132 memory:93000000-93ffffff memory:80000000-8fffffff memory:90000000-91ffffff ioport:4000(size=128) memory:94080000-940fffff

```


```
inxi -Fxz
System:    Kernel: 5.4.0-40-generic x86_64 bits: 64 compiler: gcc v: 9.3.0 Desktop: Gnome 3.36.3 
           Distro: Ubuntu 20.04 LTS (Focal Fossa) 
Machine:   Type: Laptop System: LENOVO product: 80Q2 v: Lenovo ideapad 500S-13ISK serial: <filter> 
           Mobo: LENOVO model: Lenovo ideapad 5 v: No DPK serial: <filter> UEFI: LENOVO v: DCCN18WW(V1.05) date: 08/28/2015 
Battery:   ID-1: BAT1 charge: 24.4 Wh condition: 24.4/33.3 Wh (73%) model: LENOVO PABAS0241231 status: Full 
           Device-1: hidpp_battery_0 model: Logitech Wireless Mouse M235/238/317 charge: 55% (should be ignored) 
           status: Discharging 
CPU:       Topology: Dual Core model: Intel Core i5-6200U bits: 64 type: MT MCP arch: Skylake rev: 3 L2 cache: 3072 KiB 
           flags: avx avx2 lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx bogomips: 19200 
           Speed: 1313 MHz min/max: 400/2800 MHz Core speeds (MHz): 1: 1313 2: 1218 3: 1087 4: 1122 
Graphics:  Device-1: Intel Skylake GT2 [HD Graphics 520] vendor: Lenovo driver: i915 v: kernel bus ID: 00:02.0 
           Device-2: NVIDIA GK208BM [GeForce 920M] vendor: Lenovo driver: nvidia v: 440.100 bus ID: 01:00.0 
           Display: x11 server: X.Org 1.20.8 driver: modesetting,nvidia unloaded: fbdev,nouveau,vesa 
           resolution: 1920x1080~60Hz 
           OpenGL: renderer: GeForce 920M/PCIe/SSE2 v: 4.6.0 NVIDIA 440.100 direct render: Yes 
Audio:     Device-1: Intel Sunrise Point-LP HD Audio vendor: Lenovo driver: snd_hda_intel v: kernel bus ID: 00:1f.3 
           Device-2: NVIDIA GK208 HDMI/DP Audio vendor: Lenovo driver: snd_hda_intel v: kernel bus ID: 01:00.1 
           Sound Server: ALSA v: k5.4.0-40-generic 
Network:   Device-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet vendor: Lenovo driver: r8169 v: kernel port: 3000 
           bus ID: 02:00.0 
           IF: enp2s0 state: up speed: 1000 Mbps duplex: full mac: <filter> 
           Device-2: Qualcomm Atheros QCA9377 802.11ac Wireless Network Adapter vendor: Lenovo driver: ath10k_pci v: kernel 
           port: 3000 bus ID: 03:00.0 
           IF: wlp3s0 state: down mac: <filter> 
           Device-3: Qualcomm Atheros type: USB driver: btusb bus ID: 1-7:5 
Drives:    Local Storage: total: 447.13 GiB used: 37.13 GiB (8.3%) 
           ID-1: /dev/sda vendor: Kingston model: SA400S37480G size: 447.13 GiB temp: 37 C 
Partition: ID-1: / size: 438.62 GiB used: 37.13 GiB (8.5%) fs: ext4 dev: /dev/sda2 
Sensors:   System Temperatures: cpu: 56.0 C mobo: N/A gpu: nvidia temp: 55 C 
           Fan Speeds (RPM): N/A 
Info:      Processes: 310 Uptime: 22h 59m Memory: 7.64 GiB used: 6.00 GiB (78.5%) Init: systemd runlevel: 5 Compilers: 
           gcc: 9.3.0 Shell: bash v: 5.0.17 inxi: 3.0.38 


```

---

### Post by kc1di on 2020-07-24
Does the freeze happen when your using the Nvidia side of the card?  
Nvidia can be problematic in this way.  You may need to change the driver for your card. 

This [article]("https://linuxconfig.org/how-to-install-the-nvidia-drivers-on-ubuntu-20-04-focal-fossa-linux") may be of help

---

### Post by gabbello on 2020-07-24
well first of all I'm not sure it is related to video card, it might also be related to audio also. 
I had some issues with my headphones mic not being detected when headset is plugged in. 
I played a bit with: /etc/modprobe.d/alsa-base.conf trying to fix it. Basically adding:
options snd-hda-intel model=alc294-lenovo-mic

Now I had a new freez3e at 15:28:03:

[https://pastebin.com/axFdfC27](https://pastebin.com/axFdfC27)


And I see this line: 
Jul 24 15:29:07 olga-Lenovo-ideapad-500S-13ISK pulseaudio[49455]: Most likely this is a bug in the ALSA driver 'snd_hda_intel'. 


I commented "options snd-hda-intel model=alc294-lenovo-mic", anyway it doesn't seem to do any good, I will see if it will fix it or not.

---

### Post by kc1di on 2020-07-24
I would not rule out the video card, hope you find the answer.

---

### Post by gabbello on 2020-07-24
Yes, sure it might be video, but I don't knoweven from where to start.

> Does the freeze happen when your using the Nvidia side of the card?  
I'm not sure what you meant here (or how I could check this). Last freeze was while using slack without really trying to play any video at all.

---

### Post by kc1di on 2020-07-24
You can issue this command in the terminal ```
inxi -G
```  The card being used will be the one with driver and gl info supplied. 
Similar to this ```
[inxi -G
Graphics:
  Device-1: Intel HD Graphics 5500 driver: i915 v: kernel 
  Display: x11 server: X.Org 1.20.8 driver: i915 resolution: 1600x900~60Hz 
  OpenGL: renderer: Mesa Intel HD Graphics 5500 (BDW GT2) v: 4.6 Mesa 20.0.8 
```
The one not currently in use will not have any driver and gl rendering info.

How did you install the Nvidia driver your using?
According to the last inxi run you did it was the Nvidia card being used with the 440 driver.  Some have said they have had trouble with that driver and some Nvidia cards so I would try a different driver. or different kernel.

I don't currently have any Nvidia cards available here so can't test it out.

---

