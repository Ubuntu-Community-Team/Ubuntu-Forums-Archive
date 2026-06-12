---
title: "Ubuntu for Asus EEE, Intel Atom"
date: 2014-04-07
forum: General Help
---

### Post by traynham on 2014-04-07
I recently inherited an Asus EeePC (Intel Atom at 1.66 Ghz with 1 GB of memory) from my brother.  When I received it, it had apparently not been booted in over a year.  It is running Windows XP SP3 which of course is at end of life.  I thought this would be an excellent opportunity to learn something about Ubuntu and Linux and also create a little gateway machine that could be used for email (Gmail) and other Google apps, remote to my Windows 7 desktop, client to music on my Windows Media Player, DLNA client to my home receiver, and Skype.  I would appreciate any suggestions on what version(s) of Ubuntu to run and how best to install them (no DVD or CD player) and pointers to any other helpful documentation.
 
Thank you very much,
Ken Traynham

---

### Post by Double.J on 2014-04-07
Hi there!

I've got ubuntu up and running on loads of these old N270 chips. Can definitely be done, though it won't like you running compiz at all on the gma950 graphics. 

I've got one samsung NC10 with almost the same specs that has run every version of ubuntu since karmic. Just download the 32 bit version and install from a USB stick using [pendrive linux]("http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows") from the XP install (or create the USB from an existing ubuntu machine.)

As for which distro to use, as I say it will run all versions of ubunutu, but it will be slower, and on the full ubuntu version the tiny screen resolutions become a pain (if you are using a netbook you will want to know that alt+left click lets you grab a window and move it if the menu bar is off the top of the screen ;) )

I usually run LXDE and XFCE based disto's on it now. I do like both lubuntu and xubuntu and would recommend either over a full ubuntu with unity install (if you do go for full ubuntu, sign out and sign in with unity 2d)

Best of luck! 

Keep us up to date

Jj
Ps These netbooks really to benefit from a RAM upgrade to 2GB

---

### Post by zemega on 2014-04-07
> **traynham said:**
>  When I received it, it had apparently not been booted in over a year.

Well, that spells trouble for me. You might need to change the motherboard battery, just an advice. If you keep on getting an error of BIOS not set properly after you removed the big battery and the power supply, your motherboard battery is in bad condition. I have to replace the motherboard battery (or the BIOS battery as some say) for a few laptop that has not been turned on for more that a year.

It will also help if you post your laptop model number, because sometimes there is an extra step that you need to take. for example, on my 1225B, I have to add a few line to the grub setting to solve a big problem, keyboard and touchpad sometimes not working in Ubuntu. And Xubuntu  is light and easy on older laptop. Although Lubuntu is even more lighter, it uses Lubuntu Repository while Xubuntu uses the main Ubuntu repository, thats one of my concern when choosing between Lubuntu and Xubuntu.

---

### Post by carl4926 on 2014-04-07
> **traynham said:**
> I recently inherited an Asus EeePC (Intel Atom at 1.66 Ghz with 1 GB of memory) from my brother.  When I received it, it had apparently not been booted in over a year.  It is running Windows XP SP3 which of course is at end of life.  I thought this would be an excellent opportunity to learn something about Ubuntu and Linux and also create a little gateway machine that could be used for email (Gmail) and other Google apps, remote to my Windows 7 desktop, client to music on my Windows Media Player, DLNA client to my home receiver, and Skype.  I would appreciate any suggestions on what version(s) of Ubuntu to run and how best to install them (no DVD or CD player) and pointers to any other helpful documentation.
 
Thank you very much,
Ken Traynham

It should be fine with Xubuntu 12.04 or Mint 13 XFCE

Creating a bootable USB is easy
You probably have to press Esc to select the boot device, when trying to boot from the USB

[http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows)

---

### Post by CharlesA on 2014-04-08
Model? My Asus 1005 (something) is running Fedora 20 just fine, even after sitting in the closet for over a year.

---

