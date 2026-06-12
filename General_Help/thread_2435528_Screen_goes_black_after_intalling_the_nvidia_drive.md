---
title: "Screen goes black after intalling the nvidia driver"
date: 2020-01-22
forum: General Help
---

### Post by iozen on 2020-01-22
[COLOR=#000000]Hi all[/COLOR]

[COLOR=#000000]I have a toshiba qosmio x305 q705 laptop which runs only in ubuntu_[/COLOR]
[COLOR=#000000]-nouveau, because i suffer from the chronic problem of black screen whenever i install the nvidia drivers.[/COLOR]

[COLOR=#000000]I have read on the internet that windows users have worked around this problem by a so called rivatuner program which changed the power consumption settings of the gpu (nvidia geforce 9700m gts in my case)[/COLOR]

[COLOR=#000000]I was wondering if it is possible for me to make an underclocking on the settings of my gpu similar to this rivatuner. But the problem is whenever i install the nvidia drivers all i see is the nvidia logo for a couple of seconds and then the screen goes black. I can not run anything and neither can i communicate with the driver or the nvidia-settings to make adjustments. Installing the driver with prescribed downclock settings perhaps could help. Or logging as the root (i can run the computer in the recovery mod) and make adjustments there would be great but in that environment the driver is not loaded as far as i know.[/COLOR]

[COLOR=#000000]So if you can help me run my computer with its original drivers, i will be grateful.[/COLOR]

[COLOR=#000000]Thank you.[/COLOR]

[COLOR=#000000]Computer is Toshiba qosmio x305 q705
[/COLOR]gpu is [COLOR=#000000]nvidia geforce 9700m gts[/COLOR]
[COLOR=#000000]Ubuntu version 18.04.3 lts[/COLOR]
[COLOR=#000000]Software center suggests the the nvidia  driver 340.107[/COLOR]
[COLOR=#000000]Every nvidia driver causes the same problem.

I tried to follow a lead from past. My computer might not be able to communicate with my power supply.
When i run

[/COLOR]```
[COLOR=#000000]
sudo edit /var/log/pwrstatd.log[/COLOR]
```[COLOR=#000000]

I get 

[/COLOR]>  The H2C device can't be used, because the linux system does not support libusb or libusb version is too old.

[COLOR=#000000]
in the file. Could this be the indication of a problem that my gpu and my cpu power levels can not be handled by my computer I don't know.[/COLOR]

---

### Post by Autodave on 2020-01-22
DISREGARD THIS!  BAD INFO BY ME.


Just some info for anyone else that looks at this post:  I did a little research and found this from PC World:  "This $4200 laptop packs a 2.53GHz Intel Core 2 Extreme processor with  four CPU cores; 4GB of RAM; and two nVidia GeForce 9800M GTS video  cards, each with 512MB of RAM, set up in SLI mode. In addition to  running in standard SLI graphics mode, the Qosmio X305-Q708 lets you  dial down to use the integrated GeForce 9400M graphics; this increases  the laptop's battery life (which is just 1 hour, 24 minutes in full  graphics mode) and decreases its heat and noise."

---

### Post by iozen on 2020-01-22
Dear Autodave your search is wrong. My computer is not an [COLOR=#000000]X305-Q708 but an [/COLOR][COLOR=#000000] X305 -Q705. For those who are interested the link to the specs is [/COLOR]https://www.cnet.com/reviews/toshiba-qosmio-x305-q701-review/ .

---

### Post by Autodave on 2020-01-22
I apologize for that confusion.

How is the graphics using the nouveau driver?  Is there a reason why you can't use that?

---

### Post by iozen on 2020-01-22
I can use nouveau fine. Although it is enough for non-demanding applications, does't suffice to play games. I want to play starcraft for example but that requires stronger graphic capabilities. I hope to find a way of using nvidia drivers for this purpose.

---

