---
title: "Random whitescreens while using computer"
date: 2007-10-10
forum: General Help
---

### Post by Mr. Ksoft on 2007-10-10
I'm relatively new to Ubuntu, and pretty happy with it, except for one big problem.

I'm using the computer just fine and dandy, and then, out of nowhere, the screen goes completely and utterly white.  All I can see is this whiteness, and my hardware stops working (for instance, the keyboard lights and the laser on the bottom of my mouse shut off).  I have to cut power to get it running again.

I can't see any reason it does this, because I was doing a different thing each time.  It's happened three times and I'm afraid to use the OS for too long now because of this.  I tried searching the forums for anything like this but all I can find are problems when X is just being started or when they've tried to enable desktop effects, and I'm just using the computer like normal.

However, I took a look at the system log and these are the last messages it spit out before the random whitescreening, and they're related to my wireless hardware.  While the logs for the previous two days on which it whitescreened seem to have deleted themselves, I think they had similar things listed.

```
Oct 10 21:34:27 ubuntu dhclient: DHCPREQUEST on eth1 to 192.168.1.1 port 67
Oct 10 21:34:27 ubuntu dhclient: DHCPACK from 192.168.1.1
Oct 10 21:34:27 ubuntu NetworkManager: <information>^IDHCP daemon state is now 3 (renew) for interface eth1 
Oct 10 21:34:27 ubuntu dhclient: bound to 192.168.1.101 -- renewal in 39152 seconds.
Oct 10 21:34:53 ubuntu NetworkManager: <information>^Iwpa_supplicant(6193): id='Wafflenet' wpa_ie_len=0 rsn_ie_len=0 caps=0x11 
Oct 10 21:34:53 ubuntu NetworkManager: <information>^Iwpa_supplicant(6193):    skip - no WPA/RSN IE 
Oct 10 21:34:53 ubuntu NetworkManager: <information>^Iwpa_supplicant(6193): 2: 00:16:b6:b6:48:be ssid='linksys' wpa_ie_len=0 rsn_ie_len=0 caps=0x1 
Oct 10 21:34:53 ubuntu NetworkManager: <information>^Iwpa_supplicant(6193):    skip - no WPA/RSN IE 
Oct 10 21:34:53 ubuntu NetworkManager: <information>^Iwpa_supplicant(6193):    selected non-WPA AP 00:18:f8:ff:e7:55 ssid='Wafflenet' 
Oct 10 21:34:53 ubuntu NetworkManager: <information>^Iwpa_supplicant(6193): Already associated with the selected AP. 
Oct 10 21:34:53 ubuntu NetworkManager: <information>^Iwpa_supplicant(6193): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Oct 10 21:34:53 ubuntu NetworkManager: <information>^Iwpa_supplicant(6193): Wireless event: cmd=0x8b06 len=8 
Oct 10 21:34:53 ubuntu NetworkManager: <information>^Iwpa_supplicant(6193): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Oct 10 21:34:53 ubuntu NetworkManager: <information>^Iwpa_supplicant(6193): Wireless event: cmd=0x8b19 len=8 
Oct 10 21:34:53 ubuntu NetworkManager: <information>^Iwpa_supplicant(6193): Received 702 bytes of scan results (3 BSSes) 
Oct 10 21:34:53 ubuntu NetworkManager: <information>^Iwpa_supplicant(6193): Scan results: 3 
Oct 10 21:34:53 ubuntu NetworkManager: <information>^Iwpa_supplicant(6193): Selecting BSS from priority group 0 
Oct 10 21:34:53 ubuntu NetworkManager: <information>^Iwpa_supplicant(6193): 0: 00:15:e9:66:d5:f2 ssid='HellFire' wpa_ie_len=24 rsn_ie_len=0 caps=0x11 
Oct 10 21:34:53 ubuntu NetworkManager: <information>^Iwpa_supplicant(6193):    skip - SSID mismatch 
Oct 10 21:34:53 ubuntu NetworkManager: <information>^Iwpa_supplicant(6193): 1: 00:18:f8:ff:e7:55 ssid='Wafflenet' wpa_ie_len=0 rsn_ie_len=0 caps=0x11 
Oct 10 21:34:53 ubuntu NetworkManager: <information>^Iwpa_supplicant(6193):    skip - no WPA/RSN IE 
Oct 10 21:34:53 ubuntu NetworkManager: <information>^Iwpa_supplicant(6193): 2: 00:16:b6:b6:48:be ssid='linksys' wpa_ie_len=0 rsn_ie_len=0 caps=0x1 
Oct 10 21:34:53 ubuntu NetworkManager: <information>^Iwpa_supplicant(6193):    skip - no WPA/RSN IE 
Oct 10 21:34:53 ubuntu NetworkManager: <information>^Iwpa_supplicant(6193):    selected non-WPA AP 00:18:f8:ff:e7:55 ssid='Wafflenet' 
Oct 10 21:34:53 ubuntu NetworkManager: <information>^Iwpa_supplicant(6193): Already associated with the selected AP. 
```
(By the way, the ssid it should be connecting to is Wafflenet, which is my home wireless network)
I don't know if that log'll be any help, but it's there just in case.

Anyone got an idea why it might be doing this?  I totally prefer Ubuntu over Windows but if I can't find a solution to this problem then I'll have to consider Windows more stable! D:

---

### Post by Mr. Ksoft on 2007-10-12
I hate to bump, but it appears that this topic went unnoticed.

It just happened again.  This time, though, I had vertical gray lines on the screen.

However, the last log message was exactly the same as before:

```
Oct 12 16:53:49 ubuntu NetworkManager: <information>^Iwpa_supplicant(6193): cted AP. 
Oct 12 16:53:49 ubuntu NetworkManager: <information>^Iwpa_supplicant(6193): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Oct 12 16:53:49 ubuntu NetworkManager: <information>^Iwpa_supplicant(6193): Wireless event: cmd=0x8b06 len=8 
Oct 12 16:53:49 ubuntu NetworkManager: <information>^Iwpa_supplicant(6193): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Oct 12 16:53:49 ubuntu NetworkManager: <information>^Iwpa_supplicant(6193): Wireless event: cmd=0x8b19 len=8 
Oct 12 16:53:49 ubuntu NetworkManager: <information>^Iwpa_supplicant(6193): Received 702 bytes of scan results (3 BSSes) 
Oct 12 16:53:49 ubuntu NetworkManager: <information>^Iwpa_supplicant(6193): Scan results: 3 
Oct 12 16:53:49 ubuntu NetworkManager: <information>^Iwpa_supplicant(6193): Selecting BSS from priority group 0 
Oct 12 16:53:49 ubuntu NetworkManager: <information>^Iwpa_supplicant(6193): 0: 00:15:e9:66:d5:f2 ssid='HellFire' wpa_ie_len=24 rsn_ie_len=0 caps=0x11 
Oct 12 16:53:49 ubuntu NetworkManager: <information>^Iwpa_supplicant(6193):    skip - SSID mismatch 
Oct 12 16:53:49 ubuntu NetworkManager: <information>^Iwpa_supplicant(6193): 1: 00:18:f8:ff:e7:55 ssid='Wafflenet' wpa_ie_len=0 rsn_ie_len=0 caps=0x11 
Oct 12 16:53:49 ubuntu NetworkManager: <information>^Iwpa_supplicant(6193):    skip - no WPA/RSN IE 
Oct 12 16:53:49 ubuntu NetworkManager: <information>^Iwpa_supplicant(6193): 2: 00:16:b6:b6:48:be ssid='linksys' wpa_ie_len=0 rsn_ie_len=0 caps=0x1 
Oct 12 16:53:49 ubuntu NetworkManager: <information>^Iwpa_supplicant(6193):    skip - no WPA/RSN IE 
Oct 12 16:53:49 ubuntu NetworkManager: <information>^Iwpa_supplicant(6193):    selected non-WPA AP 00:18:f8:ff:e7:55 ssid='Wafflenet' 
Oct 12 16:53:49 ubuntu NetworkManager: <information>^Iwpa_supplicant(6193): Already associated with the selected AP. 
Oct 12 16:53:49 ubuntu NetworkManager: <information>^Iwpa_supplicant(6193): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Oct 12 16:53:49 ubuntu NetworkManager: <information>^Iwpa_supplicant(6193): Wireless event: cmd=0x8b06 len=8 
Oct 12 16:53:49 ubuntu NetworkManager: <information>^Iwpa_supplicant(6193): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Oct 12 16:53:49 ubuntu NetworkManager: <information>^Iwpa_supplicant(6193): Wireless event: cmd=0x8b19 len=8 
Oct 12 16:53:50 ubuntu NetworkManager: <information>^Iwpa_supplicant(6193): Received 702 bytes of scan results (3 BSSes) 
Oct 12 16:53:50 ubuntu NetworkManager: <information>^Iwpa_supplicant(6193): Scan results: 3 
Oct 12 16:53:50 ubuntu NetworkManager: <information>^Iwpa_supplicant(6193): Selecting BSS from priority group 0 
```

Any ideas?  I highly suspect problems with my wireless, which is the ONLY way this computer can get online.

---

### Post by Mr. Ksoft on 2007-10-14
Once again, I'm bumping this.  I'm quite disappointed that nobody seems to notice (or care, not sure which)

On a whim, I decided to instead try installing drivers for my wireless from [this thread.]("http://ubuntuforums.org/showthread.php?t=405990")  It set me up through ndiswrapper.  However, it still randomly crashes. With different drivers, even.

However, the system log has a different series of messages than before at the second it crashed.

```
Oct 14 15:47:50 ubuntu NetworkManager: <information>^Iwpa_supplicant(6335): 06 len=8 
Oct 14 15:47:50 ubuntu NetworkManager: <information>^Iwpa_supplicant(6335): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Oct 14 15:47:50 ubuntu NetworkManager: <information>^Iwpa_supplicant(6335): Wireless event: cmd=0x8b06 len=8 
Oct 14 15:47:50 ubuntu NetworkManager: <information>^Iwpa_supplicant(6335): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Oct 14 15:47:50 ubuntu NetworkManager: <information>^Iwpa_supplicant(6335): Wireless event: cmd=0x8b06 len=8 
Oct 14 15:47:50 ubuntu NetworkManager: <information>^Iwpa_supplicant(6335): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Oct 14 15:47:50 ubuntu NetworkManager: <information>^Iwpa_supplicant(6335): Wireless event: cmd=0x8b06 len=8 
Oct 14 15:47:50 ubuntu NetworkManager: <information>^Iwpa_supplicant(6335): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Oct 14 15:47:50 ubuntu NetworkManager: <information>^Iwpa_supplicant(6335): Wireless event: cmd=0x8b06 len=8 
Oct 14 15:47:50 ubuntu NetworkManager: <information>^Iwpa_supplicant(6335): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Oct 14 15:47:50 ubuntu NetworkManager: <information>^Iwpa_supplicant(6335): Wireless event: cmd=0x8b06 len=8 
Oct 14 15:47:50 ubuntu NetworkManager: <information>^Iwpa_supplicant(6335): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Oct 14 15:47:50 ubuntu NetworkManager: <information>^Iwpa_supplicant(6335): Wireless event: cmd=0x8b06 len=8 
Oct 14 15:47:50 ubuntu NetworkManager: <information>^Iwpa_supplicant(6335): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Oct 14 15:47:50 ubuntu NetworkManager: <information>^Iwpa_supplicant(6335): Wireless event: cmd=0x8b06 len=8 
Oct 14 15:47:50 ubuntu NetworkManager: <information>^Iwpa_supplicant(6335): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Oct 14 15:47:50 ubuntu NetworkManager: <information>^Iwpa_supplicant(6335): Wireless event: cmd=0x8b06 len=8 
Oct 14 15:47:50 ubuntu NetworkManager: <information>^Iwpa_supplicant(6335): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Oct 14 15:47:50 ubuntu NetworkManager: <information>^Iwpa_supplicant(6335): Wireless event: cmd=0x8b06 len=8 
Oct 14 15:47:50 ubuntu NetworkManager: <information>^Iwpa_supplicant(6335): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
```

(This should probably be moved to Networking & Wireless since all evidence I've found points to my wireless causing the whitescreens)

---

### Post by -grubby on 2007-10-14
> **Mr. Ksoft said:**
> Once again, I'm bumping this.  I'm quite disappointed that nobody seems to notice (or care, not sure which)


people notice,they care but they don't know the answer

---

### Post by MatthewPlanchard on 2007-10-14
I get the white screen whenever I try to enable desktop effects. I haven't found a solution yet, though. If I do I will definitely post it in here.

---

### Post by Mr. Ksoft on 2007-10-14
> **MatthewPlanchard said:**
> I get the white screen whenever I try to enable desktop effects. I haven't found a solution yet, though. If I do I will definitely post it in here.

I'm pretty sure that's unrelated to my problem, because mine is not influenced by Desktop Effects.  Just everyday computer use.

I'm going to go and upgrade to 7.10 and see if any fixes hidden in it make it all work fine.  Otherwise, I'll probably go hang out in Windowsland until a solution is found. =/

---

