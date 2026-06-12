---
title: "Only one speaker outputs on Macbook with Edgy"
date: 2007-02-15
forum: General Help
---

### Post by Master Kale on 2007-02-15
I just installed Edgy on my macbook with a dual boot with OS X. I was able to read my music of my os x partition, but when I started listening, the sound only came out of one side. I am installed the latest Alsa and it didn't fix it. I checked alsamixer and the left channel was open but no sound coming out. I would really like both speakers. Thanks for the help.

---

### Post by yves on 2007-02-17
I do get the same behavior running 6.06 on my Lenovo AMD64 machine.
With the lspci command I find I have this :

 0403: nVidia Corporation MCP51 High Definition Audio (rev a2)

and with cat /proc/asound/modules
I see 0 snd_hda_intel.

 Not sure what it means.. what sound card do you have ?

---

### Post by Master Kale on 2007-02-25
I was able to fix my problem with a wiki entry at [https://wiki.ubuntu.com/MacBookProFeisty](https://wiki.ubuntu.com/MacBookProFeisty) . The fix should work for you it doesn't seem to be MacBook dependent. Hope it helps.

---

