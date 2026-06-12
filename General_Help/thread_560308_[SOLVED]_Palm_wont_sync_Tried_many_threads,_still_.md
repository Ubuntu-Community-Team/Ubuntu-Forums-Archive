---
title: "[SOLVED] Palm wont sync: Tried many threads, still error 32"
date: 2007-09-26
forum: General Help
---

### Post by andb on 2007-09-26
Ive found a lot of good advice in various threads, but nothing has fixed my problem yet. Gnome Pilot App will work, jpilot won't.

I am using a sony Clie PEG-SJ22/E (basically a sony Palm), which worked fine under Edgy. I installed Feisty a few months ago, and need to use the Palm again. At first, no usb device was being created when I connected the Clie, so I added visor to /etc/modules. While this fixed one error condition, I then got this:

$ dmesg
...
[ 1647.592000] usb 2-1: new full speed USB device using uhci_hcd and address 6
[ 1647.760000] usb 2-1: configuration #1 chosen from 1 choice
[ 1647.764000] usb 2-1: palm_os_4_probe - error -32 getting connection info
[ 1647.764000] visor 2-1:1.0: Handspring Visor / Palm OS converter detected
[ 1647.764000] usb 2-1: Handspring Visor / Palm OS converter now attached to ttyUSB0
[ 1647.764000] usb 2-1: Handspring Visor / Palm OS converter now attached to ttyUSB1

$ lsusb
Bus 004 Device 004: ID 054c:0066 Sony Corp. Clie PEG-N7x0C/PEG-T425 PalmOS PDA Serial


I've set the device to be  usb:,  /dev/ttyUSB0, /dev/ttyUSB1  in jpilot. When I activate the sync on jpilot, it hangs at:
****************************************
 Syncing on device usb:
 Press the HotSync button now
 *************************************** 

 /dev/pilot gives an error about the dir not existing, despite its being in the dev file structure.

If I start jpilot from the terminal, I get no kind of error message in the terminal when I press sync, it just does nothing.

I like to use jpilot for editing, so if anyone has some advice, I'd really appreciate it.

---

### Post by jppaynesr on 2007-09-28
I solved the same problem by stopping the gnome pilot daemon while using jpilot. I think the two are arguing over who can talk to the device ( a treo650 in my case). Add the applet to your toolbar to make this easier. 

Having said that, my situation is opposite yours, jpilot works like a dream, VERY fast, but gnome pilot synching to evolution is slow and frequently hangs. Also it is very hard to stop the applet if you have synched previously.

Still some work to be done to make this easy. . .

---

