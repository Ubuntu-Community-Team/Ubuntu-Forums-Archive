---
title: "canon pixma ip1600"
date: 2007-08-14
forum: General Help
---

### Post by ravendiana on 2007-08-14
hello all

I know this has been brought up before, but I'm running dapper and can't get my printer to install I've tried the directions here [http://arzanulhaq.blogspot.com/2007/06/how-to-setup-canon-pixma-ip1600-and.html](http://arzanulhaq.blogspot.com/2007/06/how-to-setup-canon-pixma-ip1600-and.html) and get a dependancy error on the second flie becuse the first file is the wrong verson.  
I tried to install the ip2200  driver direct from cannon and isntal it's rpm drivers using alien, but it can't find the files that are sitting right there in the home folder.  I'm lost.  help?

Diana

---

### Post by Seisen on 2007-08-14
You have to be running Edgy because of the version of the lib file you need, their is no way around it. If you upgrade to Edgy it will work perfectly. If you need help on how to upgrade I would be glad to help you.

---

### Post by leicester on 2007-08-14
Please Help Me Install Canon Pixma Ip1600 On 64 Bit Feisty. I Researched In The Forums But Nothing Works. The Instructions Are For 32bit Systems And I Always Get An Error Message In The Terminal. The Error Says That The Architecture Is Not Supported.. Any Help? It Would Be Greatly Appreciated

---

### Post by Seisen on 2007-08-14
You can try putting this in front of the package when you install it and see if it works. But doing this can break your system so be forewarned.

```
--force-architecture
``` so it would look like this

```
sudo dpkg -i --force-architecture libcnbj-2.6_0-1_i386.deb 
```

---

### Post by leicester on 2007-08-14
I was able to install it but after configuring cups the test page wasn't successful. Thanks for the tip, though

---

### Post by ravendiana on 2007-08-14
isn't edgy kubuntu?  I don't want to move to kubuntu, I've finally gotten my video card, mp3s and extranal hard drive working in dapper and I don't know what it will do to them and other things to move to anouther OS.  It's really not very heartening to see how many things are broken in this or that verson around here witht he fix being get a diff version, and then I see the new version breaks something else....

---

### Post by Seisen on 2007-08-14
Edgy is the next version up from dapper.

---

### Post by gobbles414 on 2007-08-14
leicester,

[Here]("http://openprinting.org/show_printer.cgi?recnum=Canon-PIXMA_iP1600") is a link to your printer on the OpenPrinting database. According to this, you might be able to get the printer working by installing it as an ip2200. I know that it didn't work for ravendiana. But he/she isn't running Feisty. I haven't read all of the links on the OpenPrinting profile, but...

I did something similar while installing a Canon MP530 on 32-bit Feisty. After trying "official" drivers without success, I went System --> Administration --> Printing --> New Printer, and added my printer as an MP830. This was instead of adding the printer as an MP500 as logic would have suggested. The MP500 driver did not print at satisfactory quality. Note that the hundreds place is different but the tens place is the same in the successful driver. That is, both the MP530 and the MP830 have 30 at the end.

EDIT: If ip2200 isn't available in the New Printer wizard, you might try others in the same class (e.g. ipxxxx).

---

### Post by crhumber on 2007-08-15
I agree.  You should be able to get it working using a different canon driver.  I have a Canon ip90 working on 64 bit ubuntu using the i560 driver.  Hope it works for you

---

