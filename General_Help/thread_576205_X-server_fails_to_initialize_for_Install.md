---
title: "X-server fails to initialize for Install"
date: 2007-10-15
forum: General Help
---

### Post by keeler1 on 2007-10-15
After getting completely fed up with fedora on my laptop, I decided to go ahead and throw ubuntu on it instead, hoping that I wouldnt have to go through hoops to get the wireless working (surprisingly one of the few easy things in fedora (for my chipset at least))

Anyways I pop it and the Ubuntu logo comes up and then a blue screen which tells me the x-server failed to initialize and I get dropped down to a terminal.  I assume this has something to do with my video card but I dont see why it would work.

My laptop is a Dell E1505 1.66ghz core duo 1 gig ram ATI x1400 vid card with 256 megs and plenty of hard drives space.

So why might the x-server fail and should I download the alternate cd?

---

### Post by overdrank on 2007-10-16
> **keeler1 said:**
> After getting completely fed up with fedora on my laptop, I decided to go ahead and throw ubuntu on it instead, hoping that I wouldnt have to go through hoops to get the wireless working (surprisingly one of the few easy things in fedora (for my chipset at least))

Anyways I pop it and the Ubuntu logo comes up and then a blue screen which tells me the x-server failed to initialize and I get dropped down to a terminal.  I assume this has something to do with my video card but I dont see why it would work.

My laptop is a Dell E1505 1.66ghz core duo 1 gig ram ATI x1400 vid card with 256 megs and plenty of hard drives space.

So why might the x-server fail and should I download the alternate cd?

ATI x1400:

Re: Feisty and Gutsy not working with ATI X1400
This is a solution from [http://www.mikesplanet.net/2007/04/i...4-ati-x-cards/](http://www.mikesplanet.net/2007/04/i...4-ati-x-cards/)
and I listed it on [http://kubuntuforums.net/forums/index.php?topic=3086249](http://kubuntuforums.net/forums/index.php?topic=3086249)

Many people are having problems installing Ubuntu 7.04 (Feisty Fawn) on machine with ATI X**** series video cards. This is caused by this bug that unfortunately could not fixed before the release of Ubuntu 7.04.

This quick guide will get Feisty installed and X.org 7.2 up and running.

Boot using PC (Intel x86) alternate install CD for Ubuntu or Kubuntu.
Start text mode installer and install Ubuntu/Kubuntu.
Finish Install and reboot.
Update package list and upgrade any packages needed.
sudo apt-get update
sudo apt-get dist-upgrade
Install fglrx closed source driver for ATI video cards.
sudo apt-get install xorg-driver-fglrx
Update loaded modules.
sudo depmod -a
Configure /etc/X11/xorg.conf
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv
Reboot
Ubuntu 7.04 should now boot into GDM/KDM.

Hope it helps.Good luck! 
Thanks to Pumalite

---

