---
title: "Why is my computer so slow after Lubuntu 20.04 install?"
date: 2020-06-18
forum: General Help
---

### Post by rdh61 on 2020-06-18
I used Lubuntu 18.04 up until a couple of months ago, when I freshly installed Lubuntu 20.04. I notice it is considerably slower. For example, start up takes ages after logging in:

```
robert@roberts-work-laptop:~$ systemd-analyze
Startup finished in 20.390s (firmware) + 13.662s (loader) + 8.362s (kernel) + 1min 3.112s (userspace) = 1min 45.528s 
graphical.target reached after 1min 3.088s in userspace
robert@roberts-work-laptop:~$ 
```

Also, other applications like LibreOffice take an age (up to a minute) to open.

Here are my specs:

```
robert@roberts-work-laptop:~$ inxi -Fzx
System:
  Kernel: 5.4.0-31-generic x86_64 bits: 64 compiler: gcc v: 9.3.0 
  Desktop: LXQt 0.14.1 Distro: Ubuntu 20.04 LTS (Focal Fossa) 
Machine:
  Type: Laptop System: LENOVO product: 37613JG v: Lenovo B590 
  serial: <filter> 
  Mobo: LENOVO model: 37613JG v: 31900003 Std serial: <filter> 
  UEFI: LENOVO v: H9ET74WW(1.11) date: 06/26/2013 
Battery:
  ID-1: BAT0 charge: 35.1 Wh condition: 35.2/42.8 Wh (82%) 
  model: SMP 45N1045 status: Unknown 
  Device-1: hidpp_battery_0 model: Logitech Wireless Mouse M185 
  charge: 55% (should be ignored) status: Discharging 
CPU:
  Topology: Dual Core model: Intel Celeron 1005M bits: 64 type: MCP 
  arch: Ivy Bridge rev: 9 L2 cache: 2048 KiB 
  flags: lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx bogomips: 7582 
  Speed: 1198 MHz min/max: 1200/1900 MHz Core speeds (MHz): 1: 1197 
  2: 1197 
Graphics:
  Device-1: Intel 3rd Gen Core processor Graphics vendor: Lenovo 
  driver: i915 v: kernel bus ID: 00:02.0 
  Display: x11 server: X.Org 1.20.8 driver: modesetting 
  unloaded: fbdev,vesa resolution: 1366x768~60Hz 
  OpenGL: renderer: Mesa DRI Intel HD Graphics 2500 (IVB GT1) 
  v: 4.2 Mesa 20.0.4 direct render: Yes 
Audio:
  Device-1: Intel 7 Series/C216 Family High Definition Audio 
  vendor: Lenovo driver: snd_hda_intel v: kernel bus ID: 00:1b.0 
  Sound Server: ALSA v: k5.4.0-31-generic 
Network:
  Device-1: Broadcom and subsidiaries BCM43142 802.11b/g/n vendor: Lenovo 
  driver: wl v: kernel port: efa0 bus ID: 02:00.0 
  IF: wlp2s0 state: up mac: <filter> 
  Device-2: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet 
  vendor: Lenovo driver: r8169 v: kernel port: 2000 bus ID: 03:00.0 
  IF: enp3s0 state: down mac: <filter> 
  IF-ID-1: br-031ef41d3be2 state: up speed: N/A duplex: N/A mac: <filter> 
  IF-ID-2: docker0 state: down mac: <filter> 
  IF-ID-3: veth10dc389 state: up speed: 10000 Mbps duplex: full 
  mac: <filter> 
  IF-ID-4: veth9661eb3 state: up speed: 10000 Mbps duplex: full 
  mac: <filter> 
Drives:
  Local Storage: total: 313.00 GiB used: 51.81 GiB (16.6%) 
  ID-1: /dev/sda vendor: Seagate model: ST320LT012-9WS14C 
  size: 298.09 GiB temp: 35 C 
  ID-2: /dev/sdc type: USB vendor: Verbatim model: STORE N GO 
  size: 14.91 GiB 
Partition:
  ID-1: / size: 126.53 GiB used: 49.42 GiB (39.1%) fs: ext4 
  dev: /dev/sda6 
Sensors:
  System Temperatures: cpu: 40.0 C mobo: 31.0 C 
  Fan Speeds (RPM): cpu: 0 
Info:
  Processes: 195 Uptime: 1h 07m Memory: 3.70 GiB used: 921.7 MiB (24.3%) 
  Init: systemd runlevel: 5 Compilers: gcc: 9.3.0 Shell: bash v: 5.0.16 
  inxi: 3.0.38 
robert@roberts-work-laptop:~$
```

Somebody on another thread of more general discussion suggested that since my specs should be able to handle the Lxqt desktop "something must be happening" in the background that could potentially be resolved. Any ideas?

---

### Post by Yellow Pasque on 2020-06-18
Figure out what is making it take so long to boot:
```
systemd-analyze blame
```

---

### Post by rdh61 on 2020-06-19
Here is today's. Looks like docker is a big contributor. In that case I'll have to live with it...

```
robert@roberts-work-laptop:~$ systemd-analyze
Startup finished in 20.772s (firmware) + 12.502s (loader) + 8.314s (kernel) + 1min 10.474s (userspace) = 1min 52.063s 
graphical.target reached after 1min 10.453s in userspace
robert@roberts-work-laptop:~$ systemd-analyze blame
31.645s docker.service                                       
29.046s man-db.service                                       
18.649s snapd.service                                        
13.671s udisks2.service                                      
12.744s NetworkManager-wait-online.service                   
10.734s dev-sda6.device                                      
10.286s accounts-daemon.service                              
 7.601s systemd-journal-flush.service                        
 7.278s networkd-dispatcher.service                          
 7.268s polkit.service                                       
 6.655s ModemManager.service                                 
 6.471s NetworkManager.service                               
 6.444s avahi-daemon.service                                 
 6.437s bluetooth.service                                    
 5.822s thermald.service                                     
lines 1-15
```

---

### Post by Yellow Pasque on 2020-06-19
Ah, so it looks like everything is taking longer to start than it should.
I don't know where I'd look next. Maybe look at SMART info on hard disk (if applicable), or skim through dmesg.

---

