---
title: "USB Problem PLEASE HELP!!!!"
date: 2013-01-09
forum: General Help
---

### Post by bigb0ss on 2013-01-09
I recently updated my Ubuntu, and did not realize until today. But my USB ports are no longer working properly and my devices are not recognizing.  I really need a fix for this problem ASAP! 

*  I always charged my phone on the road via my USB and now it does not work in all 3 ports. (Droid)

*Running 12.04.1 LTS



* I also made a post a week ago regarding a Hard Drive from Western Digital and it was not recognizing, now  it is my cell phone and that ALWAYS worked via USB.


PLEASE HELP!!!!

---

### Post by UltimateCat on 2013-01-09
Hi:

I'm not the expert with Android phones but this site may be of some use.
[http://www.androidcentral.com/tips](http://www.androidcentral.com/tips)
[http://askubuntu.com/questions/111553/usb-ports-not-working-how-do-i-check-for-drivers-and-diagnose-problem](http://askubuntu.com/questions/111553/usb-ports-not-working-how-do-i-check-for-drivers-and-diagnose-problem)
[http://askubuntu.com/questions/231869/universal-usb-doesnt-show-my-usb-port-how-do-i-fix-this](http://askubuntu.com/questions/231869/universal-usb-doesnt-show-my-usb-port-how-do-i-fix-this)


Which Droid is it; make and model?

---

### Post by llamabr on 2013-01-09
Try:

```
sudo rmmod ehci-hcd
```

and then give it another go.. Plug in your device, wait a tick, and copy us the output of:

```
dmesg | tail
```

---

### Post by bigb0ss on 2013-01-09
ERROR: Module ehci_hcd does not exist in /proc/modules


* I get this error when I punch it in the terminal

---

### Post by bigb0ss on 2013-01-09
Motorola Droid Razr Maxx (1st Gen)



and this is what i get when I punch in the 2nd code (even though the 1st code did not work:

user@ChrUbuntu:~$ dmesg | tail
[   24.019368] ath: Regpair used: 0x3a
[   24.019412] cfg80211: Regulatory domain changed to country: US
[   24.019417] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   24.019425] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   24.019432] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[   24.019439] cfg80211:   (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   24.019445] cfg80211:   (5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   24.019452] cfg80211:   (5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   24.019459] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[   34.246364] wlan0: no IPv6 routers present
user@ChrUbuntu:~$

---

### Post by llamabr on 2013-01-09
Ah, then do it 'tother way 'round:

```
sudo modprobe ehci-hcd
```

and give it another go.

---

### Post by bigb0ss on 2013-01-09
user@ChrUbuntu:~$ sudo modprobe ehci-hcd
[sudo] password for user: 
user@ChrUbuntu:~$ dmesg | tail
[   24.019368] ath: Regpair used: 0x3a
[   24.019412] cfg80211: Regulatory domain changed to country: US
[   24.019417] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   24.019425] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   24.019432] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[   24.019439] cfg80211:   (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   24.019445] cfg80211:   (5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   24.019452] cfg80211:   (5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   24.019459] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[   34.246364] wlan0: no IPv6 routers present
user@ChrUbuntu:~$

---

### Post by llamabr on 2013-01-09
awesome.  is your usb working now, then?

---

### Post by bigb0ss on 2013-01-09
and when you say "tick"   ....how long is that ?   haha I need to know exactly...cause I waited like 10 seconds.

---

### Post by llamabr on 2013-01-09
[http://h2g2.com/approved_entry/A689006](http://h2g2.com/approved_entry/A689006)

so is your usb working now?

---

### Post by bigb0ss on 2013-01-09
funny...but still not working ;(

---

### Post by llamabr on 2013-01-09
Well, I'm probably not going to read this thread into its second page, so someone else will need take it up from here.  But in the mean time, sometimes your phone won't charge from usb if it is very low.  Can you confirm that the usb is not working by trying another device?  Again, plug something else in, give it a tick or so, and then post the output of 
```
dmesg | tail
```
That will help the next bloke in helping you to troubleshoot, and etc.  Best of luck to you.

---

### Post by bigb0ss on 2013-01-09
scratch that I plugged in same wire from my old phone and it works. My regular wire will not even charge in the wall with the USB. 


Thanks guys for all your help!

---

