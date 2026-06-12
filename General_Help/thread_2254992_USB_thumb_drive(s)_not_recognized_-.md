---
title: "USB thumb drive(s) not recognized - ?"
date: 2014-12-01
forum: General Help
---

### Post by michael-piziak on 2014-12-01
I put 3 usb thump drives in my sisters 14.04 LTS system; however, none will pop up on the Launcher.

Any idea why not ?

The only other information is that I can provide is that there is a brief message upon boot up that thre is a hotplug firmware problem.

Also, I have 2 Gravis Gamepad game controllers that are both recognized in the two usb slots on the front, but the thumb drives just won't show up anywhere.

Update:  I plugged an external USB Seagate hard drive in and it is recognized.  But usb sticks/thumb drives still not recognized.

---

### Post by nerdtron on 2014-12-01
Plug in any of the unrecognized usb sticks and post the output of the command here:
```
 dmesg | tail -n 40 
```

---

### Post by michael-piziak on 2014-12-01
> **nerdtron said:**
> Plug in any of the unrecognized usb sticks and post the output of the command here:
```
 dmesg | tail -n 40 
```

The output is:

house@house-KJ294AA-ABA-m9252p:~$ dmesg | tail -n 40
[   18.811932] Please fix your hotplug setup, the board will not work without firmware loaded!
[   18.812404] cx23885_initialize_codec() f/w load failed
[   18.812635] cx23885_dvb_register() allocating 1 frontend(s)
[   18.812672] cx23885[0]: cx23885 based dvb card
[   18.846405] MT2131: successfully identified at address 0x61
[   18.848056] DVB: registering new adapter (cx23885[0])
[   18.848061] cx23885 0000:03:00.0: DVB: registering adapter 0 frontend 0 (Samsung S5H1409 QAM/8VSB Frontend)...
[   18.848354] cx23885_dev_checkrevision() Hardware revision = 0xb1
[   18.848360] cx23885[0]/0: found at 0000:03:00.0, rev: 15, irq: 17, latency: 0, mmio: 0xf9e00000
[   19.141702] r8169 0000:02:00.0 eth0: link down
[   19.141738] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   19.141960] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   19.143450] ieee80211 phy0: rt2x00lib_request_firmware: Info - Loading firmware file 'rt73.bin'
[   19.169126] ieee80211 phy0: rt2x00lib_request_firmware: Info - Firmware detected - version: 1.7
[   19.244817] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   19.245168] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   20.520245] wlan0: authenticate with e0:91:f5:80:17:0a
[   20.568219] wlan0: send auth to e0:91:f5:80:17:0a (try 1/3)
[   20.569779] wlan0: authenticated
[   20.572027] wlan0: associate with e0:91:f5:80:17:0a (try 1/3)
[   20.574657] wlan0: RX AssocResp from e0:91:f5:80:17:0a (capab=0x411 status=0 aid=2)
[   20.584528] wlan0: associated
[   20.584540] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   24.822802] init: plymouth-upstart-bridge main process ended, respawning
[   24.839669] init: plymouth-upstart-bridge main process ended, respawning
[   47.688082] audit_printk_skb: 150 callbacks suppressed
[   47.688086] type=1400 audit(1417451974.602:62): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=2150 comm="apparmor_parser"
[   47.688093] type=1400 audit(1417451974.602:63): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=2150 comm="apparmor_parser"
[   47.688510] type=1400 audit(1417451974.602:64): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=2150 comm="apparmor_parser"
[ 1983.474043] usb 2-5.3: USB disconnect, device number 6
[ 3121.608253] usb 2-5.4: new low-speed USB device number 7 using ehci-pci
[ 3121.706376] usb 2-5.4: New USB device found, idVendor=03f0, idProduct=0f0c
[ 3121.706381] usb 2-5.4: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[ 3121.706385] usb 2-5.4: Product: USB Multimedia Wireless Kit
[ 3121.706388] usb 2-5.4: Manufacturer: Chicony
[ 3121.709265] input: Chicony USB Multimedia Wireless Kit as /devices/pci0000:00/0000:00:1d.7/usb2/2-5/2-5.4/2-5.4:1.0/input/input14
[ 3121.709424] hid-generic 0003:03F0:0F0C.0003: input,hidraw2: USB HID v1.11 Keyboard [Chicony USB Multimedia Wireless Kit] on usb-0000:00:1d.7-5.4/input0
[ 3121.715219] input: Chicony USB Multimedia Wireless Kit as /devices/pci0000:00/0000:00:1d.7/usb2/2-5/2-5.4/2-5.4:1.1/input/input15
[ 3121.715447] hid-generic 0003:03F0:0F0C.0004: input,hiddev0,hidraw3: USB HID v1.11 Mouse [Chicony USB Multimedia Wireless Kit] on usb-0000:00:1d.7-5.4/input1
[ 3121.756307] WARNING! power/level is deprecated; use power/control instead
house@house-KJ294AA-ABA-m9252p:~$

---

### Post by nerdtron on 2014-12-01
What is that USB device you are plugging in? I don't think the Chicony USB Multimedia Wireless Kit is a normal USB flash drive?

Also this:
 [   18.811932] Please fix your hotplug setup, the board will not work without firmware loaded!

Can you look into the BIOS of the computer and maybe look into the USB settings? There could be disable plug and play perhaps?

---

### Post by michael-piziak on 2014-12-01
> **nerdtron said:**
> What is that USB device you are plugging in? I don't think the Chicony USB Multimedia Wireless Kit is a normal USB flash drive?

Also this:
 [   18.811932] Please fix your hotplug setup, the board will not work without firmware loaded!

Can you look into the BIOS of the computer and maybe look into the USB settings? There could be disable plug and play perhaps?

I think the firmware problem is a more serious problem (and could perhaps fix the usb problem).

The USB device I have plugged in is just an HP thumb drive.  I have another type of usb thumb drive I can plug in and report back if that would help.

In the meantime, can someone help me fix the hotplug setup/firmware problem.  I'm not sure how to fix firmware on this computer.  This computer is an HP Pavilion Elite m9252p PC

---

### Post by michael-piziak on 2014-12-01
> **nerdtron said:**
> What is that USB device you are plugging in? I don't think the Chicony USB Multimedia Wireless Kit is a normal USB flash drive?

Also this:
 [   18.811932] Please fix your hotplug setup, the board will not work without firmware loaded!

Can you look into the BIOS of the computer and maybe look into the USB settings? There could be disable plug and play perhaps?

I plugged in a different USB thumb drive (that doesn't work), typed in your command and this is reported:

[COLOR=#000000][FONT=Ubuntu Mono]
[/FONT][/COLOR]house@house-KJ294AA-ABA-m9252p:~$ dmesg | tail -n 40[ 3121.706385] usb 2-5.4: Product: USB Multimedia Wireless Kit
[ 3121.706388] usb 2-5.4: Manufacturer: Chicony
[ 3121.709265] input: Chicony USB Multimedia Wireless Kit as /devices/pci0000:00/0000:00:1d.7/usb2/2-5/2-5.4/2-5.4:1.0/input/input14
[ 3121.709424] hid-generic 0003:03F0:0F0C.0003: input,hidraw2: USB HID v1.11 Keyboard [Chicony USB Multimedia Wireless Kit] on usb-0000:00:1d.7-5.4/input0
[ 3121.715219] input: Chicony USB Multimedia Wireless Kit as /devices/pci0000:00/0000:00:1d.7/usb2/2-5/2-5.4/2-5.4:1.1/input/input15
[ 3121.715447] hid-generic 0003:03F0:0F0C.0004: input,hiddev0,hidraw3: USB HID v1.11 Mouse [Chicony USB Multimedia Wireless Kit] on usb-0000:00:1d.7-5.4/input1
[ 3121.756307] WARNING! power/level is deprecated; use power/control instead
[ 3369.877790] systemd-hostnamed[2726]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
[ 3874.760265] usb 2-5.3: new low-speed USB device number 8 using ehci-pci
[ 3874.856512] usb 2-5.3: New USB device found, idVendor=0428, idProduct=4001
[ 3874.856518] usb 2-5.3: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[ 3874.856522] usb 2-5.3: Product: GamePad Pro USB 
[ 3874.856525] usb 2-5.3: Manufacturer: Gravis
[ 3879.860973] input: Gravis GamePad Pro USB  as /devices/pci0000:00/0000:00:1d.7/usb2/2-5/2-5.3/2-5.3:1.0/input/input16
[ 3879.861177] hid-generic 0003:0428:4001.0005: input,hidraw4: USB HID v1.00 Gamepad [Gravis GamePad Pro USB ] on usb-0000:00:1d.7-5.3/input0
[ 3879.862015] usb 2-5.4: USB disconnect, device number 7
[ 3880.156271] usb 2-5.4: new low-speed USB device number 9 using ehci-pci
[ 3880.254766] usb 2-5.4: New USB device found, idVendor=03f0, idProduct=0f0c
[ 3880.254771] usb 2-5.4: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[ 3880.254775] usb 2-5.4: Product: USB Multimedia Wireless Kit
[ 3880.254778] usb 2-5.4: Manufacturer: Chicony
[ 3880.257645] input: Chicony USB Multimedia Wireless Kit as /devices/pci0000:00/0000:00:1d.7/usb2/2-5/2-5.4/2-5.4:1.0/input/input17
[ 3880.257833] hid-generic 0003:03F0:0F0C.0006: input,hidraw2: USB HID v1.11 Keyboard [Chicony USB Multimedia Wireless Kit] on usb-0000:00:1d.7-5.4/input0
[ 3880.263658] input: Chicony USB Multimedia Wireless Kit as /devices/pci0000:00/0000:00:1d.7/usb2/2-5/2-5.4/2-5.4:1.1/input/input18
[ 3880.263870] hid-generic 0003:03F0:0F0C.0007: input,hiddev0,hidraw3: USB HID v1.11 Mouse [Chicony USB Multimedia Wireless Kit] on usb-0000:00:1d.7-5.4/input1
[ 4054.281121] perf samples too long (2508 > 2500), lowering kernel.perf_event_max_sample_rate to 50000
[ 5719.299212] usb 2-5.4: USB disconnect, device number 9
[ 7592.708172] usb 2-5.3: USB disconnect, device number 8
[ 7600.332304] usb 2-5.4: new full-speed USB device number 10 using ehci-pci
[ 7600.588308] usb 2-5.4: new high-speed USB device number 11 using ehci-pci
[ 7600.681174] usb 2-5.4: New USB device found, idVendor=14cd, idProduct=125c
[ 7600.681180] usb 2-5.4: New USB device strings: Mfr=1, Product=3, SerialNumber=2
[ 7600.681183] usb 2-5.4: Product: Mass Storage Device
[ 7600.681187] usb 2-5.4: Manufacturer: Generic
[ 7600.681190] usb 2-5.4: SerialNumber: 125C20100726
[ 7600.682004] usb-storage 2-5.4:1.0: USB Mass Storage device detected
[ 7600.682371] scsi8 : usb-storage 2-5.4:1.0
[ 7601.680838] scsi 8:0:0:0: Direct-Access     Mass     Storage Device        PQ: 0 ANSI: 0 CCS
[ 7601.681200] sd 8:0:0:0: Attached scsi generic sg6 type 0
[ 7601.685448] sd 8:0:0:0: [sdf] Attached SCSI removable disk
house@house-KJ294AA-ABA-m9252p:~$


p.s. You asked if I could look into the Bios also - again, I need a command line I guess to do that.

p.s.s.  This system has been running for 3+ days with no problem other than the usb thumb drives not being recognized.  HP apparently doesn't support linux firmware fixes.   Does anyone think this firmware error will be detrimental to this computer?

---

