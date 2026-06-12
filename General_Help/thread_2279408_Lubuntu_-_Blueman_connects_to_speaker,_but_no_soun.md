---
title: "Lubuntu - Blueman connects to speaker, but no sound"
date: 2015-05-23
forum: General Help
---

### Post by ktat on 2015-05-23
I have recently been trying to connect my Bose speaker to my Lubuntu laptop via the blueman-manager.  Initially, it would find it but then would disconnect after trying to connect to the audio sink.

I tweaked the /etc/bluetooth/audio.conf file and now the blueman-manager tells me that the device is successfully connected to the audio sink.

The problem now is that the audio is only coming out of my laptop speakers when playing files.  I feel like I am close to solving this, does anyone have any ideas?

```
uname -a
Linux lubuntu13 3.13.0-46-generic #79-Ubuntu SMP Tue Mar 10 20:08:14 UTC 2015 i686 i686 i686 GNU/Linux
```

I have also tried:
```
sudo pactl load-module module-bluetooth-discover
```

with the result:
```
Home directory not accessible: Permission denied
Connection failure: Connection refused
pa_context_connect() failed: Connection refused
```

---

### Post by ktat on 2015-06-01
So, I've had a go at connecting to same speaker using Ubuntu.  Initially I had the same problem, until I opened up the audio options and found that I just needed to select the bluetooth speaker as the audio output device :).

I think I know what I need to do now, I just don't know how to do it.

Opening up "volume control settings" in lubuntu gives you the "Alsamixer" and I can't find any option here to change the device to send audio out to.

---

### Post by coffeecat on 2015-06-01
Lubuntu is an official Ubuntu flavour - it doesn't need to be in the Other OS section - so...

*Thread moved to **General Help**.*

---

### Post by walterorlin on 2015-06-02
ktat it could be that your sound is set to come out of the laptop speakers. One way you can troubleshoot is in the audicaous prefrences you can change the playback device but a lot of people like installing pavucontrol when dealing with multiple sound output devices but this will install pulseaudio as a dependency. This will then give you a GUI to select output device easily. Also since this is a laptop you might not take your bluetooth speaker with you everywhere so you may want to switch back to laptop speakers sometimes or maybe the headphone jack if your laptop has one. The other way involves editing config files and this will probably be the easiest way. I don't know of a pure alsa mixer that changes output device globally with just alsa that works in lxpanel.

---

### Post by n4rps2 on 2015-06-04
Hello!

Part of it involves pulse audio and some tweaks to the /etc/bluetooth/audio.conf file; part of it involves adding the blueman PPA to pull down the latest version of Blueman.

Using some stuff we dug up in different places on your forums, we put together a fix over at Linux Lite for the Bluetooth issue months ago.

It will also get Bluetooth going on Lubuntu systems. We also added a part about how to get some of the Broadcom-based USB Bluetooth adapters going - like the Targus ACB10/ACB10-US1, for example.

Here's the link: [https://www.linuxliteos.com/forums/network/%28solved%29-enabling-full-bluetooth-support-in-linux-lite/](https://www.linuxliteos.com/forums/network/%28solved%29-enabling-full-bluetooth-support-in-linux-lite/)

Hope this helps you folks out!

73 DE N4RPS
Rob

---

