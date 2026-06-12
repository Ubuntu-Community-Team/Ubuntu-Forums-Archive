---
title: "Ubuntu Screen Messes up on Bootup"
date: 2014-11-28
forum: General Help
---

### Post by nick159 on 2014-11-28
[COLOR=#333333][FONT=UbuntuRegular]When I bootup either on liveUSB boot or even after i installed the screen will mess up.
[http://i.imgur.com/1yB14iz.png](http://i.imgur.com/1yB14iz.png)[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]The graphics card is Nvidia if that matters. I have tried different versions and different distros. Windows XP works fine. Everything works until it gets to the desktop I can see it for like 5 seconds then it messes up and looks like that.  When I use Lubuntu the screen will so like that when I try to open minecraft. [/FONT][/COLOR]

---

### Post by oldfred on 2014-11-28
What nVidia card?
I had 9600GT and had to use nomodeset on live installer and first boot or until I installed nVidia driver from repository. 
My new system also a low power somewhat newer nVidia  620GT actually works with the open source driver, with some minor issues.

 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by nick159 on 2014-11-30
I installed Lubuntu, and the problem kept occurring when I tried to run minecraft for my brother. I installed another driver and the problem has not occurred again. Thank you for the help though!

---

