---
title: "Non persistent USB Ubuntu; deleted everything else; how to make permanent without usb"
date: 2020-01-07
forum: General Help
---

### Post by oliversmithcomp on 2020-01-07
I downloaded Ubuntu 18.04, and installed it. Turns out that doesn't make it persistent. I have a USB drive which can't handle another OS on it, so I need to figure out how to make Ubuntu persistent, WITHOUT keeping the USB in all the time. Sorry for the newbie question. 
If you have time, please walk me through installing ettercap (I managed on Windows, but this is another animal).
Thank you.

---

### Post by CelticWarrior on 2020-01-07
Burning an ISO to a USB stick is not "installing". You can surely create a Ubuntu USB stick with persistence but that or a proper installation in flash memory is always a very bad idea because it wears out the drive in months.

And if you're a newbie you shouldn't be messing with ettercap either, sorry to say. If you want to play 'hacker' just don't. If you want to seriously learn about pentesting not for criminal activities there are courses for that and in those they teach you what tools and how to use them. Some - but definitely not all - will recommend the ready made KaliOS. Unlike what many people think, unfortunately, professionals don't use it. 

But regardless of what you end up using, and considering this question alone, you still have a long way to go, lots of Linux basics to learn, before you can do the "cool stuff".

---

### Post by oliversmithcomp on 2020-01-07
I'm sorry, I understand my eagerness to learn ettercap is disrespectful and unnecessary. I am a teenager and want to learn pentesting/legitimate hacking methodology for my university application (I repeat I have no intention of becoming a black-hat or illegal hacker). I have a problem of always rushing into things, and I suppose this is the same. I used the installation 'wizard' to install Ubuntu, which subsequently told me files will not be saved on reboot. I no longer have windows (accidentally deleted a LOT of stuff messing with partitions (I know it's stupid)) and enjoy what I see of Linux's UI. I would be very grateful if you could explain: how I can install a persistent version of Linux independent of a USB drive - or - how I can install windows again given only a usb stick and my current OS (Linux Ubuntu). 
Sorry for disrespecting the power/complexity of this software, and thank you for your time.
P.S Any recommendations for a free penetration testing course? I am (evidently) a newbie.

---

### Post by dragonfly41 on 2020-01-07
I don't know about "ettercap" but it is true that the normal method of creating a LiveUSB leaves it non persistent.  I usually just run through a few installations of needed packages on booting the LiveUSB. Of course such installations are lost every time you boot up LiveUSB but I keep a permanent partition where I keep notes such as installation commands. boot-repair is one such extra package installation.

If you *do *want to create a persistent LiveUSB then [here is one tutorial]("https://www.howtogeek.com/howto/14912/create-a-persistent-bootable-ubuntu-usb-flash-drive/"). Your might do this from an existing LiveUSB session using a second flash drive for the purpose. You would then have *two* LiveUSB's - one persistent (which you have) and the second. You might need to install mkusb on the first LiveUSB to create the second. I have not used LiveUSB to create a second.

Adding a note on Windows. After you install Ubuntu onto a permanent drive you can optionally install VirtualBox and install VM Windows. But this is not on the bare machine and for your purposes of learning forensic methods you will need to install Windows afresh (if you have the licence). When searching around add the keyword "forensics" to take you to professional tools. in fact search this forum for "forensic data recovery". Study specialist sites such as [here]("https://www.grc.com/x/ne.dll?bh0bkyd2").

---

### Post by oliversmithcomp on 2020-01-07
Thanks for your help.

---

### Post by ajgreeny on 2020-01-07
We do not allow discussion of any pentesting or hacking in this forum, whether it is to be used legally or illegally.

See section 17 of the forum rules a code of conduct at [https://ubuntuforums.org/misc.php?do=showrules](https://ubuntuforums.org/misc.php?do=showrules)
> 17: Cracking: Requests for help about any form of password or encryption "cracking" are not supported. Even though there are packages such as aircrack in the repositories, discussions about cracking or software related to cracking often lead to discussions about illegal activities. Such threads will be closed.

CLOSED

---

