---
title: "do MS Office and Firefox work in Ubuntu?"
date: 2008-01-18
forum: General Help
---

### Post by Joanna92 on 2008-01-18
I am very interested in buying an Ubuntu equipped Dell, but am wondering if I would still be able to use Office and Firefox with Ubuntu?

I need to continue using Office for compatibility with my office's computers, and I simply like Firefox.

Also wondering if my Palm Desktop software would be supported in Ubuntu.

Couldn't find any answers to these questions on the site...


thanks,
  Joanne

---

### Post by chrisccoulson on 2008-01-18
Firefox comes with Ubuntu by default, as there is a native Linux version of Firefox

As an alternative to using MS Office, you could try Openoffice, which is also included by default. However, if you are worried about compatibility issues, you can run MS Office with Wine (which is completely free), or Crossover Office (which is based on Wine, but will cost some money). I suggest having a look through the forums about setting up Wine. There is no Linux version of MS Office, which is why you need to use Wine or Crossover.

I run MS Office on Crossover Office Pro with no problems at all. The reason I run Crossover Office Pro is for the ability to share installed applications across multiple users. With Wine, each user will need to install the application to their own profile, which uses more disk space (if there are 5 users using Office, then Office will be installed in 5 different profiles). However, if you are the only user of the machine, there is no reason not to use Wine.

I can't answer the question about your Palm desktop.

Hope that helps:)

---

### Post by Martin Witte on 2008-01-18
you could use wine instead of crossover office, wine is freely available in the repositories. see [http://appdb.winehq.org/appview.php?appId=31](http://appdb.winehq.org/appview.php?appId=31) for compatibility with office versions, i have good results with office 2000 running on wine on ubuntu

---

### Post by AlanR8 on 2008-01-18
Firefox is my browser of choice. Has been for about 3 years now especially under windows. I've used Office (2003) under Crossover office in Linux without to many problems but did not get Outlook working so I could use it as a mail client. So I switched to Mozilla Thunderbird and have not looked back since!

I was doing some training design work earlier last year with a UK major bank and found some issues when opening their Word templates/documents under Open Office so I ran Crossover so I could use MS again.

These days I'm 100% free of MS!

---

### Post by someonestolemyname on 2008-01-18
Firefox is completely cross-platform, as said above. If you are going to dual-boot, you can even use your existing Firefox profile in Ubuntu:

[http://cybernetnews.com/2007/10/24/cybernotes-share-a-firefox-profile-between-ubuntu-and-windows/]("http://cybernetnews.com/2007/10/24/cybernotes-share-a-firefox-profile-between-ubuntu-and-windows/")

As for office, unless you are doing advanced things in Office (in which case see above), OpenOffice works great. It saves in Word format, and rarely has problems for most word processing, etc.

---

### Post by Whiffle on 2008-01-18
The palm desktop software will not work on ubuntu, but there is software that will allow you to sync it.

---

### Post by HermanAB on 2008-01-18
Up to Office 2000 works on Wine (Free).  

For Office 2003, you need CxOffice (The leading edge of Wine, costs a few dollars).

Office 2007 won't run on Linux, unless you install a Virtual Machine with Vista.

Palm sync software has been available on Linux for many years.

Cheers,

Herman

---

### Post by Joanna92 on 2008-01-18
Thanks for all the help, guys!

A few more details:

I have MS Office XP, and mainly use Word and Excel.  Powerpoint, once in a long while.  My main concern is taking Word and Excel docs back and forth between an Ubuntu PC and my work PC...just want to make sure that I won't have screwed up formatting or anything like that.  

Oops, and I almost forgot: the other 3 programs that I use a lot are

1. Adobe Acrobat (to read PDFs and also to convert Word docs into PDFs) 
2. WinAmp for Internet radio and ripping/burning CDs
3. MS Photoeditor for basic mods of JPEG photos

I guess my main concern here is that whatever new files or docs I create in Ubuntu be easily usable on Windows PCs and vice versa.

---

### Post by Levander on 2008-01-19
acrobat - yes acrobat works, but Gutsy uses some "evince" applications to read PDF's by default.  By default because Gnash is free software, acrobat is just free of charge.

winamp - no.  Small company called Nullsoft writes Winamp, and it's for Windows only.  However, there is plenty of jukebox software on Gnome.  I use Rhythmbox because it's the Ubuntu default, but I've been thinking about switching to Banshee.

ms photoeditor - probably not, but there are plenty of free image editors on Ubuntu.  The full blown free one, the alternative to Photoshop is called Gimp.  It'll be interesting to see what more simple and basic (probably more like MS Photoeditor) picture editor people recommend.

---

### Post by ugm6hr on 2008-01-19
> **Levander said:**
> acrobat - yes acrobat works, but Gutsy uses some "evince" applications to read PDF's by default.  By default because Gnash is free software, acrobat is just free of charge.

winamp - no.  Small company called Nullsoft writes Winamp, and it's for Windows only.  However, there is plenty of jukebox software on Gnome.  I use Rhythmbox because it's the Ubuntu default, but I've been thinking about switching to Banshee.

ms photoeditor - probably not, but there are plenty of free image editors on Ubuntu.  The full blown free one, the alternative to Photoshop is called Gimp.  It'll be interesting to see what more simple and basic (probably more like MS Photoeditor) picture editor people recommend.

You can get Adobe's official reader for Linux / Ubuntu if you want, but I have had little problem with evince (default in Ubuntu), except reading *edited* pdfs.  For those, xpdf works great.  If you have the full version of Acrobat, there is nothing in Linux comparable.  If it is just to create pdfs from Office etc, that is easy in Ubuntu (either from OpenOffice directly, or using the pdf printer).  If you need to be able to complete fields in pdfs, then you are out of luck.  There are ways to simply edit a pdf (apparently), but they permanently change the pdf rather than filling in the fields.

Winamp equivalent is either XMMS, or my preferred option Audacious (for streaming mp3 radio etc).  There are lots of other music playing apps more akin to the iTunes interface too.

I have never used MS Photoeditor, but Picasa is pretty good for photo editing, and works great in Ubuntu (and Windows too!).  As mentioned, GIMP is much more advanced.

---

### Post by Canuckelhead on 2008-01-19
For almost any documents I use Open Office.  I've never had a problem with formatting but I do hear of occasional minor issues.

For work however I do create VBA scripts for some of our Word/Excel docs.  If you are in to that sort of thing I'd recommend Wine or a virtual box...  Virtual Box works well enough for me.

VirtualBox is, however, useless if you don't already have a Win Disk and Office.

I don't like using them, but they pay the bills right now.

---

