---
title: "How do you connect to a wireless network automatically"
date: 2007-11-12
forum: General Help
---

### Post by Sir_Sid on 2007-11-12
Hi changed Knetwork manager to store my network password in plain text so I didnt have to log in to kwallet to connect to a network. Now I am forced to tell Knetwork to connect everytime I boot. Is there a way to get Knetwork to connect automatically

---

### Post by Sir_Sid on 2007-11-14
Anybody with a solution??

---

### Post by tedrogers on 2007-11-17
I need help with this too....I can't get an automatic connection.

Every time I boot or log in I have to supply my WPA2 key and tell it to use WPA2 (it keeps going back to WPA1 all the time).

Anyone?

---

### Post by Sir_Sid on 2007-11-17
Well mine isnt that bad. I just have to right click it and tell it to connect. It remembers my key still

---

### Post by tedrogers on 2007-11-17
I have also posted here:

[http://ubuntuforums.org/showthread.php?t=615718](http://ubuntuforums.org/showthread.php?t=615718)

I've been tinkering all night so far and I've managed to get rid of the inactive network manager applet as shown in the screen image at the last post.

I did this by renaming the wireless network as wlan0 in the interfaces file, but still calling it eth1 in the remaining network manager applet (the one with the green signal strength bars). I don't know why this gets rid of the other net manager applet...but it does and the connections still works.

I still have not yet managed to get it connecting automatically yet though.

Anyone?

---

