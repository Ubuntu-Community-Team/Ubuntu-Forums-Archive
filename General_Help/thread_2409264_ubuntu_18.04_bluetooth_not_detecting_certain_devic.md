---
title: "ubuntu 18.04: bluetooth not detecting certain devices / speaker"
date: 2018-12-30
forum: General Help
---

### Post by uwes on 2018-12-30
Hi,

I bought a libratone too (bluetooth speaker) as a christmas present for my wife. It works just fine when we use it with our android phones. Unfortunately, my ubuntu does not even find the speaker in the bluetooth settings. Also hcitool scan does not find anything. However, bluetooth on my laptop also generally works, at least I can connect to my phone and also send files, so it's not the bluetooth functionality itself. This is were I get stuck and do not know where I should start to look. I tried a reboot, as I read about problems occuring after hibernation, but to no avail. journalctl | grep -i bluetooth also did not throw any serious errors as far as I understood it (only hci0: last event is not cmd complete (0x0f) every few seconds). Any ideas on where I could continue looking?

Thanks
Uwe

---

### Post by uwes on 2018-12-30
Update: After 20 or 30 min, my laptop also finally detects an audio device via bluetooth. At least the gui-tool shows an additional line which translates to "Audio device: not set up". However, the device is greyed out and I cannot connect to it, and if I run hcitool scan, it does not find anything again. But there is something in journalctl
```

Dez 30 21:55:13 perspire kernel: Bluetooth: hci0: last event is not cmd complete (0x0f)
Dez 30 21:55:29 perspire kernel: Bluetooth: hci0: last event is not cmd complete (0x0f)
Dez 30 21:55:46 perspire NetworkManager[991]: <info>  [1546203346.5687] manager: (EC:8C:9A:B3:02:79): new Bluetooth device (/org/freedesktop/NetworkManager/Devices/8)
Dez 30 21:55:46 perspire NetworkManager[991]: <info>  [1546203346.5726] manager: (04:B1:67:27:28:47): new Bluetooth device (/org/freedesktop/NetworkManager/Devices/9)
Dez 30 21:55:46 perspire kernel: Bluetooth: hci0: last event is not cmd complete (0x0f)
Dez 30 21:56:02 perspire kernel: Bluetooth: hci0: last event is not cmd complete (0x0f)
Dez 30 21:56:18 perspire kernel: Bluetooth: hci0: last event is not cmd complete (0x0f)
Dez 30 21:56:34 perspire kernel: Bluetooth: hci0: last event is not cmd complete (0x0f)
Dez 30 21:56:50 perspire kernel: Bluetooth: hci0: last event is not cmd complete (0x0f)
Dez 30 21:57:06 perspire kernel: Bluetooth: hci0: last event is not cmd complete (0x0f)
Dez 30 21:57:22 perspire kernel: Bluetooth: hci0: last event is not cmd complete (0x0f)
Dez 30 21:57:38 perspire kernel: Bluetooth: hci0: last event is not cmd complete (0x0f)
Dez 30 21:57:54 perspire kernel: Bluetooth: hci0: last event is not cmd complete (0x0f)

```

Unfortunately, after turning off bluetooth, the device is gone again...

---

### Post by clementc on 2018-12-31
Hi [**[COLOR=#000000]uwes[/COLOR]**]("https://ubuntuforums.org/member.php?u=744707"),

What kernel are you on? (please run uname -r in Terminal)

One thing you could try is to update your kernel to the latest version (4.20 at the time of this writing) using Ukuu Kernel Update Utility.

This [page]("http://ubuntuhandbook.org/index.php/2017/02/ukuu-install-latest-kernels-ubuntu-linux-mint/") will help you update your kernel (please make sure to backup all important files first, just in case).

Please report back once done.

Please note that you should only attempt these steps if you feel confident doing so.

---

### Post by uwes on 2019-01-20
Hi clementc,

thanks for your feedback. I thought I had email-notifications turned on, that's why I did not notice your reply earlier. In the meantime, I had returned the speaker and bought a Sony SRS-XB31 instead. However, the problem remains exactly the same. Also, I updated my bluez version to 5.50ubuntu0ppa1, as described here: [https://medium.com/@overcode/fixing-bluetooth-in-ubuntu-pop-os-18-04-d4b8dbf7ddd6]("https://medium.com/@overcode/fixing-bluetooth-in-ubuntu-pop-os-18-04-d4b8dbf7ddd6"). However, to no avail. My kernel version is 4.15.0-43. I don't really feel confident updating the kernel, at least it sounds like a more complicated operation. Might a system update to ubuntu 18.10 help? If I have the mac address of the speaker, could I somehow try to connect directly in the terminal?

Thanks

---

### Post by uwes on 2019-01-20
Hi clementc,

problem solved. I was just too stupid to notice that I have to put the speakers in pairing mode by pushing the on-button for a longer time. With the phones I seem to have gotten it right accidentally. When in pairing mode, I can connect without problems, even with the bluez version which is shipped with ubuntu 18.04. Sorry for the trouble.

---

