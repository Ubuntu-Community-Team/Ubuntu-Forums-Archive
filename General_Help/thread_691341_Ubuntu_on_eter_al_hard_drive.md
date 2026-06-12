---
title: "Ubuntu on eter al hard drive ?"
date: 2008-02-08
forum: General Help
---

### Post by Dennis McClary on 2008-02-08
I used my Toshiba laptop with the internal hard drive removed to install Ubuntu 7.10 on a Simpletech 120 GB USB hard drive. It will boot on the Toshiba and on my two Dell Optiplex GX520's(Windows XP) at work. It will not boot on my Dell Inspiron 530N which came with 7.04 installed. I get the message that grub is starting and the Ubuntu start-up screen with the organge progress bar. After the orange bar completes I get a message that local files are being checked and then it stalls. I am at work today and can't post the complete text. Any help? Do I need to disconnect the 530N hard drive and install from it.

Dennis

sorry about the spelling in title

---

### Post by phidia on 2008-02-08
You're booting with the usb drive plugged in, and the bios is set to boot from the usb drive?? And/or you are using the grub from the internal HD install to boot the usb drive?
With the alternate cd you can chose which drive to install grub to and could install grub to the external drive and then have the usb drive boot before the internal-so when it's plugged in the grub on the usb will start.

You may want to look at [this]("https://wiki.ubuntu.com/Booting").

---

### Post by Dennis McClary on 2008-02-08
Yes the BIOS is set to boot from the USB drive. Grub is installed on the external drive for sure because it was installed from a computer with no internal drive connected and the external drive will boot on my computers at the office which do not have Grub installed. 

Dennis

---

