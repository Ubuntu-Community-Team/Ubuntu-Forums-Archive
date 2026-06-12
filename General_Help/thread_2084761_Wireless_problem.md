---
title: "Wireless problem"
date: 2012-11-16
forum: General Help
---

### Post by adytza23 on 2012-11-16
Hello i have an Asus Eeepc 1015bx and i instaled Lubuntu 12.10 on it and my wireless connection keeps connecting and disconecting:( I have the Atheros AW-NE785H wireless card on it. What should i do to fix the problem?

---

### Post by Dennis N on 2012-11-16
This may not solve your problem, but it did fix the same symptoms for me (also with Lubuntu 12.10). However, different wireless card in my case.

Check:

Main Menu > Preferences > Network Connection > Wireless Tab

Select your wireless connection, then Edit button.

In the ipv6 settings tab, 

set **Method = Ignore**

This had been set to something else on installation (alternate installer was used).

After that, the connection was maintained with no further drops.

Good luck

---

### Post by greatsirkain on 2012-11-16
[http://ubuntuforums.org/showthread.php?t=2035007](http://ubuntuforums.org/showthread.php?t=2035007)
^
This guy has a similar problem with the same card, see if any of those suggestions work for you

---

### Post by richardhroth on 2013-01-14
I had the same or similar problem with lubuntu 12.10. Wireless was working fine shortly after install. When I came back to it after a download there was no connection and I could not reconnect.

Possible solution: 

I had set lubuntu to log me in automatically when computer boots. I manually logged out and back in again. Shortly thereafter I was connected wirelessly again.

Just did this - so don't know if it is a fluke, a temporary fix, or a solution.

I had worked a couple days trying to figure out what was wrong.

---

