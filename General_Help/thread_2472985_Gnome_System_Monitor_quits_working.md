---
title: "Gnome System Monitor quits working"
date: 2022-03-19
forum: General Help
---

### Post by psychohermit on 2022-03-19
Greeting folks,  Gnome system monitor quits working.  I removed and reinstalled it and it worked, but later it quit working again.  Any suggestions would be welcome. I'm running ubuntu 20.04.3 on an HP ENVY Touchsmart notebook.  ```
 glenn@LinuxBox:~$ inxi -F System:   Host: LinuxBox Kernel: 5.13.0-35-generic x86_64 bits: 64    Desktop: Gnome 3.36.9 Distro: Ubuntu 20.04.4 LTS (Focal Fossa)  Machine:   Type: Laptop System: Hewlett-Packard product: HP ENVY m6 Notebook PC    v: 097C100022405F10000320100 serial:     Mobo: Hewlett-Packard model: 222C v: KBC Version 64.06    serial:  UEFI: Insyde v: F.23 date: 07/26/2016  Battery:   ID-1: BAT0 charge: 46.1 Wh condition: 45.2/45.2 Wh (100%)  CPU:   Topology: Quad Core model: AMD A10-5750M APU with Radeon HD Graphics    bits: 64 type: MCP L2 cache: 2048 KiB    Speed: 1335 MHz min/max: 1400/2500 MHz Core speeds (MHz): 1: 1348 2: 1364    3: 1459 4: 1408  Graphics:   Device-1: AMD Richland [Radeon HD 8650G] driver: radeon v: kernel    Display: x11 server: X.Org 1.20.13 driver: radeon    resolution: 1366x768~60Hz    OpenGL: renderer: AMD ARUBA (DRM 2.50.0 / 5.13.0-35-generic LLVM 12.0.0)    v: 4.3 Mesa 21.2.6  Audio:   Device-1: AMD Trinity HDMI Audio driver: snd_hda_intel    Device-2: AMD FCH Azalia driver: snd_hda_intel    Sound Server: ALSA v: k5.13.0-35-generic  Network:   Device-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet    driver: r8169    IF: eno1 state: down mac: c4:34:6b:01:b6:65    Device-2: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter    driver: ath9k    IF: wlo1 state: up mac: b8:ee:65:3d:3d:5e    Device-3: Qualcomm Atheros type: USB driver: btusb  Drives:   Local Storage: total: 953.87 GiB used: 13.39 GiB (1.4%)    ID-1: /dev/sda vendor: SanDisk model: SDSSDH3 1T02 size: 953.87 GiB  Partition:   ID-1: / size: 627.09 GiB used: 9.34 GiB (1.5%) fs: ext4 dev: /dev/sda6    ID-2: /home size: 27.38 GiB used: 3.78 GiB (13.8%) fs: ext4 dev: /dev/sda5    ID-3: swap-1 size: 7.81 GiB used: 248.8 MiB (3.1%) fs: swap dev: /dev/sda7  Sensors:   System Temperatures: cpu: 42.2 C mobo: 0.0 C gpu: radeon temp: 41 C    Fan Speeds (RPM): N/A  Info:   Processes: 256 Uptime: 5h 46m Memory: 5.02 GiB used: 3.44 GiB (68.6%)    Shell: bash inxi: 3.0.38 
```  Thanks in advance, --glenn

---

### Post by #&amp;thj^% on 2022-03-19
Since we/I don't know how you installed it, snap version was always to blame in my useage.
```
snap remove gnome-system-monitor
sudo apt install gnome-system-monitor
```
if still not consistent, please show this:
```
apt policy gnome-system-monitor

```

---

### Post by psychohermit on 2022-03-19
Thanks, I now have the apt version instead of the snap.  Hopefully it will keep working.  Thanks, --glenn

---

### Post by #&amp;thj^% on 2022-03-19
It should, but keep us posted. :)

---

### Post by psychohermit on 2022-03-19
Ok, thank you.  --glenn

---

