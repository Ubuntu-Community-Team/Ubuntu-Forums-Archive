---
title: "Decent power management?"
date: 2013-03-16
forum: General Help
---

### Post by sam_uk on 2013-03-16
Hi all

I live off grid on a 12v solar powered system. I have a Samsung N220 which I believe is pretty efficient. I'd like to make it as good as it can be. I keep the backlight on the minimum my eyes can bear. When plugged into the external 12v DC the laptop thinks it's on mains, but it's not. Ideally I would like:

* Default lowest power settings for everyday use on internal battery or external 12v DC
* Option to turn on max performance manually when I need to compile a kernel or whatever

So far my googling and efforts amount to:

1. Bluetooth on by default is a pain. Tried Editing etc/rc.local file, & added this line:Code: rfkill block bluetooth but bluetooth is still on on a reboot. I hardly ever use bluetooth but do occasionally so don't want to break it by removing the whole bluez stack. Ideas?

2. I installed Powertop and looked at the tunables, great let's make those settings permanent.

3. To make Tunables permenent Google found this [http://sourceforge.net/apps/mediawiki/jupiter/index.php?title=Kernel](http://sourceforge.net/apps/mediawiki/jupiter/index.php?title=Kernel)
but my version of powertop just say's Good/ Bad not the useful string quoted in the above. Am I using it wrong?

4. I installed Jupiter: [http://www.webupd8.org/2011/09/jupiter-applet-finally-available-for.html](http://www.webupd8.org/2011/09/jupiter-applet-finally-available-for.html) and now it pops up little messages seemingly at random saying 'powersave mode' or 'max power mode' or whatever. No applet has appeared on my top bar, clicking the 'lighting' icon in applications seems to do nothing.

Where do I go from here?

Thanks

Sam

---

### Post by sam_uk on 2013-03-16
OK so I followed my own link :)

And found this: [http://www.webupd8.org/2011/04/how-to-re-enable-notification-area.html](http://www.webupd8.org/2011/04/how-to-re-enable-notification-area.html)

After doing that I can now see a Jupiter icon in the bottom right of my screen, partial success! I can now swap modes. Great.

However:

1. In 'powersave' mode my powertop looks like this:
                                                              
   Bad           VM writeback timeout
   Bad           Enable Audio codec power management
   Bad           Enable SATA link power management for /dev/sda
   Bad           Autosuspend for USB device MB525 [Motorola]
   Bad           Autosuspend for USB device WebCam SCB-0340N [Namuga.]
   Bad           Autosuspend for USB device Broadcom Bluetooth 2.1 Device [Broadcom Corp]
   Bad           Autosuspend for USB device EHCI Host Controller [usb1]
   Bad           Autosuspend for USB device UHCI Host Controller [usb2]
   Bad           Autosuspend for USB device UHCI Host Controller [usb3]
   Bad           Autosuspend for USB device UHCI Host Controller [usb4]
   Bad           Autosuspend for USB device UHCI Host Controller [usb5]
   Bad           Runtime PM for PCI Device Intel Corporation NM10/ICH7 Family USB UHCI Controller #1
   Bad           Runtime PM for PCI Device Intel Corporation NM10/ICH7 Family SATA Controller [AHCI mode]
   Bad           Runtime PM for PCI Device Intel Corporation NM10/ICH7 Family PCI Express Port 3
   Bad           Runtime PM for PCI Device Intel Corporation NM10/ICH7 Family PCI Express Port 4
   Bad           Runtime PM for PCI Device Intel Corporation NM10/ICH7 Family High Definition Audio Controller
   Bad           Runtime PM for PCI Device Intel Corporation Atom Processor D4xx/D5xx/N4xx/N5xx Integrated Graphi
   Bad           Runtime PM for PCI Device Intel Corporation NM10/ICH7 Family USB UHCI Controller #2
   Bad           Runtime PM for PCI Device Intel Corporation Atom Processor D4xx/D5xx/N4xx/N5xx DMI Bridge
   Bad           Runtime PM for PCI Device Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller
   Bad           Runtime PM for PCI Device Intel Corporation NM10/ICH7 Family USB UHCI Controller #4
   Bad           Runtime PM for PCI Device Realtek Semiconductor Co., Ltd. RTL8192E/RTL8192SE Wireless LAN Contro

I'd really like to get those to 'good' and keep on reboot.

2. I still have to turn off bluetooth on every reboot.

Thanks

Sam

---

### Post by sam_uk on 2013-03-16
So I found out how to save the powertop recomendations & bluetooth and posted my findings today in a tutorial format: [http://ubuntuforums.org/showthread.php?t=2126259&p=12560405](http://ubuntuforums.org/showthread.php?t=2126259&p=12560405)

---

