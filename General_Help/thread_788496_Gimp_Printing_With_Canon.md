---
title: "Gimp Printing With Canon"
date: 2008-05-09
forum: General Help
---

### Post by measekite on 2008-05-09
Currently I am using Feisty and have a Canon IP4000.

**#1** I installed the Canon PPD file after selecting Adobe and Postscript Level 2.  I do get pretty good prints but the choices in the print dialog are not up to snuff.

**#2 **I then installed a new printer in Gimp.  I selected Canon and found the IP4000.  I got many more choices except for borderless.  The quality of the print was no where near as good as the printer in **#1** even though they both said 600x600 resolution.

**#3** I then installed a 3rd printer in Gimp using the Turbo Print drivers.  I still did not get a choice for borderless printing so I gave up with that.

For a great OS like Linux and a Good (Great wanabee Photoshop) photo editor like Gimp it has terrible printer support.  Even with the driver that produces good results like the item described in **#1,** the choices are poor and the dialog boxes are a real cluge.

Is there anyway to get good printer support for Gimp?  Do the majority of poster have the same or similar problems with printing.

Until Linux and Gimp get their printing act together it is very difficult to leave Windows behind.

Comments and helo are welcome.

---

### Post by gali98 on 2008-05-09
> **measekite said:**
> Currently I am using Feisty and have a Canon IP4000.

**#1** I installed the Canon PPD file after selecting Adobe and Postscript Level 2.  I do get pretty good prints but the choices in the print dialog are not up to snuff.

**#2 **I then installed a new printer in Gimp.  I selected Canon and found the IP4000.  I got many more choices except for borderless.  The quality of the print was no where near as good as the printer in **#1** even though they both said 600x600 resolution.

**#3** I then installed a 3rd printer in Gimp using the Turbo Print drivers.  I still did not get a choice for borderless printing so I gave up with that.

For a great OS like Linux and a Good (Great wanabee Photoshop) photo editor like Gimp it has terrible printer support.  Even with the driver that produces good results like the item described in **#1,** the choices are poor and the dialog boxes are a real cluge.

Is there anyway to get good printer support for Gimp?  Do the majority of poster have the same or similar problems with printing.

Until Linux and Gimp get their printing act together it is very difficult to leave Windows behind.

Comments and helo are welcome.

From What I've seen, Gimp does not have good printing skills.
You may consider saving your picture as high quality and importing it into a program better suited. Maybe Scribus. I have heard that cannon was horrible for linux drivers.
Kory

---

### Post by carusoswi on 2008-05-11
> **measekite said:**
> Currently I am using Feisty and have a Canon IP4000.

**#1** I installed the Canon PPD file after selecting Adobe and Postscript Level 2.  I do get pretty good prints but the choices in the print dialog are not up to snuff.

**#2 **I then installed a new printer in Gimp.  I selected Canon and found the IP4000.  I got many more choices except for borderless.  The quality of the print was no where near as good as the printer in **#1** even though they both said 600x600 resolution.

**#3** I then installed a 3rd printer in Gimp using the Turbo Print drivers.  I still did not get a choice for borderless printing so I gave up with that.

For a great OS like Linux and a Good (Great wanabee Photoshop) photo editor like Gimp it has terrible printer support.  Even with the driver that produces good results like the item described in **#1,** the choices are poor and the dialog boxes are a real cluge.

Is there anyway to get good printer support for Gimp?  Do the majority of poster have the same or similar problems with printing.

Until Linux and Gimp get their printing act together it is very difficult to leave Windows behind.

Comments and helo are welcome.

IN MY VIEW, one of Ubuntu's most glaring weak spots is printer support.  I am fully aware that the problem stems from lack of OEM driver support, but, as you point out, until the problem, wherever its source, is solved, migrating permanently away from Windows is not likely for most of us for whom good printer support is important.

I just purchased Lightzone from Lightcrafts.  The license is a cross-platform type that allows me to use the software on MAC WIN or Linux.  I have tried it on XP and on Ubuntu.  Can print (though not a great interface) from XP, but results are terrible in Ubuntu.  My printers include Epson R595 and two Canon i series, i960 and i850.

The Canon appear to be totally unsupported in Ubuntu.  The Epson shows up, but the interface is poor and results are less than optimal.

To print photos, I have to revert to XP where I can achieve some excellent results.

I am biding my time until these printer problems are sorted out.

BTW, I've been very slow to adopt GIMP, but the apt but, in ways, narrow focus of Lightzone forced me to use GIMP to make some adjustments in a couple of photos.  I find myself warming up to that application.

Caruso

---

### Post by measekite on 2008-05-15
> **carusoswi said:**
> IN MY VIEW, one of Ubuntu's most glaring weak spots is printer support.  I am fully aware that the problem stems from lack of OEM driver support, but, as you point out, until the problem, wherever its source, is solved, migrating permanently away from Windows is not likely for most of us for whom good printer support is important.

I just purchased Lightzone from Lightcrafts.  The license is a cross-platform type that allows me to use the software on MAC WIN or Linux.  I have tried it on XP and on Ubuntu.  Can print (though not a great interface) from XP, but results are terrible in Ubuntu.  My printers include Epson R595 and two Canon i series, i960 and i850.

The Canon appear to be totally unsupported in Ubuntu.  The Epson shows up, but the interface is poor and results are less than optimal.

To print photos, I have to revert to XP where I can achieve some excellent results.

I am biding my time until these printer problems are sorted out.

BTW, I've been very slow to adopt GIMP, but the apt but, in ways, narrow focus of Lightzone forced me to use GIMP to make some adjustments in a couple of photos.  I find myself warming up to that application.

Caruso

Canon Japan may have a driver for your Canon printers.  You also need to download the 
and place it in a folder.  Mine is in /etc/cups/ppd/Canon_IP4000-ASF.ppd.  

I did install the cups driver for the Canon.  My IP4000 supports two paper sources; a top sheet feeder and a bottom cassette feeder.  When using some of the software the choice from the driver is either not available or does not work.  To get around this I installed two printers using the same driver.  In cups I made a separate default for each paper source. 

For Gimp 2.2 I installed an Adobe printer from the Gimp print "Setup Printer" and then chose postscript level two and selected [COLOR=Red][B]/etc/cups/ppd/Canon_IP4000-ASF.ppd.  ASF stands for Auto Sheet Feeder.

[/B][COLOR=Black]This is the top feed.

For all of this to work you need to install the original driver you downloaded in CUPS.

[http://www.cups.org/](http://www.cups.org/)

I can now print from Gimp.  For photos I cannot use borderless but I get good resolution 600 and 1200 dpi and the results up to 8.5x11 are excellent.  The Gimp dialog sucks and you need to play around with the sized and borders.

Here is what I do  In the photo I crop for the aspect ration I want.  Then I do this from the Print Dialog:

[COLOR=Blue][B]1. Press the Center Both button
2. Press Original Print Size button
3. Scale the photo after selecting the % radio button
4. Adjust for borders between .14 to .25 for the left and top.  Do not bother with the right and      bottom
5. Print[/B][/COLOR]

Of course you must select the paper size and paper type.  I find that 600dpi is a very good choice for speed and quality.

Please post when you get this working so others who have your printer model can note your experience.


[/COLOR][/COLOR]

---

### Post by carusoswi on 2008-05-16
> **measekite said:**
> Canon Japan may have a driver for your Canon printers.  You also need to download the 
and place it in a folder.  Mine is in /etc/cups/ppd/Canon_IP4000-ASF.ppd.  

I did install the cups driver for the Canon.  My IP4000 supports two paper sources; a top sheet feeder and a bottom cassette feeder.  When using some of the software the choice from the driver is either not available or does not work.  To get around this I installed two printers using the same driver.  In cups I made a separate default for each paper source. 

For Gimp 2.2 I installed an Adobe printer from the Gimp print "Setup Printer" and then chose postscript level two and selected [COLOR=Red][B]/etc/cups/ppd/Canon_IP4000-ASF.ppd.  ASF stands for Auto Sheet Feeder.

[/B][COLOR=Black]This is the top feed.

For all of this to work you need to install the original driver you downloaded in CUPS.

[http://www.cups.org/](http://www.cups.org/)

I can now print from Gimp.  For photos I cannot use borderless but I get good resolution 600 and 1200 dpi and the results up to 8.5x11 are excellent.  The Gimp dialog sucks and you need to play around with the sized and borders.

Here is what I do  In the photo I crop for the aspect ration I want.  Then I do this from the Print Dialog:

[COLOR=Blue][B]1. Press the Center Both button
2. Press Original Print Size button
3. Scale the photo after selecting the % radio button
4. Adjust for borders between .14 to .25 for the left and top.  Do not bother with the right and      bottom
5. Print[/B][/COLOR]

Of course you must select the paper size and paper type.  I find that 600dpi is a very good choice for speed and quality.

Please post when you get this working so others who have your printer model can note your experience.


[/COLOR][/COLOR]

I haven't played around with my Canon printers and Ubuntu 8.04 of late, but have succeeded in mastering the Gimp interface with my Epson R595.  I'm getting perfect prints every time, even borderless.  Obviously, it's not my skill, but a better level of compatibility between the Epson and Ubuntu that makes this possible.

As you noted, the Gimp interface is a bit stubborn when trying to size the photo.  For some reason, when I select borderless and try to adjust the print size to 4 x 6, one or the other of those dimensions will lock up on a size just a fraction smaller than 4 or 6, so that I have a white stripe along one side of the print.  To get around this, I have to mess around clicking and unclicking "Ignore page margins" in combination with the lock/unlock x/y resolution.  After a bit of trial and error, it finally becomes possible for me to increase the understated page size to a whole number (4 or 6 as applicable).

This has to be a bug.

On the other hand, I am grateful for Gimp, since it is, so far the only photo application with which I have been able to achieve quality printed photos.  I find that I have to set brightness under Output Control Common (whatever that is) to around 1.4 in order to get prints that do not appear underexposed.

Perhaps someone can explain that dialog to me.  

Anyhow, I feel as though I am progressing steadily with Ubuntu towards that day when I never have to boot into XP again (not that I loathe XP, I do not).

Caruso

---

### Post by carusoswi on 2008-10-18
Printing for me in 8.10 so far is no better than in previous Ubuntu versions.  Oh, if ever that printing issue would get fixed.  Some have simply gone out and purchased Linux supported printers, but, IMO, none are up to snuff in terms of top quality photo printing, and so, for now, I continue to print from XP.

If I have a large number of photos to print, I generally edit them from within Ubuntu, then, switch to XP to do my printing.

That will just have to do for now.

Caruso

---

### Post by measekite on 2009-01-03
> **carusoswi said:**
> Printing for me in 8.10 so far is no better than in previous Ubuntu versions.  Oh, if ever that printing issue would get fixed.  Some have simply gone out and purchased Linux supported printers, but, IMO, none are up to snuff in terms of top quality photo printing, and so, for now, I continue to print from XP.

If I have a large number of photos to print, I generally edit them from within Ubuntu, then, switch to XP to do my printing.

That will just have to do for now.

Caruso

One thing that few understand is this.  Many are touting a prediction that Linux can get enough market share to impact Windows.

I say no way.  As bad as Windows is there are two things that need to be corrected (maybe a few more) and like you said; it is not happening and nobody knows why.

The printing issue that we discussed is so important and so overlooked I just do not know what to say.  Then there are the installation issues when what you want to install is not in the distro repositioiries.  It is different for each distro .  On top of that you have all these applications files that are placed in folders all over the place.  To add an item to a menu or a panel manually you have to spend mucho time just to find an icon or an executable file.  There are not standardization.

Then there is the poor hardware support by the mfg.  Microsoft was very smart in engaging support from the hardware mfg many years ago and developing some standards.  That brought them to where they are today.  That plus a reasonable GUI that they do not really build on anymore and not such great products.

---

### Post by moodog on 2009-01-05
A lot of threads say to add a new Adobe Postscript Level 2 printer to allow gimp to print, by adding a new printer in the print dialog. Has the print dialog changed in gimp 2.6, or am i missing something? I can't find anywhere how to add a new printer.

---

### Post by Slim Odds on 2009-01-05
> **measekite said:**
> Currently I am using Feisty and have a Canon IP4000.

...

For a great OS like Linux and a Good (Great wanabee Photoshop) photo editor like Gimp it has terrible printer support.


First, upgrade to at least Hardy. You're using an old, unsupported version of Ubuntu. Move up. This often fixes peoples problems outright.

My HP printer and Epson scanner have **always** worked **BETTER** with Ubuntu than Windows.

My USB printer would just disappear from Windows. The drivers for the scanner were a nightmare to get working and would also just fail out of the blue.

Never a problem in Ubuntu.

---

