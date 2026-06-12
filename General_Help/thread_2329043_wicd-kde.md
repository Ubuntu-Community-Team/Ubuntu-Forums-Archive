---
title: "wicd-kde"
date: 2016-06-27
forum: General Help
---

### Post by togop2 on 2016-06-27
Hi, after installing wicd-kde, I see no ne application that I can run; and no new widget to add to the panel. How do I use it, then?

Thanks

---

### Post by QDR06VV9 on 2016-06-27
Have you  tried to call it in the terminal:
```
wicd-client --tray
``` 
Post back any errors.

---

### Post by X-RED_Tech on 2016-06-27
Any special reason for installing such an old software?
All Ubuntu flavors come with network-manager already. If you're trying to troubleshoot a problematic WiFi card/dongle, installing WICD is most likely NOT THE SOLUTION.

---

### Post by togop2 on 2016-06-27
> **runrickus said:**
> Have you  tried to call it in the terminal:
```
wicd-client --tray
``` 
Post back any errors.

$ wicd-client --tray
The program 'wicd-client' is currently not installed. You can install it by typing:
sudo apt install wicd-gtk

I could try the GTK frontend, but I figured it'd be better to use the KDE one on KDE.

---

### Post by QDR06VV9 on 2016-06-27
Well let us know then.
And also at least look at what X-RED_TECH suggest's

---

### Post by togop2 on 2016-06-28
> **X-RED_Tech said:**
> Any special reason for installing such an old software?
All Ubuntu flavors come with network-manager already. If you're trying to troubleshoot a problematic WiFi card/dongle, installing WICD is most likely NOT THE SOLUTION.

Here's the exact situation: My connection drops very often. I suspect the router. However, network-manager often keeps claiming the connection's up, only I won't be able to connect to internet. wicd doesn't result in more stable connection, but it at least notices when the connection drops. It often doesn't reconnect automatically, but at least I can see when it drops.

I ended up using simply wicd-gtk; if you can suggest a better idea, I'd love to hear it.

---

### Post by X-RED_Tech on 2016-06-29
A better idea would be to actually troubleshoot the problem. Here's a good place to start: [http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)
Easy to follow instructions and a ready made script to gather useful information for the experts to crunch.

Your problem may or may not be router related. It can be the driver for the WiFi and/or incorrect router settings (Always WPA2-AES, no mixed mode and above all avoid TKIP). But I'm just guessing here. If you really care for a solution you should follow the instructions in the link above an open a new thread at Networking&Wireless describing the problem as accurately as you can and adding the results of the script.

---

