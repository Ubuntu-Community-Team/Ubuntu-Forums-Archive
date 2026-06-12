---
title: "internet down. unable to install xserver update"
date: 2006-08-24
forum: General Help
---

### Post by hemple on 2006-08-24
the latest glitch in the xserver update has really got me wound up. im a noobie with linux ubuntu and i have no idea how to fix it. i followed all of the directions that ppl have posted on the site in the last 2 days. but to no avail.

when i try to install the correction to the x server problem, i get ...' 0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded. i may be an idiot in the linux area but it seems nothing changed. 

my friend logged on as root and the internet was down so that is probably the problem. but he couldnt stay to fix it cuz he is now on vacation (bandsteech)

can anyone help with getting my internet working again strictly from the command line?

---

### Post by meng on 2006-08-24
What sort of connection should you have? Wired/wireless/modem?
What is the output of:
sudo ifconfig

---

### Post by jocko on 2006-08-24
I can't help you with the internet connection, but maybe I can help you revert to an older version of xorg.
To see if you have any old versions of the package, type this in the command line:
```
cd /var/cache/apt/archives/
ls xserver-xorg-core*
```
As long as you haven't manually cleared the cache or set synaptic to delete old packages, you should see something like this:
```
xserver-xorg-core_1%3a1.0.2-0ubuntu10.1_i386.deb
xserver-xorg-core_1%3a1.0.2-0ubuntu10.3_i386.deb
xserver-xorg-core_1%3a1.0.2-0ubuntu10_i386.deb
```
if you only see the *ubuntu10.3_i386.deb, you'll have to fix your internet connection to download the fix, but if you see any of the older ones you can easily install one of them:
```
sudo dpkg -i xserver-xorg-core_1%3a1.0.2-0ubuntu10.1_i386.deb
```

Hope this helps you!

---

### Post by hemple on 2006-08-24
its wireless. and the output is :
eth0    Link encap:Ethernet HWaddr 00:16:D4:34:E0:16
        UP BROADCAST MULTICAST MTU:1500 METRIC:1
        RX packets:0 errors:0 dropped:0 overruns:0 frame:0
        TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
        collisions:0 txqueuelen:1000
        RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lo      Link encap:Local Loopback
        inet addr:127.0.0.1  Mask:255.0.0.0
        inet6 addr:  ::1/128 Scope:Host
        UP LOOPBACK RUNNING   MTU:16436   Metric:1
        RX packets:3 errors:0 dropped:0 overruns:0 frame:0
        TX packets:3 errors:0 dropped:0 overruns:0 carrier:0
        collisions:0 txqueuelen:0
        RX bytes:172 (172.0 b)  TX bytes:172 (172.0 b)

---

### Post by meng on 2006-08-24
Try
sudo iwconfig eth0 essid [ESSID name]
sudo iwconfig eth0 key [WEP key in hex]
sudo ifconfig eth0 up
sudo dhclient eth0

which is what I do to get my wireless connection going.

ping google.com
to see if it works.

---

### Post by coffeecat on 2006-08-24
**hemple**, try what jocko suggested. It's so easy. That should get you back into a GUI. Then you can solve your internet problem and see about updating to the latest (and working) xserver-xorg-core.

---

