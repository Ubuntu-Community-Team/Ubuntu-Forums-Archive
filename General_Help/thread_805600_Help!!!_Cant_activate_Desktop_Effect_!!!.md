---
title: "Help!!! Cant activate Desktop Effect !!!"
date: 2008-05-24
forum: General Help
---

### Post by glaivekiddo on 2008-05-24
-Am using Live CD to try Ubuntu, try to use desktop effect but cant seems to get it work.
-At first i thought Live CD dont have DE, but after googling, i see a lot of ppl with live cd hv DE.
-Searched the forum and do what is recommended which is checking the hardware. Here it is:

ubuntu@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation 82X38/X48 Express DRAM Controller
00:01.0 PCI bridge: Intel Corporation 82X38/X48 Express Host-Primary PCI Express Bridge
00:06.0 PCI bridge: Intel Corporation 82X38/X48 Express Host-Secondary PCI Express Bridge
00:19.0 Ethernet controller: Intel Corporation 82566DC-2 Gigabit Network Connection (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IR (ICH9R) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 4 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600 GTS (rev a1)
04:0a.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
ubuntu@ubuntu:~$ compiz
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 

Any help would be appreciated~

---

### Post by zekica on 2008-05-24
You should start 'Restricted Drivers Manager' and install Proprietary nvidia Drivers. Ubuntu doesn't have drivers with 3d acceleration for nvidia cards, so you'll need to install them using the above tool.

After you install them, you should logout and login back (do not restart live CD as it will lose all changes you made).

---

### Post by Forlong on 2008-05-24
I don't think you will be able to use desktop effects on a Live CD when using a Nvidia card.

You *need* to reboot after installing the proprietary drivers to load the proper modules, logging out and back in won't be enough.

I heard there are ways to achieve this somehow but frankly, it's too much of a hassle, installing would be much easier.


P.S. I am able to use desktop effects on the Live CD, because my graphics card is supported by an open source driver that is capable of that -- but people with Nvidia and newer ATI cards are not.

---

### Post by glaivekiddo on 2008-05-24
thx for the reply, erm... i try to do what you guys say, but somehow Restricted Drivers Manager isn't on my admin bar... help plz

---

### Post by Forlong on 2008-05-24
It's called plain *Drivers Manager* now.
But again, it won't do you any good anyway. Just install it to your harddrive, you won't regret it. :)

---

### Post by glaivekiddo on 2008-05-24
> **Forlong said:**
> It's called plain *Drivers Manager* now.
But again, it won't do you any good anyway. Just install it to your harddrive, you won't regret it. :)
do you mean installing ubuntu on my system can enable the desktop effect? i mean if the problem wont solve now, can it be solved after i install it??? thx again

btw i tried to find the drivers manager, the closest i can get is Hardware Drivers, and it doesnt show a thing

---

### Post by Forlong on 2008-05-24
> **glaivekiddo said:**
> do you mean installing ubuntu on my system can enable the desktop effect? i mean if the problem wont solve now, can it be solved after i install it??? thx again
Yes, I do think so. All you have to do is install the proprietary Nvidia driver afterwards (in fact, Ubuntu will tell you on first boot to do so).
> **glaivekiddo said:**
> btw i tried to find the drivers manager, the closest i can get is Hardware Drivers, and it doesnt show a thing
Sorry, I'm on a localized install atm. You are right, "Hardware Drivers" it is.

I don't know why it doesn't offer you anything but I guess it's because you wouldn't be able to use them anyway.

---

### Post by glaivekiddo on 2008-05-24
ok, if you say so, i'll try to install it today, will let you know if it works. thx again.

p/s: is there any link for a user-friendly beginner-ish step-by-step beryl installer? i am kinda scared to use those sudo stuff

---

### Post by Forlong on 2008-05-24
Do not try install Beryl on a recent Ubuntu release.
Beryl is a discontinued project. Most of it got ported to Compiz Fusion, which is installed by default on Ubuntu Hardy (8.04) -- in fact, those are the "desktop effects".

To get all the fancy stuff out of it, see [here]("http://forlong.blogage.de/article/2008/4/26/How-to-set-up-Compiz-Fusion-074")

---

### Post by glaivekiddo on 2008-05-24
alright, maybe i am leaving the desktop topic but i installed ubuntu, somehow the first run wizard freezes on the 2nd step, right after i set my time zone, i only caught a glimse of step 3 which is partman or something like that. i am using another computer to view this forum. once again, thx

---

### Post by Forlong on 2008-05-24
I'd recommend starting a new thread for problems like that...

What version of Ubuntu are you trying to install?
Where did you get it?

It sound like there's a problem with the partition manager.
What happens when you start
```
sudo gparted
``` in a terminal (before running the install routine)?

---

### Post by glaivekiddo on 2008-05-24
i started a new thread in installation and upgrades topic. since you are still here, i am using hardy heron 8.04 LTS. i dont dare to do anything now, i mean can i cancel the wizard and rerun it next time? i cant do the sudo thingy, as i say it freezes


p/s its been freezing for 45 mins ++ already, and you seems to be the only one who knows something

---

### Post by glaivekiddo on 2008-05-24
> **Forlong said:**
> I'd recommend starting a new thread for problems like that...

What version of Ubuntu are you trying to install?
Where did you get it?

It sound like there's a problem with the partition manager.
What happens when you start
```
sudo gparted
``` in a terminal (before running the install routine)?
ok it say lib parted 1.7.1 and a windows popped-up. i try the desktop effect, still not there. i tried appearances>>visual effect>> enable but it says Desktop effects cannot be enabled. help !!!

---

