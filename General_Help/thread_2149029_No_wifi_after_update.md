---
title: "No wifi after update"
date: 2013-05-27
forum: General Help
---

### Post by DoorGunner on 2013-05-27
Hi All

I updated last night now my wifi will not connect to my router. My windows boot runs fine.... just lost my ubuntu wifi ability :( 

Any ideas?

---

### Post by Charlotte18 on 2013-05-27
Are you able to see your wireless ssid but just not able to connect to it, or does it seem as if the wireless card is down entirely?

---

### Post by DoorGunner on 2013-05-27
Yes. What is happening is my ubuntu boot sees the router and says it is connected to the router. The router on the other hand says it is offline. 

As i mentioned above same machine but windows will connect fine. So did the Ubuntu right up to the update. I tried to remove the WPA2 and just run the router in the clear.... same problem. 

So i know it isnt the wifi card or the router.

---

### Post by Charlotte18 on 2013-05-28
Delete the wifi connection from Ubuntu. Then in the router's interface, change the name of the SSID and the address scheme. In other words, if your address scheme is 192.168.x.x, change it to 172.16.x.x.  After that, see if Ubuntu can connect to the wifi properly.

---

### Post by DoorGunner on 2013-05-28
Hi Charlotte. I just did that. Thanks for tweeking me to properly do my router. 

In this case it didnt change anything. Same old problem. I do see that there is a bug on the driver that has been posted out there. If i can get a long ethernet cable in the next few days i will try reinstalling it. 

Its a wierd problem for sure. It does allow me to connect to the router but no communication with the router at all. But will post back once i have done that.

---

### Post by DoorGunner on 2013-06-05
YEAH!!!!! got it back. I found this thread [http://ubuntuforums.org/showthread.php?t=2132451](http://ubuntuforums.org/showthread.php?t=2132451)

I ran the following codes and it magically reappeared and works :)

sudo modprobe -r rt2800pci
sudo modprobe rt2800pci nohwcrypt=1

I think what happened was the encryption portion of the wifi got switched off some how. So now with the latter code it put it back to the on possition and works great

---

