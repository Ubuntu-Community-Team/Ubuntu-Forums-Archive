---
title: "[Kubuntu] suddenly boot into black screen"
date: 2017-05-15
forum: General Help
---

### Post by xamus on 2017-05-15
Hi everyone,

Im using Kubuntu 17.04 on my ThinkPad t450. Today suddenly i got some graphic bugs when switching desktops. I thought a reboot could solve my problems, but i got black screen when the system tries to load Plasma Desktop. 
I tried some minor stuff, but cant get any further. Command line works in rec mode. 

For testing i tried my Kubuntu 17.04 Live-USB, which i used to install Kubuntu a few weeks ago and get there graphic bugs too.

Am I facing here a hardware problem?

Im thankfulll for every help!

cheers

---

### Post by mastablasta on 2017-05-15
system specs?

---

### Post by xamus on 2017-05-15
Thinkpad t450
CPU: Intel Core *i5*-5200U
 RAM: 2x4GB DDR3 
SSD: 128GB Samsung
Graphic: Intel HD Graphics 5500

Currently im running the memory test from live USB
In Grub i tried earlier kernel versions with the same bug

EDIT

Memory test without results. The core system is running in the backround and i can use terminal and access my folders. 

Which informaion are mandatory needed?

cheers

---

### Post by xamus on 2017-05-16
To bring this up again:

How can I distiguish between hardware problem and software?

I get the same problems when I boot from Live USB. Is this a strong indicator for a hardware problem?

Im happy for all help!

cheers

---

### Post by mastablasta on 2017-05-16
> **xamus said:**
> To bring this up again:

How can I distiguish between hardware problem and software?


difficult. some hardware errors manifest themselves in a certain way. others are invisible to us.

> 
I get the same problems when I boot from Live USB. Is this a strong indicator for a hardware problem?


yes it could be. but still hard to say. it is not a memorry issue. that one usually manifests in a different way. and since you can't boot off a USB it is also not a disk issue. it could also be a BIOS misconfiguration for the GPU chip.
1. since you can boot into recovery or command line mode can you check the logs in /var/log folder? particulary the boot log dmesg (but look for the old log when you tried to boot into graphics mode. also kernel and system log might reveal something. if GPU has issues it should show up in logs as error. you should be able to see if the GPU drivers are loading well or not.  
2. can you try an older version (16.04 or maybe even 14.04)? is the same issue present?
3. Next you can read the manual for laptops BIOS. then check BIOS for any odd settings. 

As per your specs - you are using intel GPU only. these are usually not problematic at all in Linux and drivers for them are inlcuded in the kernel. newer kernel therefor can mean newer drivers.

---

### Post by xamus on 2017-05-16
Got to use my mobile so sorry for typos

Thank you mastablasta for your reply. 

1) I can boot and start a command line session (in FHD) and looked through the logs. 
Dmesg is empty ("nothing has to be logged yet")
syslog is flooded with network manager, but I got an Intel 7265 so that maybe was there anyway.
Kernerl log I found the following pointing to gpu:
Kernel: GPU hang: ecode 8:0:0x85dffffb, in Xorg[1158], reason: hang on render, action: reset 
...
Drm/i915 resetting chip after you hang

2) yes I tried several times, got 3 options and tried all

3)that's a thing. I didn't changed anything so wasn't aware that a place to look. I will try later and search for interesting things.

I used Kubuntu with this laptop since last year and only upgraded to 17.04 in the hope of better iwlwifi support. I changed nothing in the system since and used the laptop till yesterday when I noticed some flickering&#8203; when I switch desktop , so I rebooted and now I'm here

---

### Post by mastablasta on 2017-05-17
looks more and more like hardware issue. 

i am not sure and i don't have linux at work, but i think there should be a dmesg.old present!?

what about BIOS settings? any options for GPU part? like voltage or frequency or something? also when booting to bios check for temperature values and make sure they are in the comfortable zone for the CPU.

as it is now we found out:
 - that basic (VGA) graphics mode Works
- text mode also works ok
- no hardware changes were made on PC only upgrade.
- older version as well as newer versions of OS do not boot to desktop even in live session.

makes me wonder if it would boot to windows manager such as icewm or fluxbox or openbox.

anyway it all seems to be connected with the GPU. the drivers are not being loaded for some reason. this could be due to some setting, switch (BIOS or driver) or simply the GPU is broken.


what about boot options? have you tried nomodeset ?

---

### Post by xamus on 2017-05-17
Hey,

I searched my bios but there no options for gpu or any sensors. 

I tried boot with the nomodeset option and getting my desktop. 
If I understand the nomodeset right, graphics processing is done by the kernel? 

I installed sensors and looked around, nothing too high, all in the warm 40°C range.

I didn't find a "dmesg.old" in /var/Log

I browsed through the gpu-manager.log

"Is Intel loaded? Yes
Is Boot VGA? Yes
Error: can't access /sys/bus/PCI/devices/0000:00:02.0/driver 
The device is not bound to any driver. Skipping...
Error: failed to open /dev/dri 
Last card number =1
Has Intel? No
How many cards? 0
Number of cards has changed!
Has the system changed? Yes
Is Mesa enabled? Yes
Is Mesa egl available? Yes
"
Got to say, this is AFTER I booted with nomodeset!

I updated my backup server with my data. So far, I will try tomorrow to install a windows and see how it works. 

Gladly I got Thinkpad guarantee till 2019 :')

---

### Post by mastablasta on 2017-05-18
ok so sicne you managed to boot with nomodeset it looks like drivers are not being loaded.

there used to be intel drivers installer for linux available. it shouldn't be needed with an older gen chip, but it wouldn't hurt to try it.: [https://01.org/linuxgraphics](https://01.org/linuxgraphics)

have you tried 14.04.1 (and not 14.04.4) with older kernel?: [http://old-releases.ubuntu.com/releases/trusty/](http://old-releases.ubuntu.com/releases/trusty/)

---

### Post by xamus on 2017-05-19
Heyho,

It's hard to download with elinks ;) I will try first a windows install, download is running. Was cut yesterday via my provider for a day.

I tried older kernels and the new kernel headers with normal update. Nothing worked.

Later I will try your suggestion downloading driver from 01.org

I'm very excited to see if windows could boot normally....

EDIT:
Installed Windows and same picture. Windows only boots in basic graphics mode and can't load proper videodrivers. 
So I think the GPU or something on the board died D:

---

