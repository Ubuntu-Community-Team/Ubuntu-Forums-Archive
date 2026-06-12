---
title: "C Drive Icon"
date: 2008-03-28
forum: General Help
---

### Post by manga on 2008-03-28
I just install ubuntu 7.10 in my comp with XP (Dual Boot).During installation...i did opt out of migration assistance.After installation....i can see my c: drive icon in my desktop in ubuntu. I can click on the icon and look at all my window files and folder. Is this normal or did i miss anything and is this safe.Thanks!:confused:

---

### Post by manga on 2008-03-28
I just install ubuntu 7.10 in my comp with XP (Dual Boot).During installation...i did opt out of migration assistance.After installation....i can see my c: drive icon in my desktop in ubuntu. I can click on the icon and look at all my window files and folder. Is this normal or did i miss anything and is this safe.Thanks!:confused:

---

### Post by danwood76 on 2008-03-28
Yes this is normal and safe.
The ntfs-3g driver allows reading and writing of windows partitions and ubutnu automatically detects ntfs drives during installation and auto mounts them for you.

regards,
Danny

---

### Post by manga on 2008-03-28
> **danwood76 said:**
> Yes this is normal and safe.
The ntfs-3g driver allows reading and writing of windows partitions and ubutnu automatically detects ntfs drives during installation and auto mounts them for you.

regards,
Danny

thanks!:)....and 1 more question

i manage to connect to internet by using a config  wvdial from other forumner.I just want to know whether the config phone number is safe coz my actual phone number is different (Singapore).Thanks

the Config wvdial is here:
------------------------------
Phone = *99**1#
Username = 123
Password = 123
Stupid Mode = 1
Dial Command = ATDT
Modem = /dev/ttyUSB0
Baud = 115200
Init2 = ATZ
Init3 = ATQ0V1E1S0=0&C1&D2+FCLASS=0
ISDN = 0
Modem Type = Analog Modem

---

### Post by danwood76 on 2008-03-28
How are you connecting through a dial up modem?
If it works I wouldnt be too worried as long as its connecting to your ISP.

---

### Post by manga on 2008-03-28
> **danwood76 said:**
> How are you connecting through a dial up modem?
If it works I wouldnt be too worried as long as its connecting to your ISP.

I`m using a HSDPA Huawei USB Modem E220.By the way...how do i check whether my ISP is the same using window XP and Ubuntu.Sorry for being a newbie.Thanks again:)

---

### Post by jeeves on 2008-03-28
During the past year Ubuntu added automatic read and write support for the NTFS file system. So it's perfectly normal to be able to see you windows XP  files on a dual boot system.

> **manga said:**
>  is this safe
I don;t claim to be an expert, but the the NTFS driver for linux has been pretty throughly tested. It has been under development for many years. It there were still  problems with it you would probably be reading  horror stories about it in this forum.

---

### Post by danwood76 on 2008-03-28
This thread is a duplicate of:
[http://ubuntuforums.org/showthread.php?t=737912](http://ubuntuforums.org/showthread.php?t=737912)

---

### Post by danwood76 on 2008-03-28
I just had a look at what modem you have and it will be fine.
Im assuming your internet service provider is a mobile phone network and that you have a sim inside the modem?

If you do then this will be fine Im sure.

---

### Post by manga on 2008-03-28
> **jeeves said:**
> During the past year Ubuntu added automatic read and write support for the NTFS file system. So it's perfectly normal to be able to see you windows XP  files on a dual boot system.


I don;t claim to be an expert, but the the NTFS driver for linux has been pretty throughly tested. It has been under development for many years. It there were still  problems with it you would probably be reading  horror stories about it in this forum.

Firstly i`m new to ubuntu and unlike window Xp.....i have my firewall and anti-virus.Secondly...if there is any hacker virus in ubuntu , it will definitely penetrate into my c:drive due to the so called ntfs-3g driver.

---

### Post by manga on 2008-03-28
> **danwood76 said:**
> I just had a look at what modem you have and it will be fine.
Im assuming your internet service provider is a mobile phone network and that you have a sim inside the modem?

If you do then this will be fine Im sure.

yup......correct.

---

