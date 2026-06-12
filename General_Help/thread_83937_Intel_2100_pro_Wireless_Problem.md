---
title: "Intel 2100 pro Wireless Problem"
date: 2005-10-29
forum: General Help
---

### Post by Billy_McSkintos on 2005-10-29
Under hoary my wireless card 'just worked' now under breezy my wireless card appears to be enabled but cannot pick up any signals.

I am thinking I might need a driver and have found this site:
[http://ipw2100.sourceforge.net](http://ipw2100.sourceforge.net)

I am sure it can help me but I can't understand the install instructions. Spot the n00b.

If you know how to help or can explain the instructions for me then please get in touch. I don't want to go back to M$ but that just works. And the wife is on my back...

Thank you

iwconfig:

unassociated  ESSID:"Monkey"  Nickname:"ipw2100"
          Mode:Managed  Channel=0  Access Point: 00:00:00:00:00:00
          Bit Rate=0 kb/s   Tx-Power:off
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by thom1221 on 2005-10-30
I didn't try hoary, but after I installed Breezy i have the same problem as you. My wireless ethernet appears, I can activate it, set it as default. And it sends and recieves packages, but the signal strength is equal to 0. I've tried to update firmaware and driver, but it didn't help me to solve this problem. My wireless router is set up with hidden SSID and a password. 
I can't explain why, but it's like it's the hidden SSID that gives me the troubles.
Isn't there any guides on the internet to solve this problem? I have really searched a lot around to find help, but still without luck.

The only difference from Billy_McSkintos' problem, is that my ethernet-card is an intel 2200 pro.

---

### Post by sourc3 on 2005-10-30
Have you tried to manually configure your /etc/network/interfaces ?

---

### Post by cbudden on 2005-10-30
Try changing the channel on your router, as this was affecting my signal strength (I have a ipw2200)

---

