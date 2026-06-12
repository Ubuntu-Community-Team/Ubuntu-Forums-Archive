---
title: "acer broadcom 4318"
date: 2007-10-26
forum: General Help
---

### Post by SpikeyMike on 2007-10-26
Hi, I have an acer aspire 3023 with a broadcom 4318 wireless card. I have just installed gutsy and when I booted it for the first time the Restricted Drivers Manager asked me if I wanted to install the firmware for my broadcom 43xx chipset so I installed it. it now recognises my wireless card and I configured it to connect to my network, with the SSID, password and static IP address etc but I cannot figure out how to get it to actually connect. I found this howto but not sure what I need to do, do I still need to install the ndiswrapper and acerhk drivers as described in this howto?

[http://ubuntuforums.org/showthread.php?t=197102&highlight=broadcom+4318](http://ubuntuforums.org/showthread.php?t=197102&highlight=broadcom+4318)

Spikey

---

### Post by SpikeyMike on 2007-10-27
please help :confused::(:confused::(

---

### Post by telovoyagarcar on 2007-10-27
im having the same problem with an Aspire 5000
Let me know if you find the solution.

Just so you know.. i've already tried all the stickies and guides in the forums and no one works.
Im thinking about getting another wireless card.

---

### Post by Tau_Lepton on 2007-11-19
I had the same card working in Feisty with ndiswrapper on my Aspire 5002.  It broke when I upgraded to Gutsy a few weeks ago; I think the problem is with acerhk.  Have any of you gotten the wireless light to actually turn on?
Also, the Broadcom 4318 card is one of the few that doesn't really work with the bcm43xx driver.  ndiswrapper is really the only way to go, from what I've heard.

EDIT:

I just got it working - all I did was (re?)add the line 'acerhk' to /etc/modules.  Now if I can just get NetworkManager to play along...

---

