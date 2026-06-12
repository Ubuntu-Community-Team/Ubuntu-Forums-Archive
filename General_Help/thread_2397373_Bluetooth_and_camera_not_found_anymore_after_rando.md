---
title: "Bluetooth and camera not found anymore after random time"
date: 2018-07-28
forum: General Help
---

### Post by invisibleshadowghost on 2018-07-28
Hi guys,

  Ihave a completely new XPS 9370 from Dell, which came with Ubuntu 16.04 pre-installed.
Bluetooth and the camera work fine on startup (I can connect to my wireless mouse and it works fie, cheese also works). But after a random period of time after the start (not explicit after a suspend etc., feels different every time) the camera and Bluetooth stop working (It says no Bluetooth found and Cheese says, that no device is found. Also ls -ltrh /dev/video* results in no such file or directory).

I tried with Ubuntu 16.04 and 18.04 trying the 4.4 and 4.15 kernel line. The error was always the same.
Interestingly, when the problem has occurred, lsusb gives me a very minimalistic output like

```

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

If everything is fine the output is
```
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 0489:e0a2 Foxconn / Hon Hai 
Bus 001 Device 002: ID 0bda:58f4 Realtek Semiconductor Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

And that is the dmesg output directly after disconnect
```

[49330.103739] xhci_hcd 0000:00:14.0: xHC is not running.
[49330.138905] xhci_hcd 0000:00:14.0: xHCI host controller not responding, assume dead
[49330.138914] xhci_hcd 0000:00:14.0: HC died; cleaning up
[49330.223321] usb 1-5: USB disconnect, device number 2
[49330.223861] usb 1-7: USB disconnect, device number 3

```

Here is the inxi output, if that helps
```
System:    Host: xps-9370 Kernel: 4.15.0-29-generic x86_64 bits: 64 Desktop: Gnome 3.28.2
           Distro: Ubuntu 18.04.1 LTS
Machine:   Device: laptop System: Dell product: XPS 13 9370 serial: N/A
           Mobo: Dell model: 0F6P3V v: A00 serial: N/A UEFI: Dell v: 1.4.0 date: 05/25/2018
Battery    BAT0: charge: 31.4 Wh 61.2% condition: 51.2/52.0 Wh (99%)
CPU:       Quad core Intel Core i7-8550U (-MT-MCP-) cache: 8192 KB
           clock speeds: max: 4000 MHz 1: 2300 MHz 2: 2299 MHz 3: 2300 MHz 4: 2300 MHz 5: 2300 MHz 6: 2299 MHz
           7: 2300 MHz 8: 2300 MHz
Graphics:  Card: Intel UHD Graphics 620
           Display Server: x11 (X.Org 1.19.6 ) drivers: intel (unloaded: modesetting,fbdev,vesa)
           Resolution: 1920x1080@60.03hz
           OpenGL: renderer: Mesa DRI Intel UHD Graphics 620 (Kabylake GT2) version: 4.5 Mesa 18.0.5
Audio:     Card Intel Sunrise Point-LP HD Audio driver: snd_hda_intel Sound: ALSA v: k4.15.0-29-generic
Network:   Card: Qualcomm Atheros QCA6174 802.11ac Wireless Network Adapter driver: ath10k_pci
           IF: wlp2s0 state: up mac: <filter>
Drives:    HDD Total Size: 512.1GB (24.8% used)
           ID-1: /dev/nvme0n1 model: PM981_NVMe_Samsung_512GB size: 512.1GB
Partition: ID-1: / size: 436G used: 89G (22%) fs: ext4 dev: /dev/nvme0n1p3
           ID-2: swap-1 size: 33.76GB used: 0.00GB (0%) fs: swap dev: /dev/nvme0n1p4
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 47.5C mobo: N/A
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 309 Uptime: 8:15 Memory: 4066.7/15757.1MB Client: Shell (bash) inxi: 2.3.56 


```

Has anybody an idea and can help me?
Is there maybe a way to "restart" the devices/reload the modules or driver, which would provide a fix for now?

Best regards

---

### Post by asynec on 2019-01-27
Were you ever able to resolve this issue? I am having the exact same issue on a Dell XPS 9575

---

