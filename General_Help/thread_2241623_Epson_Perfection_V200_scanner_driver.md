---
title: "Epson Perfection V200 scanner driver?"
date: 2014-08-27
forum: General Help
---

### Post by 2CV67 on 2014-08-27
I have used my Epson Perfection V200 Photo scanner for several years with drivers from the Avasys site, then more recently from Epson.

But I just junked my old 32-bit PC & am firing up a new 64-bit PC with Ubuntu 14.04.1.

The scanner is not detected by simple scan.

I tried to find drivers but Avasys says they transfered everything to Epson & Epson seems to have no more drivers available for Linux...

I did find a few threads mentioning 64-bit drivers for this scanner, so I think they must have existed at one time.

Can anybody suggest where I might be able to find copies?

Or any other way of getting the scanner working?

Thanks for any suggestions! :)

Edit: I didn't update the details in my signature yet!

---

### Post by rbmorse on 2014-08-27
You can get still get Linux drivers from the Epson site.  You might have to scroll down in the list of O/S choices to find Linux....it's on the bottom of the list. 

I can't post a direct link...their site is having problems right now, but drivers for the Perfection V200 do show up in the search results and the version numbers listed are current.

---

### Post by 2CV67 on 2014-08-27
Ah, just a temporary site problem?
I hope so!

I spent a lot of time on the Epson support/download site(s) and did find the right place for the V200 with Linux:

[http://www.epson.com/cgi-bin/Store/support/supDetail.jsp?oid=88043&BV_UseBVCookie=yes&infoType=Downloads&platform=OSF_O_LINUX](http://www.epson.com/cgi-bin/Store/support/supDetail.jsp?oid=88043&BV_UseBVCookie=yes&infoType=Downloads&platform=OSF_O_LINUX)

But it only took me to a page where there were "zero" items available.

I would be very pleased to have any further details of sites, package names etc...

---

### Post by rbmorse on 2014-08-27
It's a little confusing (us Linux users don't want things to be too easy, right?).  

Try this one:  

[http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX](http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX)

enter "V200 Photo" in the search dialog, make sure "linux" is selected in the rotary below then click on the little magnifying glass icon. 

that should get you to a download page with two file selectors, you need both.  The first selector will take you to the main iScan page.  Chose the .deb download that's appropriate for your installation (will be one of the ltdl7 .deb files) and also the iScan data .deb file listed below. The second selector button will take you the the V200 specific driver plugin required. Again, download the appropriate .deb for your installation.  

You will end up downloading three files:, the main iScan .deb package, the iScan data .deb file and the gt-F670 plugin .deb.  All are required. 

You may get a "page not found" error.  This is symptomatic of the problems on the site. Refresh the page and if necessary reload the search dialog. Eventually it will take you to the download page.

---

### Post by 2CV67 on 2014-08-28
Thanks very much for your persistence!

I did find the downloads as you suggested, though I would have given up without your observations!

Just a few other wrinkles to iron out before I actually try them...

Thanks again :D

---

### Post by 2CV67 on 2014-08-28
OK - it is up & running, as well (or as poorly) as ever!
Criticisms are the blue tint & the impossibility of saving settings.

Thanks again for your help!

---

### Post by 2CV67 on 2014-08-30
I spoke too soon...

It is not running as well as before.

The JPG option is greyed out & unusable, so all available options produce very large files for the usage I frequently require - e-mail attachments.

A4 color document at 150dpi produces:
PNG - 3MB
PCX - 8MB
PNM - 7MB
TIFF - 7MB
PDF - 7MB
Sticking to PNG but reducing dpi:
150dpi - 3MB
72dpi - 800kB but fuzzy
50dpi - 400kB but very fuzzy

With my previous version, I got relatively better results with 150dpi  & JPG compacting.

Does everybody lose JPG option with this version?
iscan_2.29.3-1~usb0.1.ltdl7_amd64.deb
iscan-data_1.29.0-2_all.deb
iscan-plugin-gt-f670_2.1.2-1_amd64.deb

Is there an answer?

Déjà vu:
[http://ubuntuforums.org/showthread.php?t=1807093](http://ubuntuforums.org/showthread.php?t=1807093)

---

### Post by 2CV67 on 2014-09-03
OK - I found an answer here:
[http://askubuntu.com/questions/127591/epson-scanner-requires-libjpeg-version-6-where-how-can-i-find-this](http://askubuntu.com/questions/127591/epson-scanner-requires-libjpeg-version-6-where-how-can-i-find-this)

I installed libjpeg62 from Synapt (even though there are numerous libjpegxxx's already installed).

JPEG is now available & produces a very decent-looking A4 150dpi color document in 406KB.
Compared with 3MB in PNG.

This scanner now works very well for me, again.
Until the next upgrade, no doubt...

---

