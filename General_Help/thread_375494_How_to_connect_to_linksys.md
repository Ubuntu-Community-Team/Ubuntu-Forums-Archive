---
title: "How to connect to linksys?"
date: 2007-03-03
forum: General Help
---

### Post by mike-db on 2007-03-03
Ok so I just installed Ubuntu on to my computer over windows XP because I got tired of trying to duel-boot, Now my wireless card Was from dell and I usually connected to a linksys router. How do I go about doing that now I tried in the network menu but nothing works. I've tried both types of password, and I don't know how to set up a static ip. :S

---

### Post by FluffyElmo on 2007-03-03
You should first check the wireless compatibility list to see if your card is supported. There is a page just for Dell adapters but since they also sell third party cards you'll want to determine the exact chipset and if it is supported first.
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported")

Assuming your card is being detected and is set-up, then the next step would be to connect to your router via a cable. First you should disable all encryption and password control on the router to see if you can then connect. Some drivers support encryption better than others so connecting to an open access point should be your first order of business.

Check the router adapter list to see if your card is being detected, the router logs may also give information on any connection attempts. Once you're connecting without security you can then add security back in. In the case where encryption or password control is not possible you can filter by mac address to allow only your adapter to connect.

There is also a forum devoted specifically to networking and it may be worth searching through old posts or asking more detailed questions there...
[http://ubuntuforums.org/forumdisplay.php?f=136]("http://ubuntuforums.org/forumdisplay.php?f=136")

Good Luck! Hope it all works out without too much frustration...

---

### Post by mike-db on 2007-03-04
I'm not sure what chipset mine is because it is a USB plugin wireless thinger...

---

### Post by mike-db on 2007-03-04
Here is a link to what I have. 
[http://accessories.us.dell.com/sna/productdetail.aspx?c=us&l=en&s=dhs&cs=19&sku=430-1186](http://accessories.us.dell.com/sna/productdetail.aspx?c=us&l=en&s=dhs&cs=19&sku=430-1186)

And I looked on that page it seems not to work... So am I screwed or something?

---

### Post by NewOldTimer on 2007-03-04
n00b here, but see if this helps   [http://ubuntuforums.org/showthread.php?p=1527712](http://ubuntuforums.org/showthread.php?p=1527712)
out of my league but maybe some help?

---

### Post by mike-db on 2007-03-04
Thanks for the link but I don't get what it means by. "rmmod e100 and all islsm modules" and "modprobe -a ndiswrapper" I'm a linux nub as well. :/

---

### Post by dinkoarun on 2007-03-04
You are most likely using a DELL WLAN card. This is a proprietary driver for which there is no open source drivers.

Luckily through ndiswrapper we can port these drivers over to linux.

This is the guide you should be looking at. Just follow is step by step and see what happens.
[[COLOR="Red"]**DELL WIRELESS GUIDE**[/COLOR]]("http://ubuntu1501.blogspot.com/2007/01/fixing-wifi-on-dell-1501.html")

After that come to this forum and I will let you know how to connect to a WPA network.

---

### Post by mike-db on 2007-03-04
I've been reading this over and it looks like it needs a stable internet connection to install some of the things used in it?

"sudo apt-get updatesudo 
apt-get install build-essentialsudo 
apt-get install linux-headers-`uname -r`
wget **[http://ftp.us.dell.com/network/R140747.EXE](http://ftp.us.dell.com/network/R140747.EXE)**"

Also

"wget **[http://easynews.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.32.tar.gz](http://easynews.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.32.tar.gz)**"

Thing is that I don't have a internet connection with the computer I'm using. My other computer does and its not on a wireless connection. Would I have to use the cord from that computer on my linux one and do this?

---

### Post by mike-db on 2007-03-04
So I've gone threw this and I keep getting erroes with it wants me to use the code
"sudo ndiswrapper -i bcmw15.inf"
I get an error saying...
"sudo ndiswrapper: command not found"
I also get the same error when I enter...
"sudo ndiswrapper -l"
and also on
"sudo ndiswrapper -m"

And when I enet "sudo modprbe ndiswrapper it says it can find a file...
"FATAL: Could not opne '/lib/modules/2.6.17-10-generic/kernel/drivers/net/ndiswrapper.ko': No such file or ditectory"
Now I'm not sure why it would be looking for that when I had to delete it a few steps up...

I've probably gone and done something completely dumb. Now how do I fix that which I have screwed up?

---

### Post by dinkoarun on 2007-03-04
You must install ndiswrapper before you can install the driver. Without installing the ndiswrapper this installation will not take place.

Make sure you went through the step that says

sudo make uninstall

sudo make

&

sudo make install

---

### Post by mike-db on 2007-03-04
I just get an error for that as well..

---

