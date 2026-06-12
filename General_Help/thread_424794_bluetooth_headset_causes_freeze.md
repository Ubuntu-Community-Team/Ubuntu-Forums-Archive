---
title: "bluetooth headset causes freeze"
date: 2007-04-27
forum: General Help
---

### Post by tlacuache on 2007-04-27
I just got an H700 bluetooth headset. I followed the directions linked to from [https://help.ubuntu.com/community/BluetoothSetup](https://help.ubuntu.com/community/BluetoothSetup), and everything worked fine at first (scan, entering in the pin number, etc.). I can connect to the headset fine using btsco, and I can try to start a call in Skype (or to play an mp3 in xmms), and I hear the speaker on my ear "turn on", but then my whole computer locks up. No keyboard or mouse response, nothing. What can I do?

I read something somewhere about setting some variable "enableavrcp" to 0 to avoid freezes with bluetooth, but i don't know what file this goes in and I can't seem to find it in the forums.

Any help?

-Seth Grover

---

### Post by tlacuache on 2007-04-27
I should also note that when the computer locks, my CAPS LOCK indicator light blinks like crazy. I don't know what that means.

I tried to SSH into my machine, and that was unresponsive, as well.

---

### Post by tlacuache on 2007-04-27
Here's a list of all of my bluetooth-related packages installed (that I could find):
```

bluemon         1.4-2.0.1        Activate or deactivate programs based on Bluetooth link 
bluetooth       3.9-0ubuntu4     Bluetooth stack utilities
bluez-btsco     0.50-0ubuntu2    Bluez Bluetooth SCO tool
bluez-cups      3.9-0ubuntu4     Bluetooth printer driver for CUPS
bluez-gnome     0.6-1ubuntu3     Bluetooth utilities for GNOME
bluez-hcidump   1.33-0ubuntu1    Analyses Bluetooth HCI packets
bluez-pin       0.30-2.1ubuntu3  Bluetooth PIN helper with D-BUS support
bluez-utils     3.9-0ubuntu4     Bluetooth tools and daemons
btscanner       2.1-3            ncurses-based scanner for Bluetooth devices
gnome-bluetooth 0.8.0-0ubuntu4   GNOME Bluetooth tools.
libbluetooth2   3.9-0ubuntu1     Library to use the BlueZ Linux Bluetooth stack
libbtctl4       0.8.2-0ubuntu6   GObject Bluetooth library
libgnomebt0     0.8.0-0ubuntu4   GNOME Bluetooth library
bluez-btsco     0.50-0ubuntu2    Bluez Bluetooth SCO tool
btscanner       2.1-3            ncurses-based scanner for Bluetooth devices
libbtctl4       0.8.2-0ubuntu6   GObject Bluetooth library
libgnomebt0     0.8.0-0ubuntu4   GNOME Bluetooth library
```

Also, here's a list of bluetooth related modules loaded reported by lsmod:
```
bluetooth              55908  7 rfcomm,l2cap,hci_usb
snd_bt_sco             17036  0 
snd_hwdep               9988  1 snd_bt_sco
snd_pcm                79876  4 snd_bt_sco,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd                    54020  14 snd_bt_sco,snd_hwdep,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
snd_page_alloc         10888  3 snd_bt_sco,snd_intel8x0,snd_pcm
```

---

### Post by tlacuache on 2007-04-30
Sigh...

I also tried the instructions [here]("http://ubuntuforums.org/showthread.php?t=426828"). I was actually able to record audio using the microphone of the headset, but again, whenever I tried to send any audio TO the headset, I get the kernel panic (at least I think that's what the blinking CAPS lock button means).

Any takers? This is the first time I've ever asked for help here that I haven't gotten at least some sort of helpful response within a day or so. Not a good sign. :confused: 

-Seth

---

### Post by djf_jeff on 2008-01-23
Hi,

I have the same problem as you. If I output audio to the headset, kernel panic ensure just after...

---

### Post by djf_jeff on 2008-01-26
Just want to add something. I have changed my bluetooth dongle and everything work fine now. My old dongle was a bluetooth 1.2 and my new is a bluetooth 2.0. So, it seems my headset requiere a bluetooth 2.0 dongle to work.

---

