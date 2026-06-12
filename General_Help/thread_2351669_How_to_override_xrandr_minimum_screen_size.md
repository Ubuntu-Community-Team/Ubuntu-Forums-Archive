---
title: "How to override xrandr minimum screen size"
date: 2017-02-05
forum: General Help
---

### Post by master higgins on 2017-02-05
Hi, I've been fiddling with xorg.conf to modify the minimum resolution that can be set with my video card. I'm currently using a Radeon HD 5450 and this is what is shown when i type **xrandr**:
[xrandr output]("http://pastebin.com/Htmsv2R9")
This is my current /etc/X11/xorg.conf:
[xorg.conf]("http://pastebin.com/wJcTZsNh")
And this is my Xorg.0.log:
[Xorg.0.log]("http://pastebin.com/7yjUWQUE")

xrandr currently reports a minimum resolution of 320x200. I don't know if this is get from the EDID data. I've tried to add options to xorg.conf to ignore the EDID but to no avail.

I've reached the end of the rope. Is this hard-coded in the radeon driver? Or is there a way to "cheat" the radeon driver to use a shorter minimum resolution?

BTW, this is to output 15Khz modes for a CRT TV via SCART cable. When i try to use modes with less than 320 pixels wide this is the error I get:
```
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  140 (RANDR)
  Minor opcode of failed request:  2 (RRSetScreenConfig)
  Value in failed request:  0xf0
  Serial number of failed request:  14
  Current serial number in output stream:  14


```

I hope you can help me with this.
Help would be greatly appreciated!
Greets!

---

