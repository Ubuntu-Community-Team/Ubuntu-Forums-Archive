---
title: "Mouse speed/acceleration at login (lightdm)"
date: 2012-11-28
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2012-11-28
i just got a 1600dpi mouse, coming from a 800dpi mouse; i was able to set it to my liking on the guest account like this (based on ~/.config/xfce4/xfconf/xfce-perchannel-xml/pointers.xml)
```
~$ cat /etc/xdg/xfce4/xfconf/xfce-perchannel-xml/pointers.xml
<?xml version="1.0" encoding="UTF-8"?>

<channel name="pointers" version="1.0">
  <property name="HID_04b40033" type="empty">
    <property name="Acceleration" type="double" value="0.500000"/>
  </property>
</channel>

```
i don't see how to change the speed in lightdm (aside from using the mouses sniper mode for it)

---

