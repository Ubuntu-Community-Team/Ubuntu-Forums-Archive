---
title: "Wifi-radar"
date: 2008-03-14
forum: General Help
---

### Post by supermelon928 on 2008-03-14
I installed wifi-radar in Gutsy, after switching over from windows a few weeks ago. I'm now trying to use wireless for the first time since switching, and I am not seeing any connections available on wifi-radar. 

Also after telling Terminal to "sudo wifi-radar" it opened wifi-radar but then began spewing this:

"Laptop:~$ sudo wifi-radar
dhclient3 -- version 2>&1
eth1        Interface doesn't support scanning : No such device

eth1        Interface doesn't support scanning : No such device

eth1        Interface doesn't support scanning : No such device

eth1        Interface doesn't support scanning : No such device

eth1        Interface doesn't support scanning : No such device

eth1        Interface doesn't support scanning : No such device

eth1        Interface doesn't support scanning : No such device

eth1        Interface doesn't support scanning : No such device"

and continues repeating that one line until I close wifi-radar.

The first time I had opened the program a few weeks ago, I did not connect to any network but I could see that there were some connections available. Now it does not seem to work at all. Does anyone know what this might be about?

Thanks,
pk

P.s. I should add that I used to be on a wireless connection, and I know the hardware is in my computer.

---

### Post by TimGS on 2008-05-04
Edit /etc/wifi-radar.conf

Change the entry that refers to eth1 to wlan0.

If that doesn't work (you may have to reboot - try it and see) try wlan1.

-- Tim.

---

### Post by supermelon928 on 2008-05-19
(back from college, again)

nothing with either. i doubt i'll ever get it to work. thanks though.

---

