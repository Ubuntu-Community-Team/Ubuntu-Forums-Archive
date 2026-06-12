---
title: "3Com OfficeConnect Card Issue"
date: 2005-10-18
forum: General Help
---

### Post by DarthGroznii on 2005-10-18
Hello - 

I have a somewhat old Centrino laptop (HP Compaq nx7000) and to utilise 802.11g signals, I tried to install a 3Com OfficeConnect Card Model 3CRWE154G72 into the PCMCIA slot; which the site says is supported.

The driver recognised the card, but any attempt to activate it has failed - I have tried the card on a Windows based machine and it is functional.  

Please advise.

Regards,

Darth Groznii

---

### Post by DarthGroznii on 2005-10-18
Further information - the card is recognised as eth2 in the Networking panel; activation seems to work, but fails.

I did try reinstalling Ubuntu with the card inserted - however, while the card appeared in the list of networking devices, it failed.  Works fine with the inherent Centrino chipset in the laptop. 

This appears to be a driver issue of some description.  

Thank you for any assistance in advance.

---

### Post by hajk on 2005-10-19
Does the card use an Atmel chip? In that case you must also load the Atmel firmware package.

---

### Post by DarthGroznii on 2005-10-19
It apparently uses a Prism54 chipset.

---

### Post by Pathogenix on 2005-10-19
I feel your pain, you poor fool... I went mad trying to install that card.

To get this card to work under Ubuntu, I had to use two hacks. It doesn't like the prism54 driver (Although this worked under Mandriva) and it adds an extra | to the config file.

There's a how-to here
[http://ubuntuforums.org/showthread.php?t=30680](http://ubuntuforums.org/showthread.php?t=30680)

---

### Post by DarthGroznii on 2005-10-20
I'm going mad myself - I can't find the extra pipe in the conf files - here are their contents - 

10B7:6001.5.conf

> 
NdisVersion|0x50001
Environment|1
BusType|5
mac_address|XX:XX:XX:XX:XX:XX
ndis_version|3Com,06/25/2004, 3.0.7.2

11dMode|0
CardBusBridgeCacheLineSize|0
CardBusBridgeLatencyTimer|0
CCUEnable|0
ConfigProfile|1
DeviceVxDs|3C154G72.sys
EnableRadio|1
FragThresh|2346
LongRetryLimit|4
NitroMode|1
NitroTime|650
PlatformID|14480
PpeCompressEnable|0
PpeConcatEnable|0
PpePdlpEnable|0
PpePiggyBackEnable|0
PRISMIOC|1
PSMode|1
RTSThresh|2347
ShortRetryLimit|7
SilentInstall|1
SSID|ANY
VendorDesc|3Com OfficeConnect Wireless 11g PC Card (3CRWE154G72)

10B7:6001:10B7:6001.5.conf:

> 
NdisVersion|0x50001
Environment|1
BusType|5
mac_address|XX:XX:XX:XX:XX:XX
ndis_version|3Com,06/25/2004, 3.0.7.2

11dMode|0
CardBusBridgeCacheLineSize|0
CardBusBridgeLatencyTimer|0
CCUEnable|0
ConfigProfile|1
DeviceVxDs|3C154G72.sys
EnableRadio|1
FragThresh|2346
LongRetryLimit|4
NitroMode|1
NitroTime|650
PlatformID|14480
PpeCompressEnable|0
PpeConcatEnable|0
PpePdlpEnable|0
PpePiggyBackEnable|0
PRISMIOC|1
PSMode|1
RTSThresh|2347
ShortRetryLimit|7
SilentInstall|1
SSID|ANY
VendorDesc|3Com OfficeConnect Wireless 11g PC Card (3CRWE154G72)


10B7:6001:A727:6001.5.conf:

> 
NdisVersion|0x50001
Environment|1
BusType|5
mac_address|XX:XX:XX:XX:XX:XX
ndis_version|3Com,06/25/2004, 3.0.7.2

11dMode|0
CardBusBridgeCacheLineSize|0
CardBusBridgeLatencyTimer|0
CCUEnable|0
ConfigProfile|1
DeviceVxDs|3C154G72.sys
EnableRadio|1
FragThresh|2346
LongRetryLimit|4
NitroMode|1
NitroTime|650
PlatformID|14480
PpeCompressEnable|0
PpeConcatEnable|0
PpePdlpEnable|0
PpePiggyBackEnable|0
PRISMIOC|1
PSMode|1
RTSThresh|2347
ShortRetryLimit|7
SilentInstall|1
SSID|ANY
VendorDesc|3Com OfficeConnect Wireless 11g PC Card (3CRWE154G72)


I can't see any extra pipe in this.  Am I going blind or mad?

Thanks.

---

### Post by Pathogenix on 2005-10-21
Nope, you seem to have escaped the blight of the extra pipe.

If your power light is on (not the TX/RX, just the faint green glimmer of hope) and your modprobe'ing went according to plan, I'd say try ifup and iwconfig and see what they say.

My card didn't activate either, until I manually called sudo ifup to start the interface, at which point Ubuntu went "Oh yeah... there's a wireless card"

Let me know how you get on, because I've no doubt I'll end up installing the card again at some point, and it's always nice to know what can go wrong.

---

### Post by DarthGroznii on 2005-10-21
It's worth mentioning when I did a list of the ndiswrapper drivers, it said the 3Com driver was invalid. 

There is the faint green glimmer of hope but nothing else.

---

### Post by Pathogenix on 2005-10-21
> There is the faint green glimmer of hope but nothing else.
Then there is faint green light at the end of the tunnel.

start with ndiswrapper -l and check the list of drivers which comes up. If they're all invalid, use ndiswrapper -e to remove them individually.

Now add one at a time with 
ndiswrapper -i
ndiswrapper -l

if the driver is invalid, kill it again. I know that's a very Windows way to look at the problem... take 'em all out, add them one at a time again and see what happens... but at least I didn't tell you to restart and see if it works the next time :)

One of your drivers should show up as working.

Then modprobe ndiswrapper. If it complains that the driver is invalid, congratulations, you just got the extraneous pipe error.

Kill the pipe, then ifup, iwconfig and so forth.

If you get anything new and exciting, post it here and we'll see what we can Google.

---

### Post by DarthGroznii on 2005-10-22
I should clarify what I did - I went into /etc/ndiswrapper and then typed ndiswrapper -l - it said the 3com driver was invalid.   Those three .conf files I posted were in the 3com subfolder.  I did remove the 3com driver for the moment. 

Fortunately I don't have any other ndiswrapper drivers.  Call me a purist, but I tend to be suspicious of anything that involves windows, even if it is just providing a wrapper for a driver.

---

### Post by DarthGroznii on 2005-10-22
By the way, thanks for helping me with this - this is the absolute last issue I have with my Ubuntu setup, when I have this sorted out, I'll be totally up and away.

I am wondering if there is a conflict between having two wireless networks on this laptop - there is the Centrino chipset which is at 802.11b and the card, which I need for 802.11g - I have heard elsewhere that having two network cards can cause a conflict in the routing table.

---

### Post by Pathogenix on 2005-10-22
Okay, really stupid question: which driver did you install? Onmy driver CD I have several, and only one of them actually worked, hence my suggestion that you remove and replace the drivers one by one, doing ndiswrapper  -l each time to see if you got lucky.

---

### Post by DarthGroznii on 2005-10-22
I'll have to double check, but I think there was only one .inf file on the CD.

---

### Post by Pathogenix on 2005-10-22
Well, assuming that I'm not hallucinating,I'll send you the .infs I've got. Just mail me at [email]ZIGpathogenix@ZIGgmail.com[/email]  remove all zig for great justice and working email address.

---

### Post by DarthGroznii on 2005-10-23
I've dropped you a line - thanks again for your help..

---

### Post by DarthGroznii on 2005-10-23
I've managed to rule out a conflict with Centrino wireless networking - I temporarily disabled it by blacklisting the driver, and restarting the 3com card as the only wireless network card.  Still non functional.  

There were other drivers on the CD, Driver.2k, Driver.98, and Driver.ME.  All installations with ndiswrapper failed - they all were invalid, and none had the extra pipe.

---

### Post by Pathogenix on 2005-10-24
If you've tried all three drivers, and they all read as invalid, and you've *definitely* not got the extra pipe then I'm faintly baffled.

I will let you in on my dark secret though: I ended up reinstalling on a hunch that I might have throw one too many bad drivers as ndiswrapper, and the second time through, everything went according to plan.

you might want to check that your card is being detected properly.

---

