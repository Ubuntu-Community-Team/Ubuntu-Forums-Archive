---
title: "screen resolution maximal 1024x768"
date: 2015-02-07
forum: General Help
---

### Post by Luci_raica on 2015-02-07
Hello
I'm a new ubuntu user ..it's great but i can't fix the screen resolution above 1024x768
here a screenshot from the displaySettings panel 
[IMG]http://i.imgur.com/K5v7HVr.png?1[/IMG]
[IMG]http://imgur.com/K5v7HVr[/IMG]
Display unknown.. I've tried to findsome appropiate display drivers but failed[IMG]http://ubuntuforums.org/images/icons/icon9.png[/IMG]
[IMG]http://imgur.com/KB7vlgu[/IMG]
thanks
[IMG]http://i.imgur.com/KB7vlgu.png?1[/IMG]

---

### Post by carl4926 on 2015-02-07
Can you post please the result of this from a terminal

```
lspci -nnk
```

---

### Post by Luci_raica on 2015-02-07
display is working properly now... in a misterious way.. I've done nothing
perhaps the system detected the display automatically... after 2 weeks..
here[IMG]http://i.imgur.com/UKHsXJ6.png?1[/IMG]
here the result of your command  in terminal;
00:02.0 VGA compatible controller [0300]: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor Graphics Controller [8086:0152] (rev 09)
    Subsystem: Gigabyte Technology Co., Ltd Device [1458:d000]
    Kernel driver in use: i915
can you give me some advice for a proper display driver
thanks a lot

---

### Post by carl4926 on 2015-02-07
I was interested to see if that was the only GPU

Please check. I was thinking you might have hybrid graphics?

---

### Post by Luci_raica on 2015-02-08
graphic unit is integratet in the motherboard.. I don't have an extra one

---

