---
title: "Booting from USB on Compaq Presario C700"
date: 2015-12-19
forum: General Help
---

### Post by Jayanth_Krishnamoo on 2015-12-19
Hi,

I've copied the downloaded files in my USB. I have a compaq presario C700 laptop. I'm trying to install Ubuntu in my laptop. My existing OS is Win XP. Can someone kindly give a step by step guideline so that I can help install Ubuntu OS on my laptop?

Your early reply could be very useful.

With warm regards
K.N.Jayanth Krishnamoorthy

P.S. I've burned a DVD and tried that too but of no avail. Please assist.

---

### Post by chrisehb on 2015-12-19
Hi,

You need to make your USB bootable. If you go to windows and download Rufus - [https://rufus.akeo.ie/](https://rufus.akeo.ie/) Once downloaded open and choose the .iso of ubuntu you have downloaded. Create the USB mount and reboot and boot from USB. This should allow you to install.

Chris

---

### Post by oldfred on 2015-12-19
You do not exactly copy downloaded ISO of Ubuntu to flash drive or DVD. You have to use an installer like unetbootin, rufus or many others that formats flash drive (erases it), extracts ISO and makes it bootable by installing a boot loader.

       Also link on how to create a  bootable DVD or USB flash drive, Windows or Ubuntu
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

Depending on how old of an XP system, you may not be able to boot from a flash drive. Does your BIOS have that option? Some may not show it until you  have a correct bootable flash drive. And  boot option may be under hard drives not under USB ports.

Also if older system, it may not run Ubuntu or run it well. Full Ubuntu needs somewhat newer processor and decent video processor.  Older systems work better then with Lubuntu or Xubuntu which have lighter weight gui than Unity is in Ubuntu.

       
 [https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
[http://askubuntu.com/questions/6328/how-do-i-install-ubuntu](http://askubuntu.com/questions/6328/how-do-i-install-ubuntu)
[https://sites.google.com/site/easylinuxtipsproject/first](https://sites.google.com/site/easylinuxtipsproject/first)
Install with screen shots, auto install option
[http://howtoubuntu.org/how-to-install-ubuntu-13-04-raring-ringtail#.UfFD-uHAMfT](http://howtoubuntu.org/how-to-install-ubuntu-13-04-raring-ringtail#.UfFD-uHAMfT)
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
Install options, Do not use erase entire drive unless that is really what you want. That is entire hard drive not just Windows c: "drive".
[http://www.ubuntu.com/download/help/install-desktop-long-term-support](http://www.ubuntu.com/download/help/install-desktop-long-term-support)

---

