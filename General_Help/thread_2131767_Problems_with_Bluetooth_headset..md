---
title: "Problems with Bluetooth headset."
date: 2013-04-02
forum: General Help
---

### Post by SteveDeFacto on 2013-04-02
I have a turtle beach PX5 headset. I don't understand the technical details but A2DP does not work for the mic. On Windows I can simply set the mic to use HSP/HFP and the speakers to use A2DP. This lets me hear audio in high quality and gives me a low quality mic to chat in games. However, in Ubuntu I can only set the profile to A2DP or HSP/HFP for the headset. So I can only use high quality audio with no mic or low quality audio with a low quality mic. In Ubuntu is there anyway to configure the mic to use HSP/HFP while the audio is played using A2DP?

---

### Post by SteveDeFacto on 2013-04-03
I really could use some help with this...

---

### Post by SteveDeFacto on 2013-04-04
Anybody?...

---

### Post by SteveDeFacto on 2013-04-06
...

---

### Post by anton_bors on 2013-08-13
Hey! My solution was to install blueman and configure it there with an external bluetooth adapter, because on my Laptop - I think this behaviour is on 95% of laptops - the network and bluetooth is share by one chipset.
  Also a good idea is to install pactl - it's pulseaudio control. Hope it helps.

Maybe this site can help you:
[https://help.ubuntu.com/community/BluetoothHeadset](https://help.ubuntu.com/community/BluetoothHeadset)

  Environment:
 Gnome-shell 3.8
 Ubuntu 13.04
 HP EliteBook 8560w 
DeLock Bluetooth adapter

---

