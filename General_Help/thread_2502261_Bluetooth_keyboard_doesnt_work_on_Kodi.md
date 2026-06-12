---
title: "Bluetooth keyboard doesnt work on Kodi"
date: 2024-11-07
forum: General Help
---

### Post by beric77 on 2024-11-07
Hi,

I just install Ubuntu server on a mini pc, then install kodi and update & upgrade
I have this keyboard [https://www.logitech.com/es-es/products/...board.html]("https://www.logitech.com/es-es/products/keyboards/k400-plus-touchpad-keyboard.html")
When I launch Kodi its works but not the keyboard.
My installation has not desktop enviroment.
Have I to install some component to be able to use the keyboard ?

Thanks,

---

### Post by TheFu on 2024-11-07
I have OSMC/Kodi running on a Raspberry Pi v4.  [https://www.amazon.com/Inteset-Universal-Receiver-Streamers-Including/dp/B08KBVTGFH](https://www.amazon.com/Inteset-Universal-Receiver-Streamers-Including/dp/B08KBVTGFH) is what I use.  Used a generic RC6 remote before, but this one is better.  Of course, there are cheaper "universal remotes". YMMV.

For anything more complex, I use an android phone or tablet to control/access.  That seldom happens. There are multiple "apps" for Kodi, like "Kore".

Guess it depends on your specific use.  I seldom need a full keyboard or mouse. For weekly patching, I just ssh into the system and do the updates over a terminal session.

The only time I left bluetooth enabled, by accident, on Ubuntu, I had just done a fresh install and was at a security conference.  Someone hacked in over  BT and left a nice note that they had where I couldn't miss it.  That evening, back at the hotel, I wiped the system and reloaded it fresh, careful to disable BT.

You can always check the Kodi wiki/forums for recommended keyboards.

---

### Post by beric77 on 2024-11-07
I have installed desktop enviroment, opening kodi from desktop, keyboard works correctly. I guess that when starting the terminal something was not loaded, and then in the desktop session it is.
I'm not sure if the remote you mention would work by opening kodi from the terminal without starting the desktop.

---

### Post by TheFu on 2024-11-07
kodi-standalone or something like that is the command to use to start kodi.  It has been over a decade since I actually used Kodi on an x86 system, so my memory could be off.

For a remote, you'll need to setup lirc ... which is usually just changing a symbolic link to point the config at the correct type of remote you have.

I'm not a fan of bluetooth for so many reasons.

---

### Post by beric77 on 2024-11-08
I have been using Kodi with this keybolard and Raspi 3 a lot of time, launching kodi-standalone from terminal session without problems.
 Now I have buy this mini pc more powerfull and I dont understand why doesnt work. Maybe I will try with Raspbian OS.

The question is which component is not loaded in the terminal session and is loaded in the graphical environment.

---

### Post by TheFu on 2024-11-08
I suspect there isn't any bluetooth loaded without a full GUI session also loaded, but I don't really know.

---

