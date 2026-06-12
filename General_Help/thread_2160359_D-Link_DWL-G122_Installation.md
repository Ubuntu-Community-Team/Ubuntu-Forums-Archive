---
title: "D-Link DWL-G122 Installation"
date: 2013-07-06
forum: General Help
---

### Post by hiig on 2013-07-06
I have an old laptop that is pretty much useless for most things. There are a few uses I can think of for it, but they require an internet connection. Problem is, the wireless on the laptop doesn't work, and ethernet is not practical. A while back, I found this USB wifi stick amongst some stuff I had. It's a D-Link DWL-G122 Ver B1 (Firmware version 1.00). It's old, but it should still work. Now here's the problem...

I've looked through [this page]("https://wiki.ubuntu.com/NdisWrapper_DWL-G122") for instructions on how to install the drivers, but the problem is, the driver link 404s, so I'm stuck. Is there anything I can do to get this device to work? Not sure if it's relevant, but the laptop is an Asus Z92R (so it's one heck of a craptastic laptop).

---

### Post by MrSteve on 2013-07-06
try this link for the driver which includes a linux driver ...

[http://tsd.dlink.com.tw/ModelDocu.asp?SourceType=download&sno=HMINFJ](http://tsd.dlink.com.tw/ModelDocu.asp?SourceType=download&sno=HMINFJ)

sorry its a dead link, couldn&#8217;t delete the post ...

---

### Post by hiig on 2013-07-06
I managed to find a driver from a friend. It doesn't have the same .inf file, but I'm going to try it anyway. Problem is, I'm still stuck. Following the guide in the link I had, I got to this part:

[COLOR=#333333][FONT=Ubuntu Beta]Create a module alias for [NdisWrapper]("https://wiki.ubuntu.com/NdisWrapper") with[/FONT][/COLOR]

sudo ndiswrapper -m[COLOR=#333333][FONT=Ubuntu Beta][/FONT][/COLOR][HR][/HR][COLOR=#333333][FONT=Ubuntu Beta]Add the module with[/FONT][/COLOR]
sudo modprobe ndiswrapper

However, when I do the modprobe, it says that the module ndiswrapper was not found. Any idea why?

---

