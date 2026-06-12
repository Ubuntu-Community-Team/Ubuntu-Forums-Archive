---
title: "Stuck at purple ubuntu screen, can't enter recovery"
date: 2014-01-09
forum: General Help
---

### Post by wilkins24 on 2014-01-09
Hi, after performing some updates and rebooting my computer as requested, I cannot get past the purple screen with the Ubuntu logo and the 5 orange dots. Other threads mention entering recovery mode by holding shift, but this never works for me. I have tried the left shift key, the right, bashing it like a rabid chimp with parkinsons, holding it down before I power the computer on, but nothing works. 

Computer specs:

AMD A10-6800K CPU (technically APU)
Asus F2 A85-M Pro Motherboard
Samsung 840 series 120gb HD
No graphics card (not needed since the CPU has an integrated graphics chip)

I don't really know what to do from here, and I would really like to avoid wiping my drive and performing a fresh install. Everything was working beautifully until this update.

Any help is very greatly appreciated.

---

### Post by emilio.godoyalamos on 2014-01-09
------------------------------Follow this if the startup screen on grub doesn´t appear------------------------------
You will need the ubuntu installation disk (or usb)[URL="https://help.ubuntu.com/community/Grub2/Installing"]
https://help.ubuntu.com/community/Grub2/[/URL]
---------------------------------------------------------------------------------------------------------------------------

Choose the recovery distro when apearing grub2 screen (when choosing a operative system). Choose recovery mode, connect to internet with the terminal ( [http://ubuntuforums.org/showthread.php?t=1469934](http://ubuntuforums.org/showthread.php?t=1469934) )
Afet that enter on the terminal:
sudo apt-get -f autoremove && sudo apt-get update && sudo apt-get upgrade
reboot

---

