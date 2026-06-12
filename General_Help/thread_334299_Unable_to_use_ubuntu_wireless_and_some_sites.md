---
title: "Unable to use ubuntu wireless and some sites"
date: 2007-01-08
forum: General Help
---

### Post by yopnono on 2007-01-08
Ok here the deal.
If I'm on my dappers then I can't connect to some sites like [www.mysql.com](www.mysql.com) or [www.kjell.com](www.kjell.com) if using the wifi connection. If I connect using wire it works, or if using no encryption.

This I have tried on two different machines. Using dapper wifi drivers, have updated to latest drivers for linux. Have used static IP/DNS, DHCP, but nothing, it just don't work.

However if I boot in to WinXP and connect using wifi it work just fine, and using encrypted wifi connection.

Dell D610 Intel BG 2200 IPW2200
HP Dx6100 D-LINK DWL-G520


-------------------
Odd, but In linux I can only use the WPA and TIP not AES or TIP+AES. If I do then I will not be able to access those sites..
-------------------

---

### Post by ubuntu_demon on 2007-02-22
Did you solve your problem already ?

---

### Post by yopnono on 2007-02-22
> **ubuntu_demon said:**
> Did you solve your problem already ?

Yes I found that I'm not able to use TKIP+AES at the same time for some reson.

---

### Post by ubuntu_demon on 2007-02-22
> **yopnono said:**
> Yes I found that I'm not able to use TKIP+AES at the same time for some reson.

IMHO if you select TKIP+AES first AES will be tried and TKIP after that (if the client card/settings don't support AES).

Are you sure that the router supports AES ?

Did you try wpasupplicant ? If so how did it look like ?

I'm interested because I'm searching for a decent PCI card and the DWL-G520 is an option. See : [http://www.ubuntuforums.org/showthread.php?t=363633](http://www.ubuntuforums.org/showthread.php?t=363633)

---

### Post by yopnono on 2007-02-22
> **ubuntu_demon said:**
> Are you sure that the router supports AES ?

Did you try wpasupplicant ? If so how did it look like ?

I'm interested because I'm searching for a decent PCI card and the DWL-G520 is an option. See : [http://www.ubuntuforums.org/showthread.php?t=363633](http://www.ubuntuforums.org/showthread.php?t=363633)

Intel BG 2200 IPW2200
D-LINK DWL-G520

First I tried the normal wpa

```
network={
	ssid="name"
	psk=code_string
}
```

Then this

```
ap_scan=1
network={
       ssid="name"
       scan_ssid=0
       proto=WPA RSN
       key_mgmt=WPA-PSK
       pairwise=CCMP TKIP
       group=CCMP TKIP
       psk=code_string
}
```

But the same. The router is a linksys pre-n mimo wrt54gx.
It work in windows to use TKIP+AES so I guess the AP is ok, anyhow it's the same, if using only TKIP.

But the odd part is... that it only fails to connect to some sites if using the TKIP+AES and not all, strange..

---

### Post by ubuntu_demon on 2007-02-22
> **yopnono said:**
> Intel BG 2200 IPW2200
D-LINK DWL-G520

First I tried the normal wpa

```
network={
	ssid="name"
	psk=code_string
}
```

Then this

```
ap_scan=1
network={
       ssid="name"
       scan_ssid=0
       proto=WPA RSN
       key_mgmt=WPA-PSK
       pairwise=CCMP TKIP
       group=CCMP TKIP
       psk=code_string
}
```

But the same. The router is a linksys pre-n mimo wrt54gx.
It work in windows to use TKIP+AES so I guess the AP is ok, anyhow it's the same, if using only TKIP.

But the odd part is... that it only fails to connect to some sites if using the TKIP+AES and not all, strange..

WPA can't be used with CCMP. That's what RSN/WPA2 is for. 

You should try this wpasupplicant :
```

network={
ssid="********"
proto=WPA2
key_mgmt=WPA-PSK
pairwise=CCMP
group=CCMP
psk=******
}

```

good luck!

PS :
if you set your router to TKIP+AES this means that your router will accept both TKIP and AES. AES corresponds to CCMP and is stronger than TKIP. If you have any pc's in your wireless network who don't accept AES/CCMP you should set your router to TKIP+AES. Set it to AES only otherwise.

---

### Post by yopnono on 2007-02-22
Have tried to use WPA2/RSN and AES, it's the same, it will not connect to some sites like [www.mysql.com](www.mysql.com) etc,etc.

I can't use AES if I'm on Linux but on MS it works. TKIP will do.

---

### Post by armalite on 2007-02-27
I'm facing quite same problem. I have two wireless cards, one ipw2200 and one Netgear wg511t (madwifi). 

I'm using in my home a dlink wireless ap (dwl-2100ap with 2.20eu firmware that does support wpa and wpa2) and a Gentoo freeradius server. On the notebook above i have Ubuntu Edgy and Win Xp Pro.

In Windows, I can connect (after an upgrade) with the ap via WPA and WPA2, both TKIP and CCMP, both via EAP-PEAP and EAP-TLS.

In edgy after many tries i couldn't connect via ccmp, either wpa or wpa2, only tkip works. Peap or tls doesn't matter, it is the ccmp that don't work (in the past i had problems with a philips base station not working with peap but working with tls... but that's another problem, i solved it by buying a better ap). I tried with the 2 wifi cards above, none of them connect to ap with ccmp.

I have the module ieee80211_crypt_ccmp loaded. 

Has someone tried this in Feisty?

---

### Post by ubuntu_demon on 2007-03-01
> **yopnono said:**
> Have tried to use WPA2/RSN and AES, it's the same, it will not connect to some sites like [www.mysql.com](www.mysql.com) etc,etc.

I can't use AES if I'm on Linux but on MS it works. TKIP will do.

If some sites don't work and others do then it's probably not related to your wireless settings.

Maybe you are using some sort of proxy ?

---

### Post by yopnono on 2007-03-01
> **ubuntu_demon said:**
> If some sites don't work and others do then it's probably not related to your wireless settings.

Maybe you are using some sort of proxy ?

On wire it works fine, unencrypted fine, wpa TKIP fine, wep fine.
No proxy. Have tried different DNS.

The only thing that just don't work is AES and wifi.

---

### Post by maniacmusician on 2007-03-01
> **ubuntu_demon said:**
> If some sites don't work and others do then it's probably not related to your wireless settings.

Maybe you are using some sort of proxy ?
well, OP says the sites don't work only when he's on wireless. When on a wire, it works fine.

That's pretty strange, haven't heard that before.

---

### Post by armalite on 2007-03-01
Really strange... maybe something to do with MTU? In the past i had a pair of dlink dwl-900ap that couldn't send packet bigger than a threshold (i don't remember exactly, maybe something near 1100) with wpa-psk (wep was working, indeed). Had to replace them (they were configured as a bridge) after 2 years because same thing started happening with wep.

I still have problem with aes-ccmp, i can't connect to ap completely.

---

