---
title: "Ndiswrapper questions"
date: 2005-10-26
forum: General Help
---

### Post by sfagundes on 2005-10-26
Hi,

I have an Acer Ferrari 4005 which I installed Brezzy on last night.  I got wireless working using ndiswrapper.  But i have to type the commands:

sudo modprobe ndiswrapper
sudo ifdown wlan0
sudo ifup wlan0

every time I boot.  how can i automate this task?

Also how can I decrease the time that ubuntu tries to bring up the network connections during the boot process.  alot of times i am not connected to a network, and it searches for quite a bit.

Thanks!

---

### Post by soul_rebel on 2005-10-26
first question
add ndiswrapper to /etc/modules
second question
use ifplugd

---

