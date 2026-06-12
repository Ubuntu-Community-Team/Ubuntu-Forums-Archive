---
title: "mouse, keyboard and pen input lag, while I am sharing my screen using skype,zoom etc."
date: 2019-12-19
forum: General Help
---

### Post by sameepvicky on 2019-12-19
Hi! I have an issue of mouse, keyboard and pen input lag, while I am sharing my screen using skype/zoom/etc., under Mint 19.2 Cinnamon (all ubuntu based os), on this machine Lenovo Aio 330.

Machine Specs:

System:    Host: LenovoCmintSameep Kernel: 5.0.0-31-generic x86_64 bits: 64 compiler: gcc v: 7.4.0 Desktop: Cinnamon 4.2.4 
           Distro: Linux Mint 19.2 Tina base: Ubuntu 18.04 bionic 
Machine:   Type: Desktop System: LENOVO product: F0D7001AIN v: ideacentre AIO 330-20IGM serial: <filter> 
           Mobo: LENOVO model: 36ED serial: <filter> UEFI [Legacy]: LENOVO v: O3SKT44A date: 09/05/2019 
CPU:       Topology: Dual Core model: Intel Celeron J4005 bits: 64 type: MCP arch: Goldmont Plus rev: 1 L2 cache: 4096 KiB 
           flags: lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx bogomips: 7987 
           Speed: 1325 MHz min/max: 800/2700 MHz Core speeds (MHz): 1: 1017 2: 959 
Graphics:  Device-1: Intel vendor: Lenovo driver: i915 v: kernel bus ID: 00:02.0 
           Display: x11 server: X.Org 1.19.6 driver: modesetting unloaded: fbdev,vesa resolution: 1440x900~60Hz 
           OpenGL: renderer: Mesa DRI Intel UHD Graphics 600 (Geminilake 2x6) v: 4.5 Mesa 19.0.8 direct render: Yes 
Audio:     Device-1: Intel vendor: Lenovo driver: snd_hda_intel v: kernel bus ID: 00:0e.0 
           Sound Server: ALSA v: k5.0.0-31-generic 
Network:   Device-1: Realtek RTL8821CE 802.11ac PCIe Wireless Network Adapter vendor: Lenovo driver: rtl8821ce v: N/A 
           port: e000 bus ID: 02:00.0 
           IF: wlp2s0 state: down mac: <filter> 
           Device-2: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet vendor: Lenovo driver: r8169 v: kernel port: d000 
           bus ID: 03:00.0 
           IF: enp3s0 state: up speed: 100 Mbps duplex: full mac: <filter> 
Drives:    Local Storage: total: 946.36 GiB used: 26.66 GiB (2.8%) 
           ID-1: /dev/sda vendor: Seagate model: ST1000LM035-1RK172 size: 931.51 GiB 
           ID-2: /dev/sdb type: USB vendor: Verbatim model: STORE N GO size: 14.84 GiB 
Partition: ID-1: / size: 29.40 GiB used: 8.27 GiB (28.1%) fs: ext4 dev: /dev/sda3 
           ID-2: swap-1 size: 6.00 GiB used: 0 KiB (0.0%) fs: swap dev: /dev/sda5 
Sensors:   System Temperatures: cpu: 40.0 C mobo: N/A 
           Fan Speeds (RPM): N/A 
Info:      Processes: 202 Uptime: 14m Memory: 3.70 GiB used: 1.48 GiB (40.1%) Init: systemd runlevel: 5 Compilers: gcc: 7.4.0 
           Shell: bash v: 4.4.20 inxi: 3.0.32

---

### Post by sameepvicky on 2019-12-24
[COLOR=#000000][FONT=&quot]I somehow fixed it as a workaround. Still looking for a better solution, using modesetting driver.[/FONT][/COLOR]

I referred to this page and the suggestion by Niklas:
[https://askubuntu.com/questions/1062389/how-do-i-change-driver-for-intel-graphics-and-what-options-are-available](https://askubuntu.com/questions/1062389/how-do-i-change-driver-for-intel-graphics-and-what-options-are-available)


and created a file 20-intel.conf as:
/usr/share/X11/xorg.conf.d/20-intel.conf


And put the following contents and then restarted my system. This fixed the problem.


Section "Device"
    Identifier  "Intel Graphics"
        Driver      "intel"
    Option      "AccelMethod" "sna"
    Option      "TearFree" "true"
    Option      "DRI" "3"
EndSection




----
By doing so I am using a workaround of using intel driver instead of 'modesetting' driver which is preferred. 


Athough this problem is solved, I would still like to know how can we fix it using the modesetting driver.


Its not urgent for me, but its going to be better for me in future.

---

### Post by mörgæs on 2019-12-25
You could try live booting one of the 19.10 Buntus to see if the newer drivers make a difference. Your hardware is so new that old Ubuntu releases are not necessarily a good option.

---

