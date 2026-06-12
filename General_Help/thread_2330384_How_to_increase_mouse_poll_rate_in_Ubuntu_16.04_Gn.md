---
title: "How to increase mouse poll rate in Ubuntu 16.04 Gnome"
date: 2016-07-11
forum: General Help
---

### Post by arunb on 2016-07-11
Hi,

I just installed Ubuntu 16.04 Gnome on my laptop. I am using a logitech bluetooth mouse, I find that the movement gets laggy sometimes

Earlier I was using 12.04 (Unity) in this I was able to increase the mouse polling rate by using

sudo gedit /etc/modules
add the lines
-r usbhid
usbhid mousepoll=1

To check the rate I did 
cat /sys/module/usbhid/parameters/mousepoll
1

However now I see that 'cat /sys/module/usbhid/parameters/mousepoll' returns an error, no such directory

Please advise how I can increase the rate.

Thanks
a

---

