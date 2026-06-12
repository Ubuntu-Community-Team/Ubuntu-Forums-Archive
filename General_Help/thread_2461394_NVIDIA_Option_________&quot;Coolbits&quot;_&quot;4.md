---
title: "NVIDIA Option         &quot;Coolbits&quot; &quot;4&quot;"
date: 2021-04-29
forum: General Help
---

### Post by mugsisme on 2021-04-29
I added Coolbits = 4 to my xorg.conf to try to get the fans recoginized in a program I found in the software center.  I rebooted and now the machine wont boot, it just sits there after unlocking the disk.  I tried the previous kernel and actually got to see some error messages (I didnt with the current Kernel).  I am attaching a screenshot.  I appreciate if someone could help me.  Thanks.[ATTACH=CONFIG]288394[/ATTACH]

---

### Post by CatKiller on 2021-04-29
Just that in the config file makes it have invalid structure.

Create a snippet file, called something like **/etc/X11/xorg.conf.d/20-nvidia.conf**, and put in

```
Section "Device"
        Identifier      "Default Device"
        Driver          "nvidia"
        Option          "CoolBits"      "4"
EndSection
```

---

