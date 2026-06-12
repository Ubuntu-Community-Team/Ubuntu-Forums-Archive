---
title: "Alienware AW17R3 Help"
date: 2016-05-17
forum: General Help
---

### Post by lhb1142 on 2016-05-17
Vendor: Alienware (Dell)
Model: AW17R3-7092SLV 17.3" FHD Laptop (6th Generation Intel Core i7, 16 GB RAM, 256 GB SSD + 1 TB HDD) NVIDIA GeForce GTX980M
Received: May 12, 2016
Operating System: Microsoft Windows 10 (Home)
Desired Operating System: Ubuntu Studio 16.04 'Xenial Xerus'

I received an **Alienware AW17R3-7092SLV 17.3" FHD Laptop (6th Generation Intel Core i7, 16 GB RAM, 256 GB SSD + 1 TB HDD) NVIDIA GeForce GTX980M** free of charge (don't ask!) several days ago. This computer is manufactured by Dell. It has Microsoft Windows 10 (Home) installed.

I would like to *completely* replace Windows with Ubuntu Studio 16.04.

However, when I run the 64-bit Live CD [DVD] disk (which is perfect, not corrupted in any way), everything seems to work - except the Wi-Fi.

I am even able, using an Ethernet cable, to access the Internet and install the proprietary NVidia drivers which are on this machine.

But I cannot, no matter what I do, get that computer to connect via Wi-Fi. (The Fn + F2 control doesn't work; the message in the Network information shows that Wi-Fi is disabled but, sometimes after pressing the Fx + F2 keys, the message shows that the Wi-Fi is disabled via a hardware switch and once it shows that message, the message cannot be changed.) Even though I configure the Wi-Fi connection properly (using the proper SSID and WPA2 password) in the Network setting, it does not function.

I should also mention that I tried using the new Xubuntu 16.04 64-bit Live CD (also a DVD) with exactly the same results.

Here are the Wi-Fi Network Adapter particulars:

**Killer Wireless-n/a/ac 1535 Wireless Network Adapter**

**8/23/2015 Driver Version 12.0.0.337**

**Qualcomm Atheros Communications, Inc.**

**PCI bus 60 device 0 functon 0**

I would like to know if, if I were to 'wipe' Windows and install Ubuntu Studio (or Xubuntu or even Ubuntu) whether this device will work with one or all of these operating systems. It certainly doesn't with the Live CD.

I suppose the logical thing to do would be to contact Dell's Linux unit but, as many people have pointed out over the years, this is generally fruitless.

Obviously, if the Live CD doesn't work properly, I do not want to install Ubuntu Studio to this computer - UNLESS there is someone here who can help me do so. I would wish to know exactly what the Wi-Fi connection problem is and how it can be rectified.

I sincerely thank anyone who can give me help with this problem.

---

### Post by pqwoerituytrueiwoq on 2016-05-17
i would recommend use a test HDD for this, last time i tried to get linux on a alienwhere system (unit maybe before dell bought them out) i had some crazy issues like usb being unusable, even though it booted form it or odd audio issues (turned out it has a hardware volume switch) 
you can do a full install to a flash dive or at least 8gb for the sake of testing
i did find this for your wifi chip
[http://www.killernetworking.com/support/knowledge-base/17-linux/20-killer-wireless-ac-in-linux-ubuntu-debian](http://www.killernetworking.com/support/knowledge-base/17-linux/20-killer-wireless-ac-in-linux-ubuntu-debian)

---

