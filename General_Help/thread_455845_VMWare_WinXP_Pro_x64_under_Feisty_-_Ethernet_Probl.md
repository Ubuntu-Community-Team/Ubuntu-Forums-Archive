---
title: "VMWare WinXP Pro x64 under Feisty - Ethernet Problem"
date: 2007-05-27
forum: General Help
---

### Post by Twintop on 2007-05-27
I have VMWare Player installed and working propperly, and have installed Windows XP Professional x64 as a virtual machine. All of the hardware the virtual machine is detected perfectly fine, except for my sound card (on-board) and my ethernet card (also on board).

My motherboard is a Foxconn NF4UK8AA-8EKRS nForce 4 Ultra. When I attempt to install the ethernet using Windows XP x64 nVidia Forceware drivers, the installer quits completely after the "Perparing Setup" screen closes. Trying to manually select the drivers prompts a message that the drivers are not compatible with my card.

When I let the system attempt to identify a propper driver, it chooses "AMD-8111 10/100 Integrated Ethernet Controller" and says it did not install propperly. 

Has anyone else had issues with their ethernet cards not being detected or working propperly with their 'natural' drivers under VMWare? Or does anyone have any generic drivers that would work for this? My ethernet card is identified as a ["GbE (integrated GbE MAC + Cicada CIS8201 GbE PHY)"]("http://www.alepine.com.au/home/product.jspx?id=1563")

This might be more of a Windows question than an Unbuntu question, but I figured that I'd try here first. :) Thanks!

---

### Post by Twintop on 2007-05-27
Bumping this post for anyone whom might have insight on this problem.

---

### Post by Twintop on 2007-05-28
I'm still not having any luck with VMWare running Windows XP x64, but, I was able to get another virtual machine running Windows XP Professional (32-bit) where networking works. Any insight to why this might not be working propperly under the x64 version would be appreciated. Thanks again!

---

### Post by Twintop on 2007-05-29
I've fixed this problem. The rest of this post is informational for anyone else who might be running in to the same issues.

The main problem was my guestOS value was set to "winXPPro", when it needed to be "winXPPro-64". Also, changing the ethernet device type from jlanced to e1000 allowed it to connect to the network.

---

