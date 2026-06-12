---
title: "Unable to find drivers for my D-Link wifi adapter"
date: 2013-08-24
forum: General Help
---

### Post by Zirts on 2013-08-24
Hi!

So I have this D-Link Wireless N 150 USB adapter. It's product code is DWA-127.

When I try to find drivers for it on Linux, there seems to be none...  Does anyone have an idea where I could find a driver for it or how could I get it working? ..

---

### Post by Zirts on 2013-08-24
Hi!

So I have this D-Link Wireless N 150 USB adapter. It's product code is DWA-127.

When I try to find drivers for it on Linux, there seems to be none...   Does anyone have an idea where I could find a driver for it or how could  I get it working? ..

---

### Post by The Spectre on 2013-08-24
> **Zirts said:**
> Hi!

So I have this D-Link Wireless N 150 USB adapter. It's product code is DWA-127.

When I try to find drivers for it on Linux, there seems to be none...  Does anyone have an idea where I could find a driver for it or how could I get it working? ..
Most of the time you do not need to install any drivers because the Driver for the Hardware is supported by the Linux Kernel.

It looks like you are running Ubuntu 10.10 which uses Linux Kernel 2.6.35 and the Driver for the DWA-127 was not added until Linux Kernel 3.2.0.

You could attempt to update the Kernel but since Ubuntu 10.10 has reached it's End of Life well over a year ago and is no longer receiving Security Updates you would be better off installing Ubuntu 12.04 or Newer which would have a Linux Kernel that would support the DWA-127 (And More).

---

### Post by ibjsb4 on 2013-08-24
Found this; doesn't look good

[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink#USB](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink#USB)

Got some hits here

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=D-Link+Wireless+N+150&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=D-Link+Wireless+N+150&sa=Search&cof=FORID:9)

Good luck

---

### Post by HereInOz on 2013-08-24
While this article applies to Debian rather than Ubuntu, it may give you some clues as to where to go.  

Sorry I can't do better.   If you are really running 10.10, as your profile suggests, it may help if you update to a later version with a later kernel, and you may get some joy.

---

### Post by Cheesemill on 2013-08-24
Threads merged.

Please don't start more than one thread for the same issue as it dilutes the communities ability to help.

---

### Post by Zirts on 2013-08-24
Allrigh, I will download the latest Ubuntu and see if that fixes it. Will report back.

---

### Post by Zirts on 2013-08-24
Okay... So the latest 13.04 Ubuntu understands that I have a Wifi adapter conncted to my PC but it fails to find any wifi connections. Am I screwed?

---

### Post by wildmanne39 on 2013-08-24
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
 wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a file named (wireless-info.txt, or wireless-info.txt.tar.gz) in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the wireless-info.tar.gz file as a zip file. 

If you do not have ethernet either then follow the directions at this link for running the script without internet.
[http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385)
Thanks

---

### Post by Zirts on 2013-11-16
It is pretty weird now, I have two machines with 13.10 and 3.12 Kerner. If I plug the antenna into one of them, it works just like that, no hassle needed. If I plug it into the other one, it does not.. Really strange thing..

---

