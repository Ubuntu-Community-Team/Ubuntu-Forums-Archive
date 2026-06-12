---
title: "Wireless AP detector which works with ndiswrapper?"
date: 2005-06-27
forum: General Help
---

### Post by traherom on 2005-06-27
Sorry if this has been asked (and answered) before, feel free to just point me to the thread. I didn't turn up anything with some searches, but I'm not exactly sure what you'd call it. :neutral: 

I'm wondering if there's an AP detector similar to Kismet out there which will work with a wireless card through ndiswrapper.

---

### Post by rachii on 2005-06-27
try typing```
iwlist scanning
``` into a console

is that what your looking for?

---

### Post by traherom on 2005-06-27
[QUOTE=rachii]try typing```
iwlist scanning
``` into a console

is that what your looking for?[/QUOTE]Well... I don't know exactly. I get:
```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

sit0      Interface doesn't support scanning.

Warning: Driver for device wlan0 recommend version 18 of Wireless Extension,
but has been compiled with version 17, therefore some driver features
may not be available...

wlan0     No scan results
```
So, it might work, but what does the wlan message mean/how can I fix it?


Thanks for the idea!

---

### Post by rachii on 2005-06-30
sorry i havent gotten back to you, i apparently forget to subscribe to this thread, and didnt notice when you reposted, sorry bout that  :\

ok the iwlist scan command scans for wireless AP's.   the different eth0 etc... are your network devices, the first three not being wireless, dont work.  and wlan0 is your wireless nic and it did not find any access points....

if you type ```
ndiswrapper -l
``` into the console what do you get?  that will "list" the drivers installed for your device.  maybe the driver didnt install correctly

---

### Post by traherom on 2005-06-30
[QUOTE=rachii]sorry i havent gotten back to you, i apparently forget to subscribe to this thread, and didnt notice when you reposted, sorry bout that  :\[/quote]No problem. :)

[quote=rachii]and wlan0 is your wireless nic and it did not find any access points....[/quote]Hm... coulda sworn there were two in the area, but I'll check with a winders laptop here...

[quote=rachii]if you type ```
ndiswrapper -l
``` into the console what do you get?  that will "list" the drivers installed for your device.  maybe the driver didnt install correctly[/QUOTE]Yep, it's installed correctly. There thing that I think may be the problem is the 
> Warning: Driver for device wlan0 recommend version 18 of Wireless Extension,
but has been compiled with version 17, therefore some driver features
may not be available...message. Sounds like a driver versioning error, but I pulled it directly from the same laptop's XP installation before I wiped it.

---

### Post by rachii on 2005-06-30
did you get the drivers from the cards cd?   were there different folders with drivers, and different versions.  also when i had to do configure my ndiswrapper, it wouldnt work unless i copied ALL of the files that were with the driver on the cd (there was the driver .inf, and two others)  to my harddrive, then i installed the .inf and it worked when the other files were along side it

---

