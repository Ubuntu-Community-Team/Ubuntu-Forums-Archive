---
title: "It USED to work..."
date: 2007-07-03
forum: General Help
---

### Post by Drate on 2007-07-03
Following this (my own handmade) howto: 

[http://ubuntuforums.org/showthread.php?t=381770](http://ubuntuforums.org/showthread.php?t=381770)

I can get an Edgy machine to work fine with my Linksys WMP54GS Wireless NIC.  Feisty I had to try to add a step as described in the howto... it worked once.  I only got on the internet ONCE.  Then I updated my computer, restarted, and it doesn't work anymore.

It's an old dell, 256 meg RAM, 2 gig processor, Linksys Wireless NIC (WMP54GS).

So, one issue, is I can't get the thing to stop trying to use the bcm43xx driver as an alternate driver (I'm using NDISWrapper).  I have added the line "blacklist bcm43xx" to the "/etc/modprobe.d/blacklist" file.  I don't know what else to do.  I am at wit's end.  My old stuff worked better... grrr.....

---

### Post by Drate on 2007-07-05
*bump*

---

### Post by orb9220 on 2007-07-05
Sorry can't help but you could try and post in Networking & Wireless thread and see if you get help there.

---

### Post by Drate on 2007-07-05
But my immediate problem is making the darn thing stop trying to use the bcm43xx driver.  I want to know why blacklisting doesn't have the same effect in Feisty as it did in Edgy.  Is this a global functionality loss or is only the bcm43xx module being affected?  How can I make it work like it used to?

---

### Post by Drate on 2007-07-09
bumpness

---

### Post by fredj on 2007-07-09
You could open a terminal, type sudo lshw -class network and post the result here together with
your blacklist file.

---

### Post by Drate on 2007-07-14
Okay, first is the result of that command:

 *-network:0             
       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 5
       bus info: pci@01:05.0
       logical name: wlan0
       version: 02
       serial: 00:12:17:74:40:d7
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper driverversion=1.38 firmware=Linksys,12/22/2004, 3.100.46.0 latency=32 link=no multicast=yes wireless=IEEE 802.11g
       resources: iomemory:ed002000-ed003fff irq:20
  *-network:1 DISABLED
       description: Ethernet interface
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: 9
       bus info: pci@01:09.0
       logical name: eth0
       version: 01
       serial: 00:0b:db:28:63:10
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=1.01 latency=32 link=no multicast=yes port=twisted pair
       resources: iomemory:ed000000-ed001fff irq:20

----Now for the blacklist:

# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# buggy driver causes kernel BUG on load (Ubuntu: #78255, #88430)
blacklist r818x
blacklist r8187

# this driver causes problems with the WMP54GS chipset
blacklist bcm43xx

--------And here is a sample of what happens when I try to use wpa_supplicant manually (after uninstalling network manager, I thought perhaps I could get this thing running similarly to how I have it in Puppy Linux 16.1, where it works):

sudo wpa_supplicant -Dwext -i wlan0 -c/etc/wpa_supplicant.conf
Trying to associate with SSID 'linksys_SES_39472'
Associated with 00:13:10:ea:19:d7
WPA: EAPOL-Key Replay Counter did not increase - dropping packet
WPA: EAPOL-Key Replay Counter did not increase - dropping packet
Authentication with 00:13:10:ea:19:d7 timed out.
Trying to associate with SSID 'linksys_SES_39472'
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Associated with 00:13:10:ea:19:d7
WPA: EAPOL-Key Replay Counter did not increase - dropping packet
WPA: EAPOL-Key Replay Counter did not increase - dropping packet
WPA: EAPOL-Key Replay Counter did not increase - dropping packet
Authentication with 00:13:10:ea:19:d7 timed out.
Trying to associate with SSID 'linksys_SES_39472'
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Associated with 00:13:10:ea:19:d7
CTRL-EVENT-TERMINATING - signal 2 received

---

### Post by Drate on 2007-07-17
i bump thee in th name of HELP!

---

### Post by Drate on 2007-07-18
bump it like it's hoootttt.....

---

### Post by Ayuthia on 2007-07-18
I am not for sure if this will help or not, but what you could do is move the /lib/modules/`uname -r`/kernel/drivers/net/wireless/bcm43xx directory over to your home directory and reload ndiswrapper.  This should prevent the loading of ndiswrapper from finding bcm43xx.

This doesn't explain why you are having the problem and it might still not even fix your problem.  Out of curiosity, are you using a different version of ndiswrapper?  If so, have you tried going back to the version that you used with Edgy?

---

### Post by Drate on 2007-07-19
I will try that, and yes, the version of ndiswrapper that comes with Feisty is different than the one in Edgy.  I had considered reverting to see if that helped, but I would never have thought about the first thing, so we'll see what happens!

---

