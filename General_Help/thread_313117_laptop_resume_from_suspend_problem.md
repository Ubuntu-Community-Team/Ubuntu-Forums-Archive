---
title: "laptop resume from suspend problem"
date: 2006-12-05
forum: General Help
---

### Post by robgill on 2006-12-05
When I suspend my laptop (6.06 / gnome) it goes down fine and when I resume I get text,
"eth1: NETDEV_TX_BUSY returned; driver should report queue full via ieee_device -> is_queue_full"

eth1 is my wireless connections which works, but is not connected to anything  .

Any ideas how to fix this? - I have to reboot everytime (ctrl-alt-del) seems to do that.

---

### Post by yopnono on 2006-12-05
The error is a driver problem, nothing major. You can update it if you like.
[http://ipw2200.sourceforge.net/](http://ipw2200.sourceforge.net/)
[http://ipw2200.sourceforge.net/firmware.php](http://ipw2200.sourceforge.net/firmware.php)
[http://ieee80211.sourceforge.net/](http://ieee80211.sourceforge.net/)

And try this as a connection-manager for the wifi and it also support wired.
[http://ubuntuforums.org/showthread.php?t=299462](http://ubuntuforums.org/showthread.php?t=299462)

---

### Post by robgill on 2006-12-05
Thanks for the links, but can you give me a more detailed idea of what I need to do, I've never had to change anything with drivers (all of mine worked after install). 

And, I don't think the connection-manager thing will work for me, since I'm on dapper.

---

### Post by yopnono on 2006-12-06
Read the README file in the files you download it explain everything.

And yes it works on dapper. It works on al system that have python installed.
The only thing that don't work in dapper is the tray icon = not needed.

---

### Post by robgill on 2006-12-06
I'm pretty sure I got everything updated, but now all I get when I resume from suspend is a blank screen.  I tried ctrl-alt-backspace, but it didn't do anything so I had to reboot.

---

### Post by yopnono on 2006-12-06
> **robgill said:**
> I'm pretty sure I got everything updated, but now all I get when I resume from suspend is a blank screen.  I tried ctrl-alt-backspace, but it didn't do anything so I had to reboot.

Ok for you suspend problem try to add this to the xorg.conf file
/etc/X11/xorg.conf

Option      "VBERestore" "true"

In the section "Device"

---

### Post by robgill on 2006-12-06
I tried that and it didn't work, BUT before removing that from xorg.conf

I use beryl and when I selected metacity as my window manager instead, it resumed from suspend just fine.  So I either need to figure out how to write a scrpt that will make metacity window manager before suspend, manually do it everytime, or figure out how to resume from suspend with beryl.

thanks for all of your help.

---

