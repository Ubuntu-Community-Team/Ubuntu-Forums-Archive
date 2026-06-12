---
title: "Ubuntu 18.04.1 hangs sometimes, while using a browser"
date: 2018-08-29
forum: General Help
---

### Post by karthikeyan.d on 2018-08-29
I recently bought a Dell Inspiron 15 3567 (Intel(R) Core(TM) i3-6006U CPU @ 2.00GHz). It came with 16.04. I upgraded it to 18.04.1. After the upgrade, the system started hanging once in a while. It did not respond to any keyboard input. Every time I had to power it off and on.

All hangs happened while a  browser was running : Firefox or Chrome. When the hangs with Firefox  happened, I was trying to open a link in a new tab by clicking the right  mouse button. With Chrome, the hangs happened when I was watching some  Youtube video. I googled and found the following bug

gnome-shell uses lots of memory, and grows over time
[https://bugs.launchpad.net/gnome-shell/+bug/1672297](https://bugs.launchpad.net/gnome-shell/+bug/1672297)

I decided to monitor free memory. I started a shell script every time I  logged in. It ran "free" once every 10 seconds and logged it in a file.  Nothing happened for a couple of days. Then the system froze  while I was watching a Youtube video on Chrome. I restarted the system  and checked the log. The last entry was

                                    total                used                 free  shared   buff/cache  available
Mem:        3905900       2117768        592588      501012        1195544       1054020 
Swap:       8119292                      0      8119292 

There seemed to have been sufficient memory when the system froze. I  started Firefox and was trying open the bug link (mentioned above) and  the system froze again. The script log showed

                                   total               used                 free        shared  buff/cache    available
Mem:        3905900     1375800     1515952      186780        1014148     2112240 
Swap:       8119292                     0     8119292 

So, the problem does not seem to be because of depletion of memory due to memory leak somewhere.

Is there anything else I can do to figure out the problem here? Some  other tool to use or some other parameter to monitor? How to find out if  this is a s/w or h/w issue?

So far the hangs have happened only while browsers were running. I have  watched movies (using vlc) and saw no hangs. Every time the system hung I  had to power it off and on.

Thanks

---

### Post by karthikeyan.d on 2018-10-05
Looks like this could be a problem that happens only while using the USB Tethering of iPhone.

After the previous post, I did a few experiments. In addition to Gnome3, I tried Unity and MATE with 18.04. Found the problem happening with them too. So I concluded that it is not a desktop issue. I installed 16.04 and the problem happened in that too. So it was not a 18.04 issue. I was thinking that this may be a display driver issue. However, I never saw a freeze while watching movies. Why? Could it be a OS issue? I was not sure.

Then I realized that every time the problem happened, my system was connected to the net. I was using my iPhone to connect, using USB tethering. The next day I connected to my phone using wifi, instead of usb. No freezes seen for the whole day. The next day I connected using usb and the freeze happened after a couple of hours.
This seemed to indicate the problem to be with the USB h/w or s/w or the OS.

So I bought a new 4G internet device that can be connected using USB and wifi. I have used it for the past week via USB and have not seen the freeze so far. That seems to suggest that the problem happens only when iPhone is connected to my system using USB tethering. Since the new device is working well, the problem may not be in the USB area, h/w or s/w. I also saw that the tethering gets disconnected after some time. That port will not work till reboot and I had to switch to another port. I googled and found that there have been problems in Ubuntu with iPhone USB tethering for at least a couple of years. People have reported system freezes and connection disruptions both of which I've seen.

Is this a Ubuntu issue or a iPhone issue? The connection disruptions could be because of iPhone or Ubuntu but I am not sure how iPhone USB tethering can cause Ubuntu system freeze, in both 16.04 and 18.04. I installed Fedora 28 on the same system and used it for a few hours but did not see any system freeze. I did see connection disruptions. Google informs me that Fedora users too have faced system freezes and connection disruptions using iPhone.

See the first line!

---

### Post by #&amp;thj^% on 2018-10-06
> **karthikeyan.d said:**
> 
Is this a Ubuntu issue or a iPhone issue? The connection disruptions could be because of iPhone or Ubuntu but I am not sure how iPhone USB tethering can cause Ubuntu system freeze, in both 16.04 and 18.04. I installed Fedora 28 on the same system and used it for a few hours but did not see any system freeze. I did see connection disruptions. Google informs me that Fedora users too have faced system freezes and connection disruptions using iPhone.

See the first line!
This has been an iPhone issue>>> I USB tether all the time and use a hot spot with my Moto E4 Android on both Arch Linux and Xubuntu 16.04 and 18.04 and 18.10 with no problems.
Also connected with a VPN 
I'm sorry to hear this, as I have friends that report the same as you. :( Time for a new phone maybe LOL)  :)

---

### Post by yuioni on 2018-10-06
not sure where the phone came into this. but i have this problem on both lubuntu 18.04 on a fresh install and windows 10. windows 10 will straight up hang for 5-10 seconds some times longer and then "catch up". lubuntu will just give it's "thinking" symbol when clicking a link or trying to open a new page. firefox or google chrome makes no difference for me. lubuntu has even gave me a 503 time out error. i don't think it's just you.

my config:
core i3 7350k 4.2Ghz
16GB DDR4 3000Mhz
GTX 1050TI
480GB SSD Windows 10
1TB 7200 HDD Lubuntu
3TB 5200 HDD Data Drive

---

