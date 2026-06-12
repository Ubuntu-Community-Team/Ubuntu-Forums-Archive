---
title: "Looking for a cheap printer"
date: 2023-10-16
forum: General Help
---

### Post by drichardson2 on 2023-10-16
I don't need a laser printer.  I rarely print, but when I need to then I need to.
Can people here recommend a cheap printer that simply uses black cartridges - I don't need color but if one is real affordable that does color too that's ok too.
I'm thinking something HP or Brother - ?

---

### Post by TheFu on 2023-10-16
Laser printers ARE cheaper than inkjets, unless you plan to buy a new one every year.  Ink is extremely expensive and dries out. Toner can last a decade.  I have a toner cartridge in my laser printer from 2010 that is just starting to become light.  By pulling the cartridge out and shaking it, the toner gets spread out again and it will print 20 more pages (if not more).  Bought the laser printer in 2007 for about $80. It came with a "starter" 2000 page cartridge.  That lasted until 2010. Bought (2) 10,000 page cartridges for $60 total.  I have the 2nd one still sealed in a box here.  Since 2012, I print maybe 50 pgs a year, if that.  Taxes and other govt paper forms.

In the 2000-2007, I had a few b/w inkjets.  Ink dried out at least once a year and the replacements were $35-$50.  8 x 35 = $280!  That isn't cheaper.

Laser printers ARE cheaper.

HP has become nasty with their printer business. I'd say avoid them since they want all printers to "phone home".  I have a Brother All-in-One (fax/scanner/inkjet).  Since the ink dried out, I've never replaced it or used it for printing.  It is a fax/scanner to me.  It is always a hassle to get it working on new Linux systems because it isn't **driverless**.

Whatever printer you get, make certain it is **driverless** for any functions you need.  [https://openprinting.github.io/driverless/](https://openprinting.github.io/driverless/)   That means absolutely ZERO software should need to be installed on your linux system. ZERO. NADA.  If any software is included in the Quick-Start, don't buy that printer.

If I were in the market for a new printer, I'd have recommendations.  My Samsung ML1450 laserjet isn't manufactured anymore, but it is automatically setup for all my Linux systems since 16.04.  For 22.04, I just had to confirm it the first time I went to print. It was pre-setup.  It isn't "driverless" due to being so very old, but I've always used it with the IPP standard protocol. It is USB connected to a Linux print server. I retired the 2010 system a few months ago and moved the print server to a new 20.04 install so all the other computers can use it. 

I'm not a fan of networked printers. Too easy for the printer hardware vendor to abuse that networking for their own desires. Many will refuse to print if they can't phone home.

---

### Post by drichardson2 on 2023-10-16
ok then,
Please recommend a driverless laser printer - I only need black.  The Samsung you mentioned isn't made anymore.  I actually bought an HP black laser printer and couldn't get it to work at all - even after installing hplip.....

---

### Post by TheFu on 2023-10-16
> **TheFu said:**
>  If I were in the market for a new printer, I'd have recommendations.  

I'm not in the market.  I'd check the driverless printer list at the link above ... and my short list would be a Brother Laser printer without any networking, but still driverless.  Around the world, different printers are available, so where you are in the world will matter.

Plus, before buying, I'd check my Ubuntu install **system-config-printer** tool for the make+model already being known to it.  IPP:// URLs that support PDF and/or PS files directly would be the most compatible.  

**Nothing below will directly help you, but ... perhaps seeing the information will clarify things.**

The URI for that my printer is usb://Samsung/ML-1740?serial=2W61BKCXBxxxxxxx   Again, because it is old, is has a well-known driver, 
**printer-driver-splix** is the debian package name and Ubuntu 20.04 with system-config-printer and avahi running pre-handled the setup. I just marked it as the "default" printer and created an alias "Laser" for it.  I often print from the command line using lpr and having a shorter name for the printer to target is easier.  The other name is "Samsung-ML-1740" - who wants to type all that in? Not me. Heck, I think I got the model number wrong in this thread today already. Yep, I called it a "Samsung ML1450" which was wrong.  It is a 1740, not that it matters, but "laser" is easy to remember.

```
$ dpkg -l |grep -i samsung
ii  printer-driver-splix        2.0.0+svn315-7fakesync1ubuntu0.1   amd64  Driver for Samsung and Xerox SPL2 and SPLc laser printers

```

There are all-in-one driverless devices too. If you need a scanner/fax/printer, they make laser versions of those now and the scanner can scan directly to USB flash storage or an SDHC card these days, no computer needed at all.  My next all-in-one will work without a computer connected. Of that, I'm certain.  Why fax?  I like to keep my govt at arms length and fax is the easy way to accomplish that.  My govt can't be trusted with email addresses due to open-records laws.  YMMV.  Last thing I need is another way for the govt (or people who buy govt data) to spam me.

---

### Post by dragonfly41 on 2023-10-16
I would hunt locally for office clearance sales including used printers.
I agree with @TheFu on the robustness of laser printers.
And cost drain of inkjet printers.
I have been using an HP LaserJet 2100 M since last century.
Toner cartridges are robust. The printer is built like a tank and is heavy.
Which is why I suggest hunting around locally. Old equipment sales.

---

### Post by drichardson2 on 2023-10-21
Thanks everyone for your suggestions.  Like I said previously, I actually bought a black HP Laser jet printer and couldn't get it to work at all - even after installing hplip.

What do folks think about this refurbished one ?

[https://www.ebay.com/itm/355065741097?hash=item52ab913f29&amdata=enc%3AAQAIAAAA8HNpcmX3PXjM0EEtW4WgylfB4U3Y939W2E6%252Fv4RzfUQZ2z8TFQnMwxcuK8vHV0VkV68xNjI8kJswhsy8uj50kwMhqbGKdW1oTg9W8o%252F0Tew1W5npc5aYfq4JaqYiWbjzo%252BWPq6nun7zMEU1ekH1DeGVKFy7et8Ue4TcMYc%252BgdpNBHLKFsSeVYAZpsM5a9LRcKvlQuQ3eRO83hjt1l6AjeDATprEcSqAAik35fjw8y7YSP3Mx81%252Bbk%252B9GjQLPO50%252BpyPybBcrlheWpbHuDWN%252Fto9m3fsc3L1qz6MyBNIg5ST1MU8ZLvA7MttB7LlyDeOs7g%253D%253D%7Campid%3APL_CLK](https://www.ebay.com/itm/355065741097?hash=item52ab913f29&amdata=enc%3AAQAIAAAA8HNpcmX3PXjM0EEtW4WgylfB4U3Y939W2E6%252Fv4RzfUQZ2z8TFQnMwxcuK8vHV0VkV68xNjI8kJswhsy8uj50kwMhqbGKdW1oTg9W8o%252F0Tew1W5npc5aYfq4JaqYiWbjzo%252BWPq6nun7zMEU1ekH1DeGVKFy7et8Ue4TcMYc%252BgdpNBHLKFsSeVYAZpsM5a9LRcKvlQuQ3eRO83hjt1l6AjeDATprEcSqAAik35fjw8y7YSP3Mx81%252Bbk%252B9GjQLPO50%252BpyPybBcrlheWpbHuDWN%252Fto9m3fsc3L1qz6MyBNIg5ST1MU8ZLvA7MttB7LlyDeOs7g%253D%253D%7Campid%3APL_CLK)

And this is the same printer and may be new (?)

[URL="https://www.amazon.com/HP-LaserJet-M234dwe-Wireless-6GW99E/dp/B08SHVNH7P"]https://www.amazon.com/HP-LaserJet-M234dwe-Wireless-6GW99E/dp/B08SHVNH7P

or this one:
[/URL][U][URL="https://www.amazon.com/HP-Laserjet-M110we-Wireless-Monochrome/dp/B09J79Y6Z5/ref=sr_1_2?crid=EYZV7IAVVM6&keywords=hp%2Bblack%2Blaser%2Bprinter&qid=1697883236&s=electronics&sprefix=hp%2Bblack%2Blaser%2Bprinter%2Celectronics%2C146&sr=1-2&th=1"]https://www.amazon.com/HP-Laserjet-M110we-Wireless-Monochrome/dp/B09J79Y6Z5/ref=sr_1_2?crid=EYZV7IAVVM6&keywords=hp%2Bblack%2Blaser%2Bprinter&qid=1697883236&s=electronics&sprefix=hp%2Bblack%2Blaser%2Bprinter%2Celectronics%2C146&sr=1-2&th=1

[/URL][/U]I definitely would like something that connects via USB (even if it also has wireless)  Then there is this Brother below:[URL="https://www.amazon.com/HP-Laserjet-M110we-Wireless-Monochrome/dp/B09J79Y6Z5/ref=sr_1_2?crid=EYZV7IAVVM6&keywords=hp%2Bblack%2Blaser%2Bprinter&qid=1697883236&s=electronics&sprefix=hp%2Bblack%2Blaser%2Bprinter%2Celectronics%2C146&sr=1-2&th=1"]

[/URL][https://www.amazon.com/Brother-RHL-L2300D-Monochrome-Printer-Printing/dp/B083MYW72S/ref=sr_1_1?crid=1CFQU9UGER28Z&keywords=brother%2Bblack%2Blaser%2Bprinter&qid=1697883734&s=electronics&sprefix=brother%2Bblack%2Blaser%2Bprinte%2Celectronics%2C156&sr=1-1&th=1](https://www.amazon.com/Brother-RHL-L2300D-Monochrome-Printer-Printing/dp/B083MYW72S/ref=sr_1_1?crid=1CFQU9UGER28Z&keywords=brother%2Bblack%2Blaser%2Bprinter&qid=1697883734&s=electronics&sprefix=brother%2Bblack%2Blaser%2Bprinte%2Celectronics%2C156&sr=1-1&th=1)



Addendum:  Are any of the printers above "driverless?"

---

### Post by drichardson2 on 2023-10-21
Follow up question:  I know HP printers, one often has to do the hplip thing.  Do Brother printers need something similar or do they just work.

---

### Post by dragonfly41 on 2023-10-21
Do you have the HPlip Tool Box installed? "Show Applications" and search HP.

---

### Post by MAFoElffen on 2023-10-21
Dang you TheFu!!! LOL

You started talking about the "old printers" you have, and my head went back to the chain and band printers we used to have that printed out 2000 lines per minute... That seemed fast back then. But were, what, about $20K-$30K each?

---

### Post by jimmyrus on 2023-10-23
> **drichardson2 said:**
> I don't need a laser printer.  I rarely print, but when I need to then I need to.
Can people here recommend a cheap printer that simply uses black cartridges - I don't need color but if one is real affordable that does color too that's ok too.
I'm thinking something HP or Brother - ?

May want to check these threads under your other ids. Been asking about hp lexmark and brother for a long time now.
[https://ubuntuforums.org/showthread.php?t=2474803](https://ubuntuforums.org/showthread.php?t=2474803)
[https://ubuntuforums.org/showthread.php?t=2481986](https://ubuntuforums.org/showthread.php?t=2481986)
[https://ubuntuforums.org/showthread.php?t=2254998](https://ubuntuforums.org/showthread.php?t=2254998)
[https://ubuntuforums.org/showthread.php?t=2270041](https://ubuntuforums.org/showthread.php?t=2270041)

---

