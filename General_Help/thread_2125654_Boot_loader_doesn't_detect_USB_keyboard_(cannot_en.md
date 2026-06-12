---
title: "Boot loader doesn't detect USB keyboard (cannot enable legacy filter)"
date: 2013-03-14
forum: General Help
---

### Post by bmass on 2013-03-14
So I've tried trouble-shooting this issue using the following threads:

[http://ubuntuforums.org/showthread.php?t=1372707](http://ubuntuforums.org/showthread.php?t=1372707)
[http://ubuntuforums.org/showthread.php?t=1941785](http://ubuntuforums.org/showthread.php?t=1941785)
[http://askubuntu.com/questions/83286/why-cant-i-choose-ubuntu-at-boot](http://askubuntu.com/questions/83286/why-cant-i-choose-ubuntu-at-boot)
[http://askubuntu.com/questions/83907/how-can-i-boot-into-recovery-mode-if-it-hangs-booting-single-user](http://askubuntu.com/questions/83907/how-can-i-boot-into-recovery-mode-if-it-hangs-booting-single-user)

[http://www.linuxforums.org/forum/installation/31216-boot-loader-problems-usb-keyboard-doesnt-work.html](http://www.linuxforums.org/forum/installation/31216-boot-loader-problems-usb-keyboard-doesnt-work.html)

I actually have the same mobo as the last guy to post in the linuxforums thread and I know that enabling legacy filters will solve the issue but I can't because enabling legacy filters causes the computer to try and boot from the external usb hard drive I have plugged in and the computer will not even boot. It took me quite a while to figure out that disabling legacy filter would fix this issue, but I have no idea of any other way to fix the issue with my hard drive if I have legacy filters enabled. (basically the computer halts at verifying dmi pool data if legacy filters is enabled, unless I disconnect the hard drive).

I saw that someone made boot disks for each of their operating systems and as near as I can tell this is my only solution to this issue. If that's the case I'll just enable legacy filters and unplug and plug the drives back in every time I start the computer, but that is very far from ideal.

I'm completely new to linux so I'm going to try and use the GRUB boot loader instead of Windows Boot Loader to see if I can get keyboard response like that.

Just to clarify, I have keyboard control in linux and windows and my BIOS, but just not in the boot loader so I can't select which OS I want to boot into. I'm using a wireless usb mouse/keyboard combo. I am getting around the issue right now to troubleshoot using a ps/2 keyboard plugged in additionally, but that is just temporary to allow me to boot into ubuntu.

Any help is greatly appreciated. Thanks.

---

### Post by bmass on 2013-03-14
I tried using the following:

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

to switch to GRUB instead of windows bootloader but the tabs for GRUB options are grayed out. I tried de-selecting restore MBR and restarting but GRUB options are still grayed out. Could anyone please point me in the right direction how to use GRUB instead of windows bootloader? This is just to see if the USB keyboard will respond. All of my googling mostly takes me to people trying to use windows bootloader instead of grub.

Thanks.

---

### Post by bmass on 2013-03-14
So my Boot Repair doesn't have the option to reinstall GRUB which I've seen on other people's screenshot of the problem.

After a little more research I've come to understand (I think, correct me if I'm wrong) that GRUB cannot load windows, so the installation sets things up to load the windows boot loader first, which can load windows if selected, and then if Ubuntu is selected, GRUB is loaded to select from different linux distros (which in a default install would just automatically load ubuntu unless you hold shift or esc or something)?

So if this is the case I need to try and find a third-party boot loader that can detect my keyboard? Or perhaps there is a way to have the windows boot loader enabled the usb legacy keyboard filter once it is loaded? The problem is this setting cannot be enabled until after the hard drive boots otherwise the desktop tries to boot from a USB drive.

Alternatively, if I could find another way or setting to tell the computer not to boot from USB devices? I have an ASUS A7N8X-E deluxe motherboard. I have updated to the latest version of the BIOS but as near as I can tell the only setting that controls booting from a USB hard drive is the USB Legacy Keyboard Filter setting. Is there some other way to tell the computer not to boot from USB hard drives? 

Thanks and sorry for all the questions. I'm really new to linux but I'm watching tutorials and stuff in the interim to try and learn as much as I can.

---

### Post by Mark Phelps on 2013-03-15
Sorry, but the BIOS rules ... if you require the USB legacy feature enabled in order for the PC to see the USB keyboard, there is no way around that.

---

### Post by bmass on 2013-03-15
Well the PC can see the keyboard without the feature enabled because I can use that keyboard to navigate through the BIOS. It's just the interim between the BIOS and loading the OS where is can't detect the keyboard. Just in the boot loader.

Also for example, before a boot loader is loaded, if I have a CD in and it says "press any key to boot from CD" I can use the USB keyboard to boot from the CD.

Is it worth my time trying out some third party boot loading software to see if they can detect the keyboard?

Or am I better off trying to see if there is another way to bypass the computer trying to load USB hard drives before the boot protocol? (my boot is set up with cd-rom as first boot, hdd-0 as second boot and all other boots disabled). Thanks

---

