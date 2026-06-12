---
title: "Ubuntu 20.04 not detecting display"
date: 2021-06-13
forum: General Help
---

### Post by Acharn on 2021-06-13
When I booted Ubuntu 20.04 today it came up in a lower display resolution than is normal. I was able to force grub to boot up in 1920x1080, but Display Settings are still showing Unknown Display. I have an Nvidia 1050 graphics card, but do not have the native Nvidia drivers installed. I don't do gaming, and have always used the default Linux drivers which have always worked just fine. Since I'm not able to use my PC in its native graphics resolution the problem is not serious, but I really think Ubuntu should be detecting the graphics chip and showing a menu of resolution options as it did before. Any suggestions?

---

### Post by Autodave on 2021-06-13
Some info on your hardware would be helpful.  And how is the monitor connected to the PC?  Lastly, you should probably use the nVidia driver even if you don't game.  Use the driver in the repos though: never get it from nVidia's site!  Go to Additional Drivers and use what ever one is recommended.  That 1050 card should use the newest driver.

---

### Post by Acharn on 2021-06-13
My bad. I've forgotten how to properly report a problem. My monitor is a Generic PnP Monitor, an Acer R240HY. It is connected to an Nvidia GeForce GTX 1050 graphics card through what I think is the HTML port. I don't know how to identify the ports, but I had to buy an adapter to connect the monitor. Recommended resolution on the monitor is 1920x1080, which is what I have been using. I last booted up this installation of Ubuntu about a month ago, and the resolution was automatically detected correctly. I'll look at the Additional Drivers to see what's recommended. The problem occurred before I updated and upgraded the installation, and the update did not cure it.

---

### Post by Autodave on 2021-06-13
Also check your connections then to the monitor.  Unplug and replug them a few times.

---

### Post by Acharn on 2021-06-14
That will have to wait until tomorrow. I'm currently updating my Fedora installation and it's almost suppertime. Fedora, by the way, shows the monitor as "Acer Technologies 24"".

---

