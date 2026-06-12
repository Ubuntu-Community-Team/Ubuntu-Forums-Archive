---
title: "[SOLVED] For God's sake please tell me one wireless adapter that works on Feisty out"
date: 2007-07-27
forum: General Help
---

### Post by willz06jw on 2007-07-27
As you can tell from the subject line I am coming to my wit's end.  I just want  to buy a wireless adapter that I can plug into my Ubuntu 7.04 computer and it works w/o tinkering.  

Some points:
I am not talking about cards that are attached to motherboard on desktops or laptops.

The page linked below doesn't help me find a name brand card that works out-of-the-box for WEP in 7.04
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

I never want to look at ndiswrapper or have to restart /etc/init.d/networking again

Please help me!
Willz06jw - formerly a sane man

---

### Post by AceofSpades19 on 2007-07-27
its not ubuntu's fault, its the hardware manufactures fault, if it really bothers you just right your own drivers

---

### Post by aysiu on 2007-07-27
On the contrary, on that very page, there's one that has out-of-the-box WEP:
```
 Digicom
USB Wave 54
zd1211rw
?
Yes
Yes
Works without problems in Feisty configured with network-manager and using WEP. Not tested with WPA but SHOULD work fine.
2007-06-23
USB
```

---

### Post by sterilegenie on 2007-07-27
> **willz06jw said:**
> As you can tell from the subject line I am coming to my wit's end.  I just want  to buy a wireless adapter that I can plug into my Ubuntu 7.04 computer and it works w/o tinkering.  

Some points:
I am not talking about cards that are attached to motherboard on desktops or laptops.

The page linked below doesn't help me find a name brand card that works out-of-the-box for WEP in 7.04
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

I never want to look at ndiswrapper or have to restart /etc/init.d/networking again

Play the violins for all of the potential Ubuntu customers that have had the same problem as me and quit...
:-({|=:-({|=:-({|=:-({|=

Please help me!!1!!
Willz06jw - formerly a sane man

So if your not talking about cards that are attached to a desktop or a laptop, what other type of wireless device are you looking to get going?

My belkin F5D7010 works well under 7.04 and have had good luck with dlink cards

---

### Post by dpar on 2007-07-27
D-Link
	

DWL-650
	

?
	

orinoco_cs
	

Yes
	

Yes
	

Yes
	

Automatically detected, setup even asks for the WEP key
	

	

From the same website.

---

### Post by russo.mic on 2007-07-28
You know, i've had Ubuntu on 3 different laptops, and on the last 2 ndiswrapper worked great,even with the dreaded Broadcom hardware, and on my current Apple Macbook Pro madwifi worked flawlessly.

You can go out and spend $120 on Windows XP, then keep paying for apps to do what it is you want.  OR, you can read some howtos.  between the both options, I choose the latter.

Good luck!

Russo

---

### Post by prodezigner on 2007-07-28
My lappy (Lenovo 3000 N100) has an Intel Pro A/B/G card and it works awesome. Kinda shocked me, not use to wireless in Linux.

---

### Post by willz06jw on 2007-07-31
> So if your not talking about cards that are attached to a desktop or a laptop, what other type of wireless device are you looking to get going?

Attached to the motherboard of a desktop or laptop ... in other words I
know that many Intel and Atheros _internal laptop _wireless adapters work out of the box
... and very well out of the box in fact (I use an Acer laptop that works perfectly even with WPA).  

My question was weither there were any PCI cards and/or USB fobs that worked that well.

btw AceOfSpades, I know that it isn't Ubuntu's fault -- but having one working PCI/USB adapter that is officially supported would be good for the Ubuntu community.  I've been doing some reading and I have found out that Dell has been pressuring hardware vendors to make Linux drivers, so we should see some good things in the future.

Here is the list of Wireless Adapters that will work out of the box on Ubuntu that I received from this post:
D-Link DWL-650
Digicom USB Wave 54 zd1211rw
Belkin F5D7010 


Thanks for your help, I will try these out.  I feel that Ubuntu unofficial supported list is poorly organized (Not organized by Ubuntu version number) and in disarray.  I am trying to make my own wiki right now, but I have to have time to update it with these entries.   

[http://tinker-free-ubuntu-hardware.wetpaint.com/]("http://tinker-free-ubuntu-hardware.wetpaint.com/")

Thanks again,
William Howard

---

### Post by willz06jw on 2007-07-31
An Update I called Dell, and they said for their Desktops that they install these adapters to use WPA and WEP out of the box.

Netgear wg311a
pci

Netgear  wpn111a
usb - and smaller range

---

### Post by Panganat on 2007-07-31
I just remedied my wireless woes at the hints provided by e-James to my post **Wireless?= connectionless ** from a week ago.  The info in the links were very good.  The only difficulty (due to being a Newb) was that i did not initially recognized that i had to install ndiswrapper that made the install effortless. See the links that e-james posted in my post to see if they help. my $0.02 as a newb.

---

### Post by willz06jw on 2007-07-31
Panganat,

With some wireless adapters you don't have to install ndiswrapper (Thank Goodness).  I am trying to find out witch adapters work without that piece of software.

Will

---

### Post by xc3RnbFO8P on 2007-07-31
I got wireless working on ubuntu  feisty fawn  live cd ( WUSB54GC Linksys), then I install it on my hd , restart and it was still running.
I update, restarted and it was OK.
Then started Firefox and open a URL, BANG! 
My connection was gone.
I tried another install
Started live cd, No Wireless connection.
Gave up. installed Windows.
Then I was thinking about why it worked first time on a live cd.
So I  tried again, and it worked again with live cd.
But I am not updating again.
It seems that it have to be on clean HD to work, no old Ubuntu leftovers.
Here is some thoughts: 
Something has changes in the kernel
Ipv6, I remember when I couldn't play internet radio after ipv6 update,
have to make changes in Firefox (about:config  ipv6 false to true)
It may sound stupid, but I had to let it out.

---

