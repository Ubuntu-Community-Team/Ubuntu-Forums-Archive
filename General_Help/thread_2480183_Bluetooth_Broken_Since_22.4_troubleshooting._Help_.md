---
title: "Bluetooth Broken Since 22.4 troubleshooting. Help me Reinstall Bluetooth in 22.11."
date: 2022-10-21
forum: General Help
---

### Post by schlaegel on 2022-10-21
Bluetooth had been working fine in 22.4, then one day it stopped, but instead of waiting for a new package that got it working, I searched websites for solutions and tried them all. Now it's worse.

I thought upgrading to 22.10 would reinstall the bluetooth stack and everything would work again, but it's still in the same broken state.

```
[B]$ sudo apt list --installed '*blue*'
[/B]Listing... Done
blueman/kinetic,now 2.3.2-1 amd64 [installed]
bluetooth/kinetic,kinetic,now 5.65-0ubuntu1 all [installed]
bluez-obexd/kinetic,now 5.65-0ubuntu1 amd64 [installed,automatic]
bluez-tools/kinetic,now 2.0~20170911.0.7cb788c-4 amd64 [installed]
bluez/kinetic,now 5.65-0ubuntu1 amd64 [installed]
gir1.2-gnomebluetooth-3.0/kinetic,now 42.4-1 amd64 [installed,automatic]
gnome-bluetooth-3-common/kinetic,kinetic,now 42.4-1 all [installed,automatic]
gnome-bluetooth-sendto/kinetic,now 42.4-1 amd64 [installed,automatic]
libbluetooth3/kinetic,now 5.65-0ubuntu1 amd64 [installed,automatic]
libgnome-bluetooth-3.0-13/kinetic,now 42.4-1 amd64 [installed,automatic]
libgnome-bluetooth-ui-3.0-13/kinetic,now 42.4-1 amd64 [installed,automatic]
libspa-0.2-bluetooth/kinetic,now 0.3.58-2ubuntu1 amd64 [installed,automatic]

```

```
[B]$ sudo dmesg | grep Blue
[/B][    2.510270] Bluetooth: Core ver 2.22
[    2.510312] Bluetooth: HCI device and connection manager initialized
[    2.510316] Bluetooth: HCI socket layer initialized
[    2.510319] Bluetooth: L2CAP socket layer initialized
[    2.510326] Bluetooth: SCO socket layer initialized
[    4.544575] Bluetooth: hci0: Reading Intel version command failed (-110)
[    6.148036] Bluetooth: hci0: command tx timeout
[    7.677065] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    7.677068] Bluetooth: BNEP filters: protocol multicast
[    7.677070] Bluetooth: BNEP socket layer initialized

```


When I turn on Bluetooth in gnome-control-center nothing happens.

---

### Post by QIII on 2022-10-22
A sure way to muck things up is to search the web and "try everything".  At this point, we can't know what you did and we can't know the state of your machine.

Did you upgrade to 22.10 or did you do a clean installation?  

Upgrades will often carry problems along like junk in an attic -- and possibly even compound them.  Also, 22.10 is an interim release and that is probably not good for trying to resolve problems.

---

### Post by schlaegel on 2022-10-22
Yep. Trying everything usually doesn't work. One seldom tries everything by design. Each try was after unsuccessfully tying what someone else had reported worked for them. The sad part is that Bluetooth worked great until an update.

Maybe someone here knows how to install the Bluetooth stack as it comes with Ubuntu, or maybe someone can help me decipher the logs.

I'm not a newb to Linux, quite the opposite. However, I am relatively inexperienced with Ubuntu, it's package managers, and the Bluetooth stack.

---

### Post by #&amp;thj^% on 2022-10-22
Well again without knowing what you've done, let's peek @
```
sudo systemctl status bluetooth
[sudo] password for me: 
&#9679; bluetooth.service - Bluetooth service
     Loaded: loaded (/usr/lib/systemd/system/bluetooth.service; enabled; preset>
     Active: active (running) since Sat 2022-10-22 08:44:29 MDT; 3h 48min ago
       Docs: man:bluetoothd(8)
   Main PID: 1064 (bluetoothd)
     Status: "Running"
      Tasks: 1 (limit: 9356)
     Memory: 2.2M
        CPU: 96ms
     CGroup: /system.slice/bluetooth.service
             &#9492;&#9472;1064 /usr/lib/bluetooth/bluetoothd

Oct 22 08:57:11 arch-me bluetoothd[1064]: Endpoint registered: sender=:1.92 pat>
Oct 22 08:57:11 arch-me bluetoothd[1064]: Endpoint registered: sender=:1.92 pat>
Oct 22 08:57:11 arch-me bluetoothd[1064]: Endpoint registered: sender=:1.92 pat>
Oct 22 08:57:11 arch-me bluetoothd[1064]: Endpoint registered: sender=:1.92 pat>
Oct 22 08:57:11 arch-me bluetoothd[1064]: Endpoint registered: sender=:1.92 pat>
Oct 22 08:57:11 arch-me bluetoothd[1064]: Endpoint registered: sender=:1.92 pat>
Oct 22 08:57:11 arch-me bluetoothd[1064]: Endpoint registered: sender=:1.92 pat>
Oct 22 08:57:11 arch-me bluetoothd[1064]: Endpoint registered: sender=:1.92 pat>
Oct 22 08:57:11 arch-me bluetoothd[1064]: Endpoint registered: sender=:1.92 pat>
Oct 22 08:57:18 arch-me bluetoothd[1064]: src/profile.c:record_cb() Unable to g>
lines 1-22/22 (END)...skipping...
&#9679; bluetooth.service - Bluetooth service
     Loaded: loaded (/usr/lib/systemd/system/bluetooth.service; enabled; preset: disabled)
     Active: active (running) since Sat 2022-10-22 08:44:29 MDT; 3h 48min ago
       Docs: man:bluetoothd(8)
   Main PID: 1064 (bluetoothd)
     Status: "Running"
      Tasks: 1 (limit: 9356)
     Memory: 2.2M
        CPU: 96ms
     CGroup: /system.slice/bluetooth.service
             &#9492;&#9472;1064 /usr/lib/bluetooth/bluetoothd

Oct 22 08:57:11 arch-me bluetoothd[1064]: Endpoint registered: sender=:1.92 path=/MediaEndpoint/A2DPSource/faststream
Oct 22 08:57:11 arch-me bluetoothd[1064]: Endpoint registered: sender=:1.92 path=/MediaEndpoint/A2DPSource/faststream_duplex
Oct 22 08:57:11 arch-me bluetoothd[1064]: Endpoint registered: sender=:1.92 path=/MediaEndpoint/A2DPSink/opus_05
Oct 22 08:57:11 arch-me bluetoothd[1064]: Endpoint registered: sender=:1.92 path=/MediaEndpoint/A2DPSource/opus_05
Oct 22 08:57:11 arch-me bluetoothd[1064]: Endpoint registered: sender=:1.92 path=/MediaEndpoint/A2DPSource/opus_05_51
Oct 22 08:57:11 arch-me bluetoothd[1064]: Endpoint registered: sender=:1.92 path=/MediaEndpoint/A2DPSource/opus_05_71
Oct 22 08:57:11 arch-me bluetoothd[1064]: Endpoint registered: sender=:1.92 path=/MediaEndpoint/A2DPSink/opus_05_duplex
Oct 22 08:57:11 arch-me bluetoothd[1064]: Endpoint registered: sender=:1.92 path=/MediaEndpoint/A2DPSource/opus_05_duplex
Oct 22 08:57:11 arch-me bluetoothd[1064]: Endpoint registered: sender=:1.92 path=/MediaEndpoint/A2DPSource/opus_05_pro
Oct 22 08:57:18 arch-me bluetoothd[1064]: src/profile.c:record_cb() Unable to get Hands-Free Voice gateway SDP record: Host is down


```
Also is it blocked;
```
rfkill list all
``` 
Mine is soft blocked IE:
```
0: ideapad_wlan: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
1: ideapad_bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: no
2: phy0: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
3: hci0: Bluetooth
	Soft blocked: yes
	Hard blocked: no
```
EDIT:
```
inxi -E
Bluetooth:
  Device-1: Intel AX200 Bluetooth type: USB driver: btusb
  Report: rfkill ID: hci0 rfk-id: 3 state: down bt-service: enabled,running
    rfk-block: hardware: no software: yes address: see --recommends

```

---

### Post by #&amp;thj^% on 2022-10-22
If your really after a little clean-up then use: 
```
sudo apt reinstall --purge bluez gnome-bluetooth
```
Now if you check:
```
sudo systemctl status bluetooth.service
&#9675; bluetooth.service - Bluetooth service
     Loaded: loaded (/lib/systemd/system/bluetooth.service; enabled; vendor pre>
    ** Active: inactive (dead)**
       Docs: man:bluetoothd(8)

```

Re/Start use:
```
sudo systemctl start bluetooth.service
```
we check again with:
```
sudo systemctl status bluetooth.service
&#9679; bluetooth.service - Bluetooth service
     Loaded: loaded (/lib/systemd/system/bluetooth.service; enabled; vendor pre>
     Active: active (running) since Sat 2022-10-22 14:49:49 MDT; 4s ago
       Docs: man:bluetoothd(8)
   Main PID: 3449 (bluetoothd)
     Status: "Running"

```
I would still like to see the outputs from my earlier post#4 above.
If still dead use this:
```
sudo hciconfig hci0 up
```

---

### Post by jeremy31 on 2022-10-22
It is some kernel issue after seeing this error ```
hci0: Reading Intel version command failed (-110)
```
A shutdown followed by a cold boot might work

---

### Post by #&amp;thj^% on 2022-10-22
I noticed that as well jeremy31, let's hope it's that simple.

---

