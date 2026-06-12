---
title: "ubuntu with FSC Amilo A 1650G !"
date: 2006-08-30
forum: General Help
---

### Post by cpu4 on 2006-08-30
hii 
I want to install ubuntu in FSC Amilo 1650G.. 
the problem that I face and faced at past, wireless!!!!  
Never get wireless work on it.. 
dont forget that I have an access code for my wifi network.. 
any idea to configure and to get wireless works on it........
..........!!:confused: :confused:

---

### Post by cpu4 on 2006-08-31
????????????????????????????????????

---

### Post by The Keeper on 2006-08-31
See the links below.
[http://www.ubuntuforums.org/showthread.php?t=229427](http://www.ubuntuforums.org/showthread.php?t=229427)
[http://users.tkk.fi/~uniemimu/amilo/](http://users.tkk.fi/~uniemimu/amilo/)

---

### Post by cpu4 on 2006-08-31
thanks alot .. :) is this solution worked with you??

---

### Post by freak101 on 2006-09-07
My laptop is an amilo A1650, the wireless card is working fine with bcm43xx module. 
The steps I followed to install the broadcom card: 
- install acer_acpi to activate the card (wireless led light on :cool: )
- generate bcm43xx firmware using bcm43xx-fwcutter from the windows driver.
- load the module bcm43xx
Final touch is wpa_supplicant, useful if you need to connect to wpa protected networks.

I can write a more detailed description if it can help.

Antonio

acer_acpi => [http://code.google.com/p/aceracpi/](http://code.google.com/p/aceracpi/)
broadcom windows driver => [ftp://ftp.support.acer-euro.com/notebook/ferrari_4000/driver/winxp64bit/80211g.zip](ftp://ftp.support.acer-euro.com/notebook/ferrari_4000/driver/winxp64bit/80211g.zip)
bcm43xx-fwcutter is included in the repository.

---

### Post by Y-S on 2007-02-22
> **freak101 said:**
> My laptop is an amilo A1650, the wireless card is working fine with bcm43xx module. 
The steps I followed to install the broadcom card: 
- install acer_acpi to activate the card (wireless led light on :cool: )
- generate bcm43xx firmware using bcm43xx-fwcutter from the windows driver.
- load the module bcm43xx
Final touch is wpa_supplicant, useful if you need to connect to wpa protected networks.

I can write a more detailed description if it can help.

Antonio

acer_acpi => [http://archernar.co.uk/acer_acpi/acer_acpi_main.html](http://archernar.co.uk/acer_acpi/acer_acpi_main.html)
broadcom windows driver => [ftp://ftp.support.acer-euro.com/notebook/ferrari_4000/driver/winxp64bit/80211g.zip](ftp://ftp.support.acer-euro.com/notebook/ferrari_4000/driver/winxp64bit/80211g.zip)
bcm43xx-fwcutter is included in the repository.

I love you guy, this is a solution that works for my Amilo A1650, after having tried many how-to. :guitar:

---

### Post by Chez Geek on 2007-06-16
> **freak101 said:**
> My laptop is an amilo A1650, the wireless card is working fine with bcm43xx module. 
The steps I followed to install the broadcom card: 
- install acer_acpi to activate the card (wireless led light on :cool: )
- generate bcm43xx firmware using bcm43xx-fwcutter from the windows driver.
- load the module bcm43xx
Final touch is wpa_supplicant, useful if you need to connect to wpa protected networks.

I can write a more detailed description if it can help.

Antonio

acer_acpi => [http://code.google.com/p/aceracpi/](http://code.google.com/p/aceracpi/)
broadcom windows driver => [ftp://ftp.support.acer-euro.com/notebook/ferrari_4000/driver/winxp64bit/80211g.zip](ftp://ftp.support.acer-euro.com/notebook/ferrari_4000/driver/winxp64bit/80211g.zip)
bcm43xx-fwcutter is included in the repository.
Hi Antonio,

I'm a complete newbie and I'd love to get started on Ubuntu. Unfortunately the fact that I can't get my wireless to work actually stops me from learning. I'd really appreciate a detailed, idiot-proof and step-by-step explanation.

You mentioned that you could write a more detailed description and I'd really appreciate if I could take you up on that offer.

Thanks a lot for your help!

---

### Post by spleethoven on 2007-06-16
I would like that to :)

---

### Post by bren on 2007-06-22
this is what you need guys (a how to) 

NOTE THE POST LATER IN THIS THREAD which says there is a 0.4 version for feisty (this description uses a package 0.3 for edgy).   Otherwise this thread will work for you!

[http://ubuntuforums.org/showthread.php?t=224349&highlight=bren+amilo](http://ubuntuforums.org/showthread.php?t=224349&highlight=bren+amilo)

bren

---

### Post by Chez Geek on 2007-06-24
@Bren

Fantastic - thank you very much! I'm a complete newbie on Ubuntu but I like the idea and love the helpful community.

For anyone else who reads this finding themselves stuck somehow: the following guide also quite good:
[http://ubuntuforums.org/showthread.php?p=1071920&mode=linear]("http://ubuntuforums.org/showthread.php?p=1071920&mode=linear")

CG

---

