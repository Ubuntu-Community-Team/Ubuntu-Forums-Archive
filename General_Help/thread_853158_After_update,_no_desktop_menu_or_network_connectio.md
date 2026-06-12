---
title: "After update, no desktop menu or network connection"
date: 2008-07-08
forum: General Help
---

### Post by danfluidmind on 2008-07-08
I'm running 8.04 and just ran the updater to update all my packages and then rebooted. Now when I login I see the desktop background, but there is no menu across the top and no bar across the bottom. AND, the NetworkManager can't seem to get my network set up. It's no longer setting the default gateway or putting my name server into resolv.conf.

Anyone have any ideas where I should start to get things working again? I can't find anything in the logs.

Thanks
--Dan

---

### Post by simonapnic on 2008-07-08
For your network, try to do this from the CLI:
**dhclient**.
It should try to negotiate a connection with your DHCP server.

---

### Post by danfluidmind on 2008-07-08
Thanks Simon. I ended up getting the network up again. When I first installed 8.04 NetworkManager would not let me set a static IP address, so I put it into /etc/network/interfaces manually. After this latest upgrade NetworkManager apparently didn't like that, so I took my manual settings out of the interfaces file, rebooted and now the network seems to work again.

But I still get no desktop menu or application bar at the bottom. Can anyone point me to the place in the X11 or Gnome config files that puts those elements on the desktop? What are the processes called?

Thanks
--Dan

---

### Post by danfluidmind on 2008-07-08
Problem resolved. I found in another post the idea or running gnome-panel manually. I tried that and found that gnome-panel WAS NO LONGER INSTALLED!

How in the hell the latest system updates UNINSTALLED such an essential part of the system is beyond me! But there it is.

I saw in a different post someone suggest running "apt-get update" and then "apt-get install ubuntu-desktop" to see if anything was missing, and sure enough, it re-installed gnome-panel (along with a bunch of other things apparently missing.)

So now everything seems to be working again.

--Dan

---

