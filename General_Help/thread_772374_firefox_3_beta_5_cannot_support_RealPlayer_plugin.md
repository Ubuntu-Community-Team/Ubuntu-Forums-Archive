---
title: "firefox 3 beta 5 cannot support RealPlayer plugin?"
date: 2008-04-28
forum: General Help
---

### Post by leeyee on 2008-04-28
Hi guys
I upgraded from 7.10 to 8.04 yesterday, firefox 2 + RealPlayer 11 worked fine in 7.10.

Now it seems that firefox beta 5 cannot support RealPlayer plugin, take this website as an example: [http://www.51voa.com/VOA_Standard_English/VOA_Standard_English_21124.html](http://www.51voa.com/VOA_Standard_English/VOA_Standard_English_21124.html)

The audio gives "Not yet supported" in this site. However, use totem plugin can play audio correctly. To make sure it's not caused by pre-installed RealPlayer, i've tried re-install it. Reinstallation didn't resolve the problem.

You guys have got the same situation? Thanks for you help!

---

### Post by Farthing-or-less on 2008-04-28
Same problem, and it's quite unbelievable. Plugin links yield to Totem, no matter what. External player links also yield to Totem. It's as if Real Player doesn't exist. THere must be a work around.

Anyone else?

---

### Post by EarloftheWest on 2008-04-29
Looking for a solution as well.

---

### Post by 5735guy on 2008-04-30
Here is how you get Real Player streaming on Firefox 3 with Hardy.

Download Real Player 11 [http://www.real.com/linux](http://www.real.com/linux)

Open a Terminal and submit the following commands.

cd ~/Desktop

chmod +x RealPlayer11GOLD.bin

sudo ./RealPlayer11GOLD.bin

Real Player 11 will then install.

Go to a Real streaming website ie BBC Radio [http://www.bbc.co.uk/radio/](http://www.bbc.co.uk/radio/)

Select a station you would like to listen to and click Listen Live, a message will then appear asking you to install missing plugins, click on that then select and install the Helix option at the bottom.
Restart Firefox once the software is installed and thats it you are ready to go.It works with Listen Again as well.

IMPORTANT
Uninstall any conflicting packages first ie. Mozilla Mplayer, Totem Mozilla, Gecko Media Player and Gnome Player.

ENJOY. :guitar:

---

### Post by leeyee on 2008-04-30
Hey, that's good, i fixed it.

Just enlightened by 5735guy, I checked apt-get repositories and intalled helix-mozilla-player and helix-player, then restart firefox, it gets back RealPlayer plugin again!

However, you still need to install RealPlayer first i think, because helix-player may not support streams like mp3.

BTW: You must have totem-mozilla uninstalled, otherwise you may get "Not Yet Supported" info again.

---

### Post by jamaas on 2008-05-16
Thanks for this, big help.  Just one complication, it seems to work fine for live streaming but will not broadcast the archived stuff from "listen again" .... any suggestions?

Thanks

Jim


> **5735guy said:**
> Here is how you get Real Player streaming on Firefox 3 with Hardy.

Download Real Player 11 [http://www.real.com/linux](http://www.real.com/linux)

Open a Terminal and submit the following commands.

cd ~/Desktop

chmod +x RealPlayer11GOLD.bin

sudo ./RealPlayer11GOLD.bin

Real Player 11 will then install.

Go to a Real streaming website ie BBC Radio [http://www.bbc.co.uk/radio/](http://www.bbc.co.uk/radio/)

Select a station you would like to listen to and click Listen Live, a message will then appear asking you to install missing plugins, click on that then select and install the Helix option at the bottom.
Restart Firefox once the software is installed and thats it you are ready to go.It works with Listen Again as well.

IMPORTANT
Uninstall any conflicting packages first ie. Mozilla Mplayer, Totem Mozilla, Gecko Media Player and Gnome Player.

ENJOY. :guitar:

---

### Post by 5735guy on 2008-05-17
Try opening up Real Player 11 from Applications > Sound and Video then when it comes to the option click 'Configure Mozilla Helpers' see if that does the trick.

---

### Post by kowsik on 2008-05-17
thanks a lot. I was searching for help on realp player installation. This took care of my problem.

---

