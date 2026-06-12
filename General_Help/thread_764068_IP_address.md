---
title: "IP address"
date: 2008-04-23
forum: General Help
---

### Post by Periswell on 2008-04-23
hi

how do you find out what your ip address is because where ever i look i cannot see it anywhere.

-josh

---

### Post by johnl on 2008-04-23
If you open System -> Administration -> Network Tools and choose your card from the combo box at the top (wlan0/ath0 for wireless, eth0 for wired...), you should see the IP information right there.

Alternatively, to do it from the command line:
ifconfig | grep "inet addr"

Hope this helps!

---

### Post by Fire_Chief on 2008-04-23
On the desktop (Gnome), right click on the Network Manager Icon in the upper right-hand corner (looks like 2 screens) and select Connection Information.

Or you could open a terminal window and type ifconfig. Look for either eth0 or eth1 as the device and then you'll see the IP address in the second line of information.

Cheers!

---

### Post by upthelum on 2008-04-23
> **Periswell said:**
> hi

how do you find out what your ip address is because where ever i look i cannot see it anywhere.

-josh

Open Terminal and type ifconfig then hit enter.

---

