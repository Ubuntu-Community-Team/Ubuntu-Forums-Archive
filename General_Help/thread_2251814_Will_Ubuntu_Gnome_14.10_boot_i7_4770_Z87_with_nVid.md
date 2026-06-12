---
title: "Will Ubuntu Gnome 14.10 boot i7 4770 Z87 with nVidia 750ti ?"
date: 2014-11-06
forum: General Help
---

### Post by macsociety on 2014-11-06
I am running now Ubuntu Gnome 14.04 LTS on my Gigabyte G1 Sniper Z87 based Maingear system with i7 4770 CPU but with built in Intel 4000 video as the 14.04 LTS would not boot from my nVidia 750ti video card.  So for months been using the onboard video.  Tried once to install nvidia driver but it hosed my system and I had to re-install the OS.  So I don't want to chance that again.  Not a linux expert.

Anyway, anyone know if the newer 14.10 that just came out has support for nVidia 750ti so I have a better chance it can boot without black screen from CD so I can re-install and run newer OS but on nVidia card now.

Hate having to only use my onboard memory.

I have read that the drivers could be installed on older 14.04 but like I said, maybe installing the drivers while on onboard memory hoses the system as even if I install newer drive and then turn off onboard video and direct it to nVidia, it still got black screen.

TJ

---

### Post by rbmorse on 2014-11-07
I've got Ubuntu Gnome 14.10 (with Gnome 3.12) running on my ASUS Z97 motherboard with a i7-4790 CPU and Geforce 660 Ti. Not exactly your kit, but close.  No show-stopping problems with either legacy BIOS or UEFI installs.  

The only anomaly I noticed was that the monitor produced a "wrong video mode" error while the LiveDVD was loading itself, but it continued to run and after a couple of minutes the Live session desktop appeared.  At that point everything operated normally.  I could avoid this by setting the "nomodeset" parameter in the GRUB menu at boot time.  On one occasion (out of about ten....I was playing with UEFI options and getting most of them wrong) the DVD ran for a couple of minutes, but no desktop appeared.  In that case typing:

 startx<enter> 

in the blind got things going again.  

In all cases once the Desktop appeared I ran the Ubuntu installer by clicking on the "Install Ubuntu" icon from the live session desktop and everything worked normally.  

After the installation completes my system starts normally with the nVidia free "nouveau" driver, but I install the nVidia 331 (tested) driver from repository using Synaptic at first opportunity.  That works fine. 

I use the 660 Ti on the HDMI output, but I don't think that makes any difference. 

One thing you might check in your BIOS settings...make sure the internal video adapter is not set as the primary or default video otherwise the BIOS will attempt to send output to the Intel video during POST and boot.  Also, I don't trust the "AUTO" setting (never worked properly on the Intel Z79 board I had before I got the Z97) so I change the video related BIOS settings to disable the integrated graphics adapter and make the PCIe graphics the default adapter.

---

### Post by oldfred on 2014-11-07
Some more info on nVidia 750's. Needs newest kernel & nVidia driver versions or using ppa's if not most current version by default.
 Maxwell 750 
[http://ubuntuforums.org/showthread.php?t=2214805](http://ubuntuforums.org/showthread.php?t=2214805)
[http://www.phoronix.com/scan.php?page=article&item=evga_geforce_gtx750&num=1](http://www.phoronix.com/scan.php?page=article&item=evga_geforce_gtx750&num=1)
[http://www.phoronix.com/scan.php?page=article&item=nvidia_maxwell_750linux&num=1](http://www.phoronix.com/scan.php?page=article&item=nvidia_maxwell_750linux&num=1)

---

