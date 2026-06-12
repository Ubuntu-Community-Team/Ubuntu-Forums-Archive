---
title: "Skype + Bluetooth Headset"
date: 2008-06-23
forum: General Help
---

### Post by money2themax on 2008-06-23
i want to use my bluetooth head set with skype
i tried to follow this

[https://help.ubuntu.com/community/BluetoothSkype#head-39bd2352ed38cf0b5a8f554ad66a39acf8568f39](https://help.ubuntu.com/community/BluetoothSkype#head-39bd2352ed38cf0b5a8f554ad66a39acf8568f39)

```

**Check and load permanently:**

  
[LIST]
[*]Check with: 
 "dmesg"
If it works correctly you can load it permanently by adding the appropriate module name to the end of  /etc/modules 
 "gksudo gedit /etc/modules"
[/LIST]


```I don't know what to do @ this point so i moved on
[FONT=monospace]
```

[/FONT]btsco -v 00:1A:45:68:42:AE

```I got this 

```

btsco v0.42
Device is 1:0
Voice setting: 0x0060
Can't connect RFCOMM channel: Operation now in progress

```then i tried this

```

aplay -B 1000000 -D plughw:/usr/share/sounds/login.wav

```nothing happened

now i'm here asking you for your help

---

### Post by money2themax on 2008-06-23
i'm also setting up a in home server

---

### Post by money2themax on 2008-06-23
Does anybody work with bluetooth often to help me understand this?

---

