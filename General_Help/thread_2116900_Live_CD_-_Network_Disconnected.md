---
title: "Live CD - Network Disconnected"
date: 2013-02-17
forum: General Help
---

### Post by regfman on 2013-02-17
I made a Live CD 12.10-Desktop-i386.  It works with my dual core five year old asus mobo. I can boot from it and connect to the internet through my Linksys WRTSL554GS router.

I just put together a computer with a Gigabyte GA-H77-DS3H mobo.  When the Ubuntu boots I get to Try Ubuntu and then I get to the desktop but I get "Network Disconnected - you are now offline".

Any ideas?

---

### Post by regfman on 2013-02-17
I see instructions that say I should use a wifi connection if Ubuntu doesn't connect via the ethernet.  But I think my $95 mobo doesn't have built in wifi.   So that option is out.

Is there some driver that I am missing for the Gigabyte mobo that I would need to patch into making a new .iso for the LiveCD disc?

Or maybe the Linksys router's firmware (stock) doesn't talk to Ubuntu on that gigabyte motherboard?

---

### Post by gordintoronto on 2013-02-17
This might be relevant:
[http://askubuntu.com/questions/165192/how-do-i-install-drivers-for-the-atheros-ar8161-ethernet-controller](http://askubuntu.com/questions/165192/how-do-i-install-drivers-for-the-atheros-ar8161-ethernet-controller)

You could run this command: lspci
and paste the output here. And check whether this appears:
Ethernet controller: Atheros Communications Inc. AR8161 Gigabit Ethernet (rev 08)

And yes, the DS3H does not include built-in WiFi.

---

### Post by regfman on 2013-02-18
> **gordintoronto said:**
> 

You could run this command: lspci
and paste the output here. And check whether this appears:
Ethernet controller: Atheros Communications Inc. AR8161 Gigabit Ethernet (rev 08)



Ethernet Controller: Atheros Communications Inc. AR8161 Gigabit Ethernet (rev 10)

Reading the link you referenced the guy was having a problem with 12.04 and it was mentioned that the driver he needed was not in that 12.04 build.  I am using 12.10.  Seems that my Atheros rev 10 is not supported in the Ubuntu 12.10?

---

### Post by gordintoronto on 2013-02-18
It seems likely that 12.10 doesn't support your Ethernet port. You could try 13.04, which is available as Alpha software. It has a later kernel, and that's where device support lives.

---

