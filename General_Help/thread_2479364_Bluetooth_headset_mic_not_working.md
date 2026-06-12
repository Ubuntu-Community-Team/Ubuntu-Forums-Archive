---
title: "Bluetooth headset mic not working"
date: 2022-09-22
forum: General Help
---

### Post by moy12 on 2022-09-22
I have a Bose 700 bluetooth headset. I'm able to pair it with my desktop (see below for system information) by using an external USB dongle (see below). 

VERSION="22.04.1 LTS (Jammy Jellyfish)"
Desktop Computer
description: Motherboard
       product: B560 Pro4
       vendor: ASRock
Intel(R) Core(TM) i5-10600K CPU @ 4.10GHz

usb:2
                   description: Generic USB device
                   product: BCM20702A0
                   vendor: Broadcom Corp
                   physical id: 9
                   bus info: usb@1:9
                   version: 1.12
                   serial: 000272CCA812
                   capabilities: usb-2.00
                   configuration: driver=btusb speed=12Mbit/s

Codec: Realtek ALC897


As shown in the first screenshot, the Headphone - Bose NC 700 HP option shows up

In the next screenshot, you can see that if I change the Configuration to Handsfree Head Unit (HFP), I can then see Bluetooth Input - Bose NC 700 HP as the input device. However, no sound seems to go through the mic.

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=291062&stc=1[/IMG]

I tried various things I found online, such as the following:

-pavucontrol, alsa-tools-gui
-pipewire
-alsamixer
-hdajackretask
-looking for audio codec config [here]("https://www.kernel.org/doc/html/latest/sound/hd-audio/models.html") (didn't find mine)
-was going to try ofono/ofono-phonesim, but had trouble adding the repository 

The headset works just fine in Windows and Android device.

Thanks for any help.

---

