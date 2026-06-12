---
title: "Ubuntu 19.10 doesn't recognize 2nd monitor (this is different, I promise)"
date: 2019-10-28
forum: General Help
---

### Post by mattbacon2 on 2019-10-28
I'm sure you're all thinking, "This is a duplicate, there are a ton of other posts and they're all solved."
But I've tried all of those solutions, multiple times. The only solution that worked was backing up my data and completely reinstalling Ubuntu.

As far as I can tell, there is no recognition on the most basic level. Xrandr, lshw, and similar programs all seem to overlook the display. :confused:

When I plug the display in to other computers it works, and plugging other displays in to my computer doesn't. And the worst part is that this is only a problem about 50% of the time! :? All of the other times, the display is recognized and it works fine.

Please help! :KS I can provide log files/command outputs if needed.

---

### Post by HermanAB on 2019-10-28
The screen monitor port also has a serial interface similar to i2c.  It seems that this is not working, prolly because of a bad solder joint. So you may need to grab a tool box and get busy...

---

### Post by mattbacon2 on 2019-10-28
I'm not sure it's that. It's never stopped working while I had the computer on. It's only an issue when I reboot at which point it is "decided" whether it will work, which is usually a 50-50 split. Also, the display goes out of sleep before going back into sleep when it's plugged in, though that could be explained with your hypothesis. I'll try wiggling the connector and see if that fixes it.

---

### Post by mattbacon2 on 2019-11-03
Alright, I wiggled the connector and after about three minutes of wiggling it just worked. Thank you!

---

