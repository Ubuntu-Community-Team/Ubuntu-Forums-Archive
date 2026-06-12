---
title: "NetworkManager doesnt support wpa - acpi/apm doesnt work - hdparm - dvd fails?"
date: 2007-08-21
forum: General Help
---

### Post by newhappyxuser on 2007-08-21
Hi everybody, I have been using first dsl (2.4) and then I moved to latest xubuntu because I heard from its good hardware support.  I have been googling hours and hours to solve these problems with no success this far, that is why I choosed to ask here. It would be nice to someone quickly respond these as my nervous system is halting soon :)

1. Why the laptop batterymeter doesnt appear in any distros I tried, is this a x/xfce problem or acpi/apm problem ? Suspend and hibernation works smoothly though

2. The NetworkManagers network-admin shows only wep-encryption in the list which is bad as wpa-aes is required to good protection. Anyway, the networkmanager should handle wpa automagically as stated here: [https://help.ubuntu.com/community/WifiDocs/NetworkManager](https://help.ubuntu.com/community/WifiDocs/NetworkManager) and the kernel provides native drivers to my wlan-card. How could I pass by this problem ? 

3. Why the dma-acceleration in hard-drives is disabled by default and how to enable it ? (hdparm --help didnt help :(

4. Both vlc and xine fails to play dvd-movies / hangs after a few second movie is played. Every needed packages such as libdvdcss2 should are installed, dixv-movies plays smoothly as baby.



My computer Armada M700 stands for P3-850MHz, 192Megs of ram, DVD-drive, broadcomm 4138 based wlan-card (yes, native driver exists) and Ati rage mobility 8MB and should be well combatible with linux, even earlier red hats worked in this machine :)

---

### Post by newhappyxuser on 2007-08-21
Btw, i just installed latest kubuntu and all above problems seems to be gone :confused:

---

### Post by newhappyxuser on 2007-08-22
kubuntu was too slow so im trying xubuntu once again.

no ideas everyone ?

---

### Post by stchman on 2007-08-22
> **newhappyxuser said:**
> Hi everybody, I have been using first dsl (2.4) and then I moved to latest xubuntu because I heard from its good hardware support.  I have been googling hours and hours to solve these problems with no success this far, that is why I choosed to ask here. It would be nice to someone quickly respond these as my nervous system is halting soon :)

1. Why the laptop batterymeter doesnt appear in any distros I tried, is this a x/xfce problem or acpi/apm problem ? Suspend and hibernation works smoothly though

2. The NetworkManagers network-admin shows only wep-encryption in the list which is bad as wpa-aes is required to good protection. Anyway, the networkmanager should handle wpa automagically as stated here: [https://help.ubuntu.com/community/WifiDocs/NetworkManager](https://help.ubuntu.com/community/WifiDocs/NetworkManager) and the kernel provides native drivers to my wlan-card. How could I pass by this problem ? 

3. Why the dma-acceleration in hard-drives is disabled by default and how to enable it ? (hdparm --help didnt help :(

4. Both vlc and xine fails to play dvd-movies / hangs after a few second movie is played. Every needed packages such as libdvdcss2 should are installed, dixv-movies plays smoothly as baby.



My computer Armada M700 stands for P3-850MHz, 192Megs of ram, DVD-drive, broadcomm 4138 based wlan-card (yes, native driver exists) and Ati rage mobility 8MB and should be well combatible with linux, even earlier red hats worked in this machine :)

What version of Ubuntu are you running?  Feisty supports WPA/WPA2 out of the box.

Edgy needs the wpasupplicant package installed.

DO play DVDs you need the medibuntu libdvdcss package.  Follow my procedures.

Play DVDs
[http://www.stchman.com/dvd_rip.html](http://www.stchman.com/dvd_rip.html)

MP3 playback
[http://www.stchman.com/cd_rip.html](http://www.stchman.com/cd_rip.html)

Bottom article deals with WPA/WPA2 for Edgy
[http://www.stchman.com/ath_drv.html](http://www.stchman.com/ath_drv.html)

I would upgrade that machine to minimum 256MB.

---

### Post by newhappyxuser on 2007-08-23
> **stchman said:**
> What version of Ubuntu are you running?  Feisty supports WPA/WPA2 out of the box.


Yes, that´s why it´s weird, because im running feisty. When I sudo network-admin, there is no wpa/wpa2 available, only wep :(

What is the problem with xubuntu or is the problem between keyboard and monitor..

---

### Post by newhappyxuser on 2007-08-25
> **newhappyxuser said:**
> Yes, that´s why it´s weird, because im running feisty. When I sudo network-admin, there is no wpa/wpa2 available, only wep :(

What is the problem with xubuntu or is the problem between keyboard and monitor..

No one doesnt have still any ideas ?

---

