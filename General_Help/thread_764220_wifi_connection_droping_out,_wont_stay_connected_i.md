---
title: "wifi connection droping out, wont stay connected issues"
date: 2008-04-23
forum: General Help
---

### Post by d4t4min3r on 2008-04-23
I just installed 8.04 HH and i have a issue with my wifi connections

im using wusb54gv4  usb wifi linksys and the router is a 54gs

the driver is all set up right by itself using the rf2500 i believe it is but my issue is, when it does connect, the connection seems to be very week and it drops out every 10 seconds or so. It finds all the networks in range and lets me connect usually but it just drops out

doing sudo dhclient wlan0 gives me
unable to resolve host Home
not sure what this means

when i look at the connection propertys its all right, has an ipaddress and all that and when i do ifconfig and iwconfig it all looks good

can anyone please help me

---

### Post by phidia on 2008-04-23
You might want to check [this]("http://ubuntuforums.org/showthread.php?t=588045&highlight=wusb54gv4") out. That how to may give you a better signal with your wifi device. I realize the how to is for gutsy but heron is still in development.

---

