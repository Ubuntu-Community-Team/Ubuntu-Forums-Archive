---
title: "Audio/Sounds Stops after 15 mins"
date: 2018-12-16
forum: General Help
---

### Post by Quarkrad on 2018-12-16
Running up to date 18.04.  Recently install set of USB speakers - they stop working after 15 mins, consistently; I can get them working again by pressing the keyboard volume button.  A suggestion to diagnose this was to run **dmesg | tail** after the speakers stop working. The output is:

```
liz@lizubuntu:~$ dmesg | tail
[  474.456315] usb 2-1.6: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  474.456317] usb 2-1.6: Product: ENVY 4500 series
[  474.456319] usb 2-1.6: Manufacturer: HP
[  474.456321] usb 2-1.6: SerialNumber: CN48F151GM05X4
[  474.760373] usblp 2-1.6:1.1: usblp0: USB Bidirectional printer dev 11 if 1 alt 0 proto 2 vid 0x03F0 pid 0xC511
[  474.761167] usbcore: registered new interface driver usblp
[  479.861389] usblp0: removed
[  479.872373] usblp 2-1.6:1.1: usblp0: USB Bidirectional printer dev 11 if 1 alt 0 proto 2 vid 0x03F0 pid 0xC511
[  545.390998] usblp0: removed
[  601.100542] usb 2-1.6: USB disconnect, device number 11
liz@lizubuntu:~$ 

```

During the 15min I scanned a document which I'm guessing is why there are references to the Envy 4500 above.  Any further suggestions appreciated - what is causing device number 11 to disconnect (assuming device 11 are my speakers).

---

### Post by Quarkrad on 2018-12-16
I forgot a possible important statement.  I have two machines (each running 18.04) sharing a monitor and mouse via a kvm switch - said speakers are connected to the kvm switch (connected via stereo jack).  On this other machine the sound also stops after 15mins and can be re-activated by pressing the keyboard volume control. The **dmesg | tail** output on the second machine is:

```
dad@dadubuntu:~$ dmesg | tail
[  254.235704] [UFW BLOCK] IN=enp2s0 OUT= MAC=01:00:5e:00:00:fb:40:9b:cd:9a:1d:2d:08:00 SRC=192.168.1.1 DST=224.0.0.251 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=884 PROTO=2 
[  378.667737] [UFW BLOCK] IN=enp2s0 OUT= MAC=01:00:5e:00:00:01:40:9b:cd:9a:1d:2d:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=58813 PROTO=2 
[  502.716253] [UFW BLOCK] IN=enp2s0 OUT= MAC=01:00:5e:00:00:01:40:9b:cd:9a:1d:2d:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=58814 PROTO=2 
[  503.723901] [UFW BLOCK] IN=enp2s0 OUT= MAC=01:00:5e:00:00:fb:40:9b:cd:9a:1d:2d:08:00 SRC=192.168.1.1 DST=224.0.0.251 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=885 PROTO=2 
[  589.592995] usb 1-5: reset high-speed USB device number 3 using xhci_hcd
[  627.951835] [UFW BLOCK] IN=enp2s0 OUT= MAC=01:00:5e:00:00:01:40:9b:cd:9a:1d:2d:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=58815 PROTO=2 
[  642.297266] usb 1-5: reset high-speed USB device number 3 using xhci_hcd
[  752.080002] [UFW BLOCK] IN=enp2s0 OUT= MAC=01:00:5e:00:00:01:40:9b:cd:9a:1d:2d:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=58816 PROTO=2 
[  877.315654] [UFW BLOCK] IN=enp2s0 OUT= MAC=01:00:5e:00:00:01:40:9b:cd:9a:1d:2d:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=58817 PROTO=2 
[  877.315889] [UFW BLOCK] IN=enp2s0 OUT= MAC=01:00:5e:00:00:fb:40:9b:cd:9a:1d:2d:08:00 SRC=192.168.1.1 DST=224.0.0.251 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=886 PROTO=2 
dad@dadubuntu:~$ 


```

---

### Post by Quarkrad on 2018-12-16
Sorry, sorry, sorry - having a major senior moment.  These speakers are NOT usb - they are mains powered and have a standard sterio jack that plugs into the sound output.  (Creative Labs a250).

---

### Post by CatKiller on 2018-12-16
It sounds to me like the sound card is being turned off as a power saving measure, but then not being re-enabled when you start to play sounds again. It's power management that I'd start to look at first.

---

### Post by Quarkrad on 2018-12-16
Sorted - it appears my speakers adhere to **ErP regulations**. "...In keeping with ErP (Energy-related Products) regulations, your Creative speaker will go into Standby mode if it doesn&#8217;t detect audio input (via aux-in/line-in) after a specific amount of time....".  It appears the speakers have a set to a threshold level - a solution is to turn up the volume.  I guess other speaker make/models could also adhere to this regulation.  I have turned up the volume (too loud - just testing) and the speakers did not turn off.

---

### Post by CatKiller on 2018-12-16
Glad to hear you got to the bottom of it.

---

