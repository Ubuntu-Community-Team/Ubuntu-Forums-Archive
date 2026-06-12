---
title: "Audio rotates from playing fine to exceptionally loud static"
date: 2018-02-18
forum: General Help
---

### Post by cpare2 on 2018-02-18
Hoping someone can help me get to the root of the sound problems I am having on my Ubuntu System for months...
[LIST]
[*]Sound seems to flip between playing perfectly and static so loud it almost knocks me out of my chair every few seconds
[*]Multiple audio devices are listed (can I disable the ones that I don't need, and how?)
[*]Soundbar isn't always the default device - where do I set this?
[/LIST]

```

uname -a
Linux appserver 4.13.0-32-generic #35-Ubuntu SMP Thu Jan 25 09:13:46 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux
cat /proc/asound/cards 0 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xfe400000 irq 16
 1 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xfe080000 irq 33
 2 [SoundBar       ]: USB-Audio - Dell AC511 USB SoundBar
                      Dell Dell AC511 USB SoundBar at usb-0000:00:16.2-1.2, full speed

```

---

### Post by HermanAB on 2018-02-19
Well, here you go: [http://www.acehardware.com/product/index.jsp?productId=2793673](http://www.acehardware.com/product/index.jsp?productId=2793673)

Alternatively, run pavucontrol or alsamixer and turn everything down, then enable one at a time, till you found the culprit.

---

### Post by Yellow Pasque on 2018-02-19
> Multiple audio devices are listed (can I disable the ones that I don't need, and how?)

If all you want is the USB soundbar, this should do it (after reboot):
```
echo "blacklist snd-hda-intel" | sudo tee -a /etc/modprobe.d/blacklisthda.conf
```

Then, if you want to use the devices for that session:
```
sudo modprobe -v snd-hda-intel
```

---

