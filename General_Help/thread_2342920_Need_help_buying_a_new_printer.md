---
title: "Need help buying a new printer"
date: 2016-11-11
forum: General Help
---

### Post by ardouronerous on 2016-11-11
My HP Deskjet 3744 just broke, I've used this printer since Windows XP and Xubuntu 12.04 LTS and it has worked out of the box, and I'm looking for a new printer, however, I'm not sure if the printer I will choose will work on Xubuntu 16.04 LTS.

Here's the printer I've found so far: HP DeskJet Ink Advantage 1115 Printer

And here's the info I found: [http://hplipopensource.com/hplip-web/models/deskjet/deskjet_1110_series.html](http://hplipopensource.com/hplip-web/models/deskjet/deskjet_1110_series.html)

I can't really make heads or tails of the information.

My questions are, will this printer work out of the box like my previous printer? Do I need to install something to make the printer work?

---

### Post by ardouronerous on 2016-11-11
And here another printer that seems affordable. Again, I'm not sure if this printer will work on Xubuntu 16.04.

*Canon Pixma IP2870*

---

### Post by oldfred on 2016-11-11
I have two low cost (read expensive ink) HP printers and they work well.

When they were new, the version of HPLIP in Ubuntu's repository was many versions older. 
So I downloaded newest hplip directly from HP and it runs its own script to install
Have gotten errors on missing tray, but there is a setting to solve that.
And often printer while physically on, it is off. I have to go into HP Device manager settings & turn it on.

---

### Post by ardouronerous on 2016-11-11
If I'm not sure if the printer will work on Xubuntu 16.04, and the installation CD says it will work on Windows XP, could I install the printer on XP via Virtualbox and print from there?

---

### Post by oldfred on 2016-11-11
No need, it should just work.
But the install CD would be just for Windows.
You have to install drivers from Ubuntu's repository. 
Or if not new enough then the version of hplip directly from HP.

---

### Post by ardouronerous on 2016-11-11
But what about Canon Pixma IP2870? How would I know if this printer would work on Xubuntu 16.04?

---

### Post by SeijiSensei on 2016-11-11
> **ardouronerous said:**
> But what about Canon Pixma IP2870? How would I know if this printer would work on Xubuntu 16.04?

Check this invaluable resource: [http://www.openprinting.org/printers](http://www.openprinting.org/printers)

I stopped buying inkjet printers because the cost of the ink is quite high.  Also as someone who prints only occasionally, my HP Photosmart would fail to work because the printer cartridges had "expired."  Yeah sure.

Now I have an LED ("laser-class") [HL-3170CDW]("https://www.amazon.com/Brother-HL-3170CDW-Networking-Certified-Replenishment/dp/B00BQU141C") from Brother. It's connected to my network router via Ethernet so all my devices, both printers and smartphones, can print to it.  I don't think I've had to replace a cartridge yet.

---

### Post by colin.p on 2016-11-11
I found that (as far as my own experience) HP printers were the easiest to set up, as the drivers worked just fine with the least amount of screwing around. It was even easy to set up in Android. However, the $300 HP inkjet printer that I bought only lasted until the extended warranty ran out and don't ask me about the price of the flippin' cartridges. So I bought a Canon MF4700 laser printer and that is by far the worst POS printer I have ever had the misfortune to own. The driver support (even though Canon has made some driver advances) is weak at best, though hardware wise, not too bad. If I were you, save the pain and heartache and stick with HP and be very cautious about Canon printers unless Canon has made one to actually work with linux.

---

### Post by wildmanne39 on 2016-11-12
My brother laser printer works with ubuntu but it was a little harder to setup then the hp I use to use. Hp is very compatible with ubuntu.

---

### Post by Bucky Ball on 2016-11-12
> **Wild Man said:**
> My brother laser printer works with ubuntu but it was a little harder to setup then the hp I use to use. Hp is very compatible with ubuntu.

Exactly my experience for the first bit and definitely to the second bit.

---

### Post by SeijiSensei on 2016-11-12
One easy way to set up a Brother printer is to use the "printer install tool" that you can download from the support site for your printer.  It runs from the command prompt, identifies the required drivers, then downloads and installs them.  That said, I usually set up printers using the CUPS utility at [http://localhost:631/](http://localhost:631/).  In the case of my network-attached Brother, it was automatically detected by this method.

---

### Post by MechaMechanism on 2016-11-12
I have a Networked Postscript Okidata Laser printer.  The printer is on an Ethernet network and has 244 MB of memory.  It has a Postscript module installed.

So what I recommend is a color laser printer that has built in postscript.  100% of all postscript printers are compatible with all Linux distributions that use cups.  With a postscript printer there is no need for third party software, it just works.  It's true, you do pay more for postscript, but as someone who has a postscript printer I can vouch for laser printers that have postscript.  Plus they last for several years.  Mine is ten years old and I still can find parts for it from Okidata.  Get at least 256 MB of ram in the printer.

Both these printers have native Postscript.
I recommend this one; [http://store.hp.com/us/en/pdp/printers/hp-color-laserjet-pro-mfp-m477fdn-cf378a-bgj](http://store.hp.com/us/en/pdp/printers/hp-color-laserjet-pro-mfp-m477fdn-cf378a-bgj)

Or for a little more goodies, this one; [http://store.hp.com/us/en/pdp/printers/hp-color-laserjet-pro-mfp-m477fdw-cf379a-bgj](http://store.hp.com/us/en/pdp/printers/hp-color-laserjet-pro-mfp-m477fdw-cf379a-bgj)

---

### Post by SeijiSensei on 2016-11-12
Brother lasers support HP-PCL, and Brother's own version of Postscript, BR-Script.  I turned on Postscript emulation in my printer because that's the only language that works correctly for [envelope printing on Linux]("http://www.linuxquestions.org/questions/linux-software-2/libreoffice-3-5-7-2-in-fedora-17-writer-envelopes-brother-hl2240-printer-4175455725/#post4931376").

---

### Post by kurt18947 on 2016-11-12
> **SeijiSensei said:**
> One easy way to set up a Brother printer is to use the "printer install tool" that you can download from the support site for your printer.  It runs from the command prompt, identifies the required drivers, then downloads and installs them.  That said, I usually set up printers using the CUPS utility at [http://localhost:631/](http://localhost:631/).  In the case of my network-attached Brother, it was automatically detected by this method.

My experience parallels Seiji Sensei re Brother printers. One thing I've done with Brother inkjets is to get refillable cartridges. That has helped a LOT with ink costs. Brother's linux web site information is quite dated but the installer script has worked very well for me. Samsung's MFD laser has worked very well and the drivers are included, or you can download linux drivers from Samsung's support web site. Samsung also makes a color laser that can be found for an attractive price if you're patient. That printer is rated around 19 pages/min. B&W but only 4 pages/min. color. 

As has been pointed out, inkjet nozzles can dry out and clog if the printer isn't used weekly. Laser toner doesn't dry out so it can sit for weeks and still work as expected. HP and some Canons use cartridges with the nozzles built in. Brother's print head is separate from the cartridges so if the head gets plugged and can't be cleared by cleaning, it's probably cheaper to replace the printer than replace a clogged print head.

---

### Post by oldrocker99 on 2016-11-12
> **SeijiSensei said:**
> Check this invaluable resource: [http://www.openprinting.org/printers](http://www.openprinting.org/printers)

I stopped buying inkjet printers because the cost of the ink is quite high.  Also as someone who prints only occasionally, my HP Photosmart would fail to work because the printer cartridges had "expired."  Yeah sure.

Now I have an LED ("laser-class") [HL-3170CDW]("https://www.amazon.com/Brother-HL-3170CDW-Networking-Certified-Replenishment/dp/B00BQU141C") from Brother. It's connected to my network router via Ethernet so all my devices, both printers and smartphones, can print to it.  I don't think I've had to replace a cartridge yet.

That's my printer as well. No problem at all setting it up wirelessly, although I did have to enter the printer's IP address in the print dialog in the Device URI section. It works like a charm; I had to replace cartridges, but I do print a lot.

---

### Post by Hewjr100 on 2016-11-12
hi, I use hp exclusively, the 8600 and 8700 series works fine.

Henry

---

### Post by ardouronerous on 2016-11-14
Thanks for the replies guys, at the moment, HP isn't an option for me and my family, my dad's kinda interested in Canon PIXMA iP2870 because of the price, his looking for a low-cost printer and it seems that the Canon printer meets his budget.

With that said, I've done some digging around, and Canon does have some Linux drivers available for download;

*iP2800 series IJ Printer Driver Ver. 4.10 for Linux (rpm Packagearchive)*
[URL="http://support-ph.canon-asia.com/contents/PH/EN/0100586402.html"]http://support-ph.canon-asia.com/contents/PH/EN/0100586402.html
[/URL]
[I]iP2800 series IJ Printer Driver Ver. 4.10 for Linux (debian Packagearchive)
[/I][http://support-ph.canon-asia.com/contents/PH/EN/0100586502.html](http://support-ph.canon-asia.com/contents/PH/EN/0100586502.html)

Does these work and how do I install them?

If all else fails, can I install the XP driver for the printer into Virtualbox running XP and use the printer from there?

---

### Post by Bucky Ball on 2016-11-14
> **ardouronerous said:**
> If all else fails, can I install the XP driver for the printer into Virtualbox running XP and use the printer from there?

Yuck. A messy workaround.

To install the .deb file for that printer you download it and double-click it. That's it.

iP2800 series IJ Printer Driver Ver. 4.10 for Linux (debian Packagearchive)
[http://support-ph.canon-asia.com/con...100586502.html](http://support-ph.canon-asia.com/con...100586502.html)

Have no idea about the ink setup on the Canon and don't remember your exact requirements for what you want the printer to do, but ink consumption and replacement is a definite.

I know that, for some unsaid reason, HP is out of the question. I have monochrome duplex Brother HL-2270DW wireless printer that costs us virtually nothing to run re. ink. If you are buying something that consumes a lot of expensive ink that can't be easily and cheaply refilled DIY then expect to pay for that printer again and again via ink supplies.

Just a thought. :)

---

### Post by ardouronerous on 2016-11-14
> **Bucky Ball said:**
> Yuck. A messy workaround.

To install the .deb file for that printer you download it and double-click it. That's it.

iP2800 series IJ Printer Driver Ver. 4.10 for Linux (debian Packagearchive)
[http://support-ph.canon-asia.com/con...100586502.html](http://support-ph.canon-asia.com/con...100586502.html)

Have no idea about the ink setup on the Canon and don't remember your exact requirements for what you want the printer to do, but ink consumption and replacement is a definite.

I know that, for some unsaid reason, HP is out of the question. I have monochrome duplex Brother HL-2270DW wireless printer that costs us virtually nothing to run re. ink. If you are buying something that consumes a lot of expensive ink that can't be easily and cheaply refilled DIY then expect to pay for that printer again and again via ink supplies.

Just a thought. :)

Why is the Virtualbox route messy?

For most of my computing life, I've had three printers, a Dot-matrix  printer and two HP Inkjet printers, I've mainly lived on ink refills for  most of my computing life and seldom had to replace an ink  cartridge, only when they break.

Here's the content of the driver:

> cnijfilter-ip2800series-4.10-1-deb.tar.gz
cnijfilter-ip2800series-4.10-1-deb
* packages
               - cnijfilter-common_4.10-1_amd64.deb
               - cnijfilter-common_4.10-1_i386.deb
               - cnijfilter-ip2800series_4.10-1_amd64.deb
               - cnijfilter-ip2800series_4.10-1_i386.deb
* resources
               - printer_fr_utf8.lc
               - printer_ja_utf8.lc
               - printer_zh_utf8.lc
install.sh

---

### Post by wildmanne39 on 2016-11-14
A Long time ago the only way I could print from ubuntu was through virtualbox while it worked I have to say it was not idea and was a bigger pain then you think because for one I did not use windows much so every time I booted it in vb I had to wait a long time for it to install updates, today with it a lot easier to get printers working in ubuntu it is not worth not using ubuntu to print in my opinion.

---

### Post by ardouronerous on 2016-11-15
> **Wild Man said:**
> A Long time ago the only way I could print from ubuntu was through virtualbox while it worked I have to say it was not idea and was a bigger pain then you think because for one I did not use windows much so every time I booted it in vb I had to wait a long time for it to install updates, today with it a lot easier to get printers working in ubuntu it is not worth not using ubuntu to print in my opinion.

Well, on the updates, since Windows XP doesn't get updates anymore and I disabled Internet via Virtualbox settings for security reasons, so I don't have that problems when I boot up into XP.

At the moment I'm using XP on Virtualbox to make my scanner work on Ubuntu because  there seems to be a bug in sane, my scanner worked on 12.04 and 14.04,  but not on 16.04.

---

### Post by Bucky Ball on 2016-11-15
Thought you were installing Win in virtualbox just to use the printer. That would be a messy workaround just to use a printer. Seems you use XP in VB as a matter of course, though, so ...

---

### Post by ardouronerous on 2016-11-15
> **Bucky Ball said:**
> Thought you were installing Win in virtualbox just to use the printer. That would be a messy workaround just to use a printer. Seems you use XP in VB as a matter of course, though, so ... 

 Yeah pretty much my situation, I also avidly test ReactOS whenever they release a new version, because I'd like to use ReactOS instead of XP if I could, and so far, it's pretty unstable.

And I'm also actively watching Wine as well, if I could use Wine to install the XP drivers for my scanner and printer, that would be a cool workaround, but AFAIK, Wine doesn't work well with Windows device drivers.

---

### Post by Hewjr100 on 2016-11-15
Watch out for the cost of ink.  Printer maybe cheap, but ink can cost alot more.

Henry

---

### Post by Tadaen_Sylvermane on 2016-11-15
Another thing to mention about HP Printers. Make sure you get a model that the HPLIP package supports, else you may need to backport a newer package for it. I had to do that with my HP Envy 5640 on 14.04, had to backport the 15.10 hplip to 14.04. Wasn't hard, just something needed doing.

---

### Post by ardouronerous on 2016-11-21
I've done some digging around and I found this; Gutenprint Printer Drivers and Canon PIXMA iP2870 is listed as supported, although it's experimental.

Here's the links:
Gutenprint Printer Drivers ([http://gimp-print.sourceforge.net/](http://gimp-print.sourceforge.net/))
Gutenprint Supported Printers ([http://gimp-print.sourceforge.net/p_Supported_Printers.php](http://gimp-print.sourceforge.net/p_Supported_Printers.php))

I've done some digging around in my own system and found these installed already;

- libgutenprint2 (5.2.11-1) runtime for the Gutenprint printer driver library
- printer-driver-gutenprint (5.2.11-1) printer drivers for CUPS

Does that mean Canon PIXMA iP2870 should be plug and play if I have these installed already?

---

### Post by ardouronerous on 2016-11-23
Bump

---

### Post by Bucky Ball on 2016-11-23
Unsure why you're going down this path. Canon has a Linux driver for the 2800 series. Think someone mentioned it earlier. 

[http://support-asia.canon-asia.com/contents/ASIA/EN/0100586502.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100586502.html)

That's a link to the Asian driver site. 

The printer may be plug and play, emphasis on 'maybe', with those things you mention installed, but you need the printer's driver for full functionality, or possibly any functionality, I'd think.

Looks to me like you are coming at this through the backdoor. Try the front. If there's a Linux driver from the manufacturer, which there is for Canon, HP and Brother, then install it and see if it works. The driver will drag in what it needs when you install, or should, and you don't need to be digging around finding out what the dependencies are for this device driver or that device, etc. etc. ...

If there's a Linux ***driver*** available for the printer, you're good to go. Ignore whether you've got this or that installed for the moment. It is only important that you have the right driver for the printer installed first. If there's problems after that, then troubleshoot.

You seem to be troubleshooting first before the device driver is installed. :-k :)

---

### Post by kurt18947 on 2016-11-23
Bucky is giving good advice. You could get the printer and plug it in. Open your distro's printer app and click 'add a printer' or whatever. See if your new printer is found. If so, see if a driver is found. If no driver is found, install the Canon driver. Don't make it harder than it needs to be.

---

### Post by ardouronerous on 2016-11-23
Thanks for the advice.
The reason why I'm being so cautious is because I don't want to spend money only to buy a high-tech paperweight, and as I've experienced, OS incompatibility isn't part of the warranty.

---

### Post by Bucky Ball on 2016-11-23
> **ardouronerous said:**
> The reason why I'm being so cautious is because I don't want to spend money only to buy a high-tech paperweight, and as I've experienced, OS incompatibility isn't part of the warranty.

Totally understood. When I'm hunting new hardware, if I can't find anyone having issues with it, which seems to be the case with the Canon PIXMA iP2870, I look for someone who is happily using it already (and sometimes raving about it :)).

Maybe pick a couple of possibles and see if there's anyone out there using them in 16.04 already.

As mentioned, HP and Brother are friendly and easy to install, but not sure you're going to find a printer that's 'plug and play', although there may be some out there.

PS: [This is for another device]("http://askubuntu.com/questions/586002/canon-pixma-ip2820-driver-for-ubuntu"), but same would apply for your device and looks like same website. As the thread ends with a post saying it will be left to help people, I assume it worked for the 2820.

---

### Post by ardouronerous on 2016-11-23
Pixma iP2820 and iP2870 uses the same Linux driver that you linked in your previous post.

I've downloaded the driver and here's the content;

cnijfilter-ip2800series-4.10-1-deb.tar.gz
cnijfilter-ip2800series-4.10-1-deb
- - packages
               - - - cnijfilter-common_4.10-1_amd64.deb
               - - - cnijfilter-common_4.10-1_i386.deb
               - - - cnijfilter-ip2800series_4.10-1_amd64.deb
               - - - cnijfilter-ip2800series_4.10-1_i386.deb
- - resources
               - - - printer_fr_utf8.lc
               - - - printer_ja_utf8.lc
               - - - printer_zh_utf8.lc
- install.sh

Not exactly as straightforward as running a .deb file in GDebi Package Installer, so how do I install the driver?

---

### Post by Bucky Ball on 2016-11-23
You [read the first answer here]("http://askubuntu.com/questions/586002/canon-pixma-ip2820-driver-for-ubuntu") as I linked in my last post. You don't even need to open the folder, just a terminal.

---

### Post by ardouronerous on 2016-11-23
I don't know how to execute the ./install.sh though.

---

