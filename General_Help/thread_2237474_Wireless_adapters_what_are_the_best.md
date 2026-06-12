---
title: "Wireless adapters: what are the best?"
date: 2014-08-02
forum: General Help
---

### Post by daniel146 on 2014-08-02
Ok long story, short. Computer does not have a wireless card built in and my used-to-be adapter fell apart and I don't want to search for an adapter I think will work but won't because I need to update it.
I can't update my computer to get the drivers if I can't connect to the internet now, can I? So I need some suggested adapters that would work without the immediate need for updated drivers.

---

### Post by kc1di on 2014-08-02
The two [on this page]("https://www.thinkpenguin.com/catalog/wireless-networking-gnulinux") should work out of the box.

---

### Post by kurt18947 on 2014-08-02
> **daniel146 said:**
> Ok long story, short. Computer does not have a wireless card built in and my used-to-be adapter fell apart and I don't want to search for an adapter I think will work but won't because I need to update it.
I can't update my computer to get the drivers if I can't connect to the internet now, can I? So I need some suggested adapters that would work without the immediate need for updated drivers.

I don't know that there are any wifi AC adapters that 'work out of the box'.  I also caution about manufacturers changing chipsets without changing model designation; it may that Model ABC works out of the box, Model ABC v.2 does not - different chip set - and the difference may not easy to discern.  Having said that, I've had good luck with RTL8192SU chipset based adapters (TrendNet TEW-649UB)and Atheros AR9271 chipset (Netgear WNA1100).  Another chipset that I've had good luck with is MediaTek's RT5370 which is used in many products, often the 'nano' sized USB adapters. The shortcoming with the RT5370 devices I have are signal strength, where Realtek devices might show 100% signal strength, RT5370 devices might show 50% - 60%.  The speed is still reasonable and I don't get disconnects.  This might be due to my wifi router, dunno.  Hope this is helpful to you.

---

### Post by daniel146 on 2014-08-03
Can you specify which ones exactly? There's much more than two on the link you posted.
Shouldn't these work or do people have experience that says otherwise?
[http://www.amazon.com/gp/aw/d/B003283M6Q/ref=mp_s_a_1_4?qid=1407071600&sr=8-4&pi=AC_SX110_SY165_QL70](http://www.amazon.com/gp/aw/d/B003283M6Q/ref=mp_s_a_1_4?qid=1407071600&sr=8-4&pi=AC_SX110_SY165_QL70)
[http://www.amazon.com/gp/aw/d/B00EQT0YK2/ref=mp_s_a_1_2?qid=1407071600&sr=8-2&pi=SX200_QL40](http://www.amazon.com/gp/aw/d/B00EQT0YK2/ref=mp_s_a_1_2?qid=1407071600&sr=8-2&pi=SX200_QL40)
[http://www.amazon.com/gp/aw/d/B00762YNMG/ref=mp_s_a_1_1?qid=1407071600&sr=8-1&pi=SX200_QL40](http://www.amazon.com/gp/aw/d/B00762YNMG/ref=mp_s_a_1_1?qid=1407071600&sr=8-1&pi=SX200_QL40)
PS sorry for late response been super busy

---

### Post by kc1di on 2014-08-04
all those adapters on that page are certified to work with Linux. 

All the adapters[ on this page]("http://wireless.kernel.org/en/users/Devices/USB") are said to work with Linux.  but may require the installation of correct driver first.
your question originally stated work out of the box.

according to the averts for the adapters that you listed they are supposed to work , but have no experience with any of them - good luck.

---

### Post by kurt18947 on 2014-08-05
> **daniel146 said:**
> Can you specify which ones exactly? There's much more than two on the link you posted.
Shouldn't these work or do people have experience that says otherwise?
[http://www.amazon.com/gp/aw/d/B003283M6Q/ref=mp_s_a_1_4?qid=1407071600&sr=8-4&pi=AC_SX110_SY165_QL70](http://www.amazon.com/gp/aw/d/B003283M6Q/ref=mp_s_a_1_4?qid=1407071600&sr=8-4&pi=AC_SX110_SY165_QL70)
[http://www.amazon.com/gp/aw/d/B00EQT0YK2/ref=mp_s_a_1_2?qid=1407071600&sr=8-2&pi=SX200_QL40](http://www.amazon.com/gp/aw/d/B00EQT0YK2/ref=mp_s_a_1_2?qid=1407071600&sr=8-2&pi=SX200_QL40)
[http://www.amazon.com/gp/aw/d/B00762YNMG/ref=mp_s_a_1_1?qid=1407071600&sr=8-1&pi=SX200_QL40](http://www.amazon.com/gp/aw/d/B00762YNMG/ref=mp_s_a_1_1?qid=1407071600&sr=8-1&pi=SX200_QL40)
PS sorry for late response been super busy

I'm not sure about the first two - there's no real info about them e.g. which chipset they use.  The 3rd one will work well -- if you [install a patched driver.]("https://github.com/pvaret/rtl8192cu-fixes")  There are several Realtek devices that work well if you install that patched driver.  That does not make them 'works out of the box' IMO.  Something to be aware of - some sellers claim their device "works with linux".  It does, if you build and install the driver.  Their statement may only mean that there's a linux driver available, not that the device is "plug 'n' play". Oh, then when the kernel updates the wifi device breaks and you have to rebuild and reinstall the driver.  I got bit by that crap when I was new to linux.

---

### Post by daniel146 on 2014-08-08
Hey guys, I'm here because I've been having problems ([you can check here if you want]("http://ubuntuforums.org/showthread.php?t=2237474&p=13089650#post13089650")). And basically, I bought a new [adapter]("http://www.amazon.com/gp/product/B00JDVRCI0/ref=oh_aui_detailpage_o01_s00?ie=UTF8&psc=1"), but upon receiving it today: it does not work and Lubuntu refuses to recognize if the software is in. Basically, any suggestions on how to fix this? Help is dearly appreciated. Also, according to the distributor the adapter is supposed to start working as soon as it is plugged in [I've tried switching it around the USB slots just to make sure one of them wasn't acting up]
PS I didn't post in my old thread because I didn't want to constantly revive a relatively dead thread whenever I had an update on my situation.

---

### Post by papibe on 2014-08-09
Threads merged.

---

### Post by obake2 on 2014-09-05
I'm curious how this is going since I have a desktop computer dualbooting Windows 7 & Linux Mint 17. But no-one uses Linux Mint in this machine since the wireless adapter doesn't seem to work in Mint. It connects to the internet, but then it disconnects in few seconds, and it cannot be enabled again. In the very few seconds that it is connected to the internet, the internet speed is slower than Dial-Up.

The wireless adapter that our family computer is using is a Realtek RTL8188CU Wireless LAN 802.11n USB 2.0.
It doesn't work in Linux Mint so I suspect it doesn't on Ubuntu or other distros either.

---

### Post by kurt18947 on 2014-09-05
> **obake2 said:**
> I'm curious how this is going since I have a desktop computer dualbooting Windows 7 & Linux Mint 17. But no-one uses Linux Mint in this machine since the wireless adapter doesn't seem to work in Mint. It connects to the internet, but then it disconnects in few seconds, and it cannot be enabled again. In the very few seconds that it is connected to the internet, the internet speed is slower than Dial-Up.

The wireless adapter that our family computer is using is a Realtek RTL8188CU Wireless LAN 802.11n USB 2.0.
It doesn't work in Linux Mint so I suspect it doesn't on Ubuntu or other distros either.

I'm not certain but that behavior sounds like a typical RealTek adapter using the 'built-in' driver though they usually work for several minutes before disconnecting.  I tried an RTL8192CU generic adapter with Mint 17 live USB and it worked for perhaps 30 minutes before locking up.  My RTL8188CUs adapter (Edimax 7811Un) didn't do as well, it barely connected.   I looked at [Realtek's current linux driver list]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false") and the RTL8188CU is not listed.  The RTL8188CU**s** is supported by the patched driver on Github found here:

[https://github.com/pvaret/rtl8192cu-fixes](https://github.com/pvaret/rtl8192cu-fixes)

and it works very well.  Realtek only lists a couple linux drivers for all their wifi adapters.  Larry Finger has patches for recently released devices, I don't know that he has anything for the RTL-8188CU.  Perhaps someone who has experience with your device will chip in.

---

### Post by obake2 on 2014-09-16
> **kurt18947 said:**
> Realtek only lists a couple Linux drivers for all their wifi adapters. 

Guess now I know to stay away from Realtek.

Thank you Kurt. :)


Do you know another suggestion (a replacement) by any chance?

---

### Post by SeijiSensei on 2014-09-16
I try to use [Intel parts]("http://www.newegg.com/Intel-Wireless-Adapters/BrandSubCat/ID-1157-31") whenever possible because the drivers are written by Intel and included with the kernel.

---

### Post by kurt18947 on 2014-09-18
> **obake2 said:**
> Guess now I know to stay away from Realtek.

Thank you Kurt. :)


Do you know another suggestion (a replacement) by any chance?

Stay away?  Not really, I think is pretty common in the linux world and probably Windows too.  The thing with Realtek is that the 'baked-in' driver doesn't work great, the driver from Realtek does but Realtek doesn't seem too concerned about keeping their linux driver offered for download current.  The patched Realtek driver on Github works very well for RTL81XX IME.  The only Realtek chipset I've found to work well with the 'baked-in' driver is RTL8192SU.

---

