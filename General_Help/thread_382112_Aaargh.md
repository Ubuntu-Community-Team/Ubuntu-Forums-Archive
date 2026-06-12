---
title: "Aaargh"
date: 2007-03-11
forum: General Help
---

### Post by db0 on 2007-03-11
*Note:  This is a crosspost from the Linux Mint Forums as I am running Bianca (based on Ubuntu 6). I am Crossposting here since I was having the main freezing problem in Ubuntu 6 as well, so this might be related.*

I am seriously pissed at the way my linux installation is behaving. 
[list]
[*]First of all, the most annoying thing. My computer keeps freezing (no mouse moving or anything). When it does so, I cannot do anything. Cannot change desktop, cannot kill the X-Server nothing. I have no idea why this happens as it seems to be completely random (closing a program, browsing whatever). Funny thing is that the music from amarok keeps on playing until the current song ends.  Playing from the browser through (such as pandora) kills the music as well.
This is amazingly frustrating, as I do not have any idea where to start looking. The Syslog does not have any indication on what is causing it.
This was happening with Ubuntu as well, but I thought it might have been a freak incident. No luck.

[*]I installed the official Nvidia Drivers using the nvidia script and later dist-upgraded my system. Initially GDM would not load so I thought I just have to recompile the module. Noooo, that would be too easy.
I re-run the script and everything is OK, GDM loads and I work until my computer locks (see previous paragraph). I restard and GDM starts complaining again. Now I have to run this ```
sudo rmmod nvidia && sudo modprobe nvidia
``` every time my computer starts (after it is finished telling me gdm will not load) and then restart gdm

[*]I connect to the internet using a pppoe connection. I use pppoeconf to configure it and with ubuntu it worked like a charm. Now however, almost every time I reboot, pppoe will not start. I have to run pppoeconf once more.
[/list]
So, can someone *please* help me find out what the hell is going on before I give up in frustration?

EDIT: Forgot to mention that I am running Beryl.
Anyway, as a test, I have enabled the NV driver again (which automatically disables Beryl) instead of nvidia and the PC has not frozen yet. Next I'm going to try enabling nvidia without Beryl to see if it helps

---

### Post by zvacet on 2007-03-11
```

```I can help you about net.system>administration>network settings>highlight your modem>properties>select your type of connection>chek upper left box>close.Go to DNS and delete address you see and put your own addresses>close
```
sudo pppoeconf
```
If this doesn´t work then
[http://easylinux.info/wiki/Ubuntu_Edgy#How_to_install_Broadband_ADSL.2FPPPoE_Client_.28RP-PPPoE.29]("http://easylinux.info/wiki/Ubuntu_Edgy#How_to_install_Broadband_ADSL.2FPPPoE_Client_.28RP-PPPoE.29")
Replace Exec=gksudo /opt/rp-pppoe-3.8/go-gui with Exec=gksudo=tkpppoe
Restart.programs>internet>rp-pppoe
If you are not able to get GUI than
```
sudo -i
```
```
cd /opt/rp-pppoe3.8
```
when you are inside just type ./go


P.S.If you have trouble with connection before you do all this you don´t have to run pppoeconf everytime.
```
pon dsl-provider
```
and you will connect

---

