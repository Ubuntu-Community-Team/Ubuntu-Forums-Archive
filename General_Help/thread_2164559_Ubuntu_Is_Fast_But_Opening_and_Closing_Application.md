---
title: "Ubuntu Is Fast But Opening and Closing Applications Is Slow [PLUS]"
date: 2013-07-31
forum: General Help
---

### Post by shabalabadingdong on 2013-07-31
So today I installed Ubuntu 13.04 today from my flash drive and it is great.  I love it.  My first linux OS. It's fast and all, but opening and closing applications is slow and can be very slow like 4-5 seconds.  And this is not right off boot.  Clicking icons on the status bar isn't quick.  Scrolling in Firefox isn't really snappy.  I installed Ubuntu on my Dell Inspiron 1521 laptop which is quite old now (about 7 years old), and doesn't really have all the new high tech specs to be running newer operating systems really smoothly, but it's runs alright, I have installed the linux kernel 3.10.1 and it seems to have made a okay difference, but not dramatic.  I also have installed preload, and decreased the swappiness value to 5 which helped but, not a lot.  I really want Ubuntu to be really quick and snappy, even with my poor specs (if that is even possible).  I can't install the graphics card drivers they are outdated and they stopped making the drivers for Ubuntu (I'm pretty sure).  I also may have to get more RAM.  Here are my specs.

Memory - 873.9 MB
Processor - AMD Athlon(tm) 64 X2 Dual-Core Processor TK-55 × 2
 Graphics - Gallium 0.4 on ATI RS690 (which on Windows was like ATI X1something...I forgot)
OS Type - 32-bit
Disk- 156.5 GB

-Thanks for any help!

---

### Post by lah7 on 2013-08-01
**Welcome to the community! **It could be the graphic drivers that are slowing down the interface and performance, I've seen this happen on both ATI and Nvidia cards when their additional drivers haven't been installed.
[U]
If you haven't already, try:[/U]
1. Typing **"software"** into the dash and click [B]"Software & Updates"
[/B]2. Click on the **"Additional Drivers"** tab.
3. Install the ATI driver if it is available for installation. If nothing's there, fear not, it'll be somewhere on the net.

_You may wish to use a lighter environment._
The Unity desktop's great, but for older PCs, it could be the cause of this slowdown. I'd suggest trying **LXDE**, which is used by default in Lubuntu. It's great for systems like yours that are not up for running the latest.

The fast way to install this is to use the terminal. Press **CTRL+ALT+T** and type:
```
sudo apt-get install lxde
```
[I]And then enter your password, don't worry if it's not typing, it's just hidden.
[/I]
Once LXDE downloads & installs, log out of your session, and select the Ubuntu icon next to your name to change the desktop environment to LXDE. It should be a lot more snappier, if it's not, it could be your hardware and whether there's something that is slowing down how your system reads and writes.

_You could switch to Lubuntu, which is lightweight, and still Linux at its heart!_
My sister has an over 10 year old notebook and it happily runs Lubuntu 13.04, which uses LXDE and lightweight apps. Unity was slow on that. If you wanted to install Lubuntu's lightweight apps, you could type:
```
sudo apt-get install lubuntu-desktop
```
But if you wanted to switch OS, image the Lubuntu installation media ([http://www.lubuntu.net]("http://www.lubuntu.net/")) to your flash drive, and replicate your steps to install Lubuntu to the hard drive.

---

### Post by shabalabadingdong on 2013-08-01
> **lah7 said:**
> **Welcome to the community! **It could be the graphic drivers that are slowing down the interface and performance, I've seen this happen on both ATI and Nvidia cards when their additional drivers haven't been installed.
[U]
If you haven't already, try:[/U]
1. Typing **"software"** into the dash and click [B]"Software & Updates"
[/B]2. Click on the **"Additional Drivers"** tab.
3. Install the ATI driver if it is available for installation. If nothing's there, fear not, it'll be somewhere on the net.

_You may wish to use a lighter environment._
The Unity desktop's great, but for older PCs, it could be the cause of this slowdown. I'd suggest trying **LXDE**, which is used by default in Lubuntu. It's great for systems like yours that are not up for running the latest.

The fast way to install this is to use the terminal. Press **CTRL+ALT+T** and type:
```
sudo apt-get install lxde
```
[I]And then enter your password, don't worry if it's not typing, it's just hidden.
[/I]
Once LXDE downloads & installs, log out of your session, and select the Ubuntu icon next to your name to change the desktop environment to LXDE. It should be a lot more snappier, if it's not, it could be your hardware and whether there's something that is slowing down how your system reads and writes.

_You could switch to Lubuntu, which is lightweight, and still Linux at its heart!_
My sister has an over 10 year old notebook and it happily runs Lubuntu 13.04, which uses LXDE and lightweight apps. Unity was slow on that. If you wanted to install Lubuntu's lightweight apps, you could type:
```
sudo apt-get install lubuntu-desktop
```
But if you wanted to switch OS, image the Lubuntu installation media ([http://www.lubuntu.net]("http://www.lubuntu.net/")) to your flash drive, and replicate your steps to install Lubuntu to the hard drive.

Thank you very much, there were no Additional drivers, and I'm still searching online, but I'm gonna give Lubuntu a try.

---

