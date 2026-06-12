---
title: "ubutnu is making weird sound until i pause and play the audio again"
date: 2021-10-09
forum: General Help
---

### Post by ronjjjg8885 on 2021-10-09
i recently resinstalled Ubuntu 20.04.3 LTS

when i play youtube on firefox it's making weird noises until i pause it. and when playing again the sound starts to be fine.

after a reboot..... the same thing.

i've a new computer and i can provide you with its specifications if you need.

is that a known bug?

i had ubuntu on the same machine with no such problems.

thanks!!

---

### Post by ajgreeny on 2021-10-09
Yes please; do provide us with the hardware by showing us the output of terminal command ```
inxi -Fzx
```
Please use **Code-Tags** for terminal output as it makes that output much more easily read and understood, formatting the text as seen in terminal, not as plain text when it is copied and pasted. See my signature below for a **How-to**

---

### Post by ronjjjg8885 on 2021-10-09
```
System:
  Kernel: 5.11.0-37-generic x86_64 bits: 64 compiler: N/A 
  Desktop: Gnome 3.36.9 Distro: Ubuntu 20.04.3 LTS (Focal Fossa) 
Machine:
  Type: Desktop System: Gigabyte product: B460MDS3H v: N/A serial: <filter> 
  Mobo: Gigabyte model: B460M DS3H v: x.x serial: <filter> 
  UEFI: American Megatrends v: F5d date: 03/18/2021 
Battery:
  Device-1: hidpp_battery_0 model: Logitech Wireless Keyboard 
  charge: 55% (should be ignored) status: Discharging 
CPU:
  Topology: 6-Core model: Intel Core i5-10600KF bits: 64 type: MT MCP 
  arch: N/A L2 cache: 12.0 MiB 
  flags: avx avx2 lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx 
  bogomips: 98397 
  Speed: 800 MHz min/max: 800/4800 MHz Core speeds (MHz): 1: 800 2: 800 
  3: 800 4: 800 5: 800 6: 800 7: 800 8: 800 9: 800 10: 800 11: 800 12: 800 
Graphics:
  Device-1: NVIDIA TU116 [GeForce GTX 1650 SUPER] vendor: Gigabyte 
  driver: nvidia v: 470.63.01 bus ID: 01:00.0 
  Display: x11 server: X.Org 1.20.11 driver: nvidia 
  unloaded: fbdev,modesetting,nouveau,vesa resolution: 1920x1080~60Hz 
  OpenGL: renderer: NVIDIA GeForce GTX 1650 SUPER/PCIe/SSE2 
  v: 4.6.0 NVIDIA 470.63.01 direct render: Yes 
Audio:
  Device-1: Intel vendor: Gigabyte driver: snd_hda_intel v: kernel 
  bus ID: 00:1f.3 
  Device-2: NVIDIA TU116 High Definition Audio vendor: Gigabyte 
  driver: snd_hda_intel v: kernel bus ID: 01:00.1 
  Sound Server: ALSA v: k5.11.0-37-generic 
Network:
  Device-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet 
  vendor: Gigabyte driver: r8169 v: kernel port: 3000 bus ID: 04:00.0 
  IF: enp4s0 state: up speed: 1000 Mbps duplex: full mac: <filter> 
  IF-ID-1: virbr0 state: down mac: <filter> 
  IF-ID-2: virbr0-nic state: down mac: <filter> 
Drives:
  Local Storage: total: 2.27 TiB used: 58.00 GiB (2.5%) 
  ID-1: /dev/nvme0n1 vendor: Samsung model: SSD 980 500GB size: 465.76 GiB 
  ID-2: /dev/sda vendor: Seagate model: ST2000DM008-2FR102 size: 1.82 TiB 
  temp: 41 C 
Partition:
  ID-1: / size: 456.96 GiB used: 57.99 GiB (12.7%) fs: ext4 
  dev: /dev/nvme0n1p2 
Sensors:
  System Temperatures: cpu: 16.8 C mobo: 16.8 C gpu: nvidia temp: 49 C 
  Fan Speeds (RPM): N/A gpu: nvidia fan: 0% 
Info:
  Processes: 378 Uptime: 3m Memory: 15.56 GiB used: 2.74 GiB (17.6%) 
  Init: systemd runlevel: 5 Compilers: gcc: 9.3.0 Shell: bash v: 5.0.17 
  inxi: 3.0.38
```

is that what you needed?
i've installed ```
inxi
``` for doing so

TNX

---

### Post by ronjjjg8885 on 2021-10-10
i will try to re install ubuntu....
thanks anyway

---

### Post by mIk3_08 on 2021-10-10
> **ronjjjg8885 said:**
> i will try to re install ubuntu....
thanks anyway
can you still show us your previous system logs during the moment you encounter the issue? 
```
cat /var/log/syslog
```
then paste it in ubuntu paste bin and
```
sudo dmesg
```
regards.

---

### Post by ronjjjg8885 on 2021-10-12
thank you all
can't check your suggestions at the moment because i'm not able to use my ubuntu at all....
i will see if i can figure it out and tell you later....

:)

---

### Post by mIk3_08 on 2021-10-12
> **ronjjjg8885 said:**
> thank you all
can't check your suggestions at the moment because i'm not able to use my ubuntu at all....
i will see if i can figure it out and tell you later....

:)

Sure. Just update us if need some help. The Ubuntu Forum community are willing to help you. If you have another concern aside of this issue don't hesitate to add a new thread if needed. Good Luck and Welcome to Linux World.

---

