---
title: "Solid black page when printing pdfs"
date: 2014-04-27
forum: General Help
---

### Post by Mercedes99 on 2014-04-27
I am running 32 bit Ubuntu release 14.04. I have a networked printer, Canon Pixma MX880. For quite some time now, if I try to print a pdf from either Adobe Reader 9 or the Evince Document Viewer I get a page of solid black ink. All other document formats are fine. 

I can print pdfs OK from XPDF, but that package is fairly basic, and it doesn't even show up as a pdf viewer option in the applications list when using the 'Open With' command.

I have tried the printer via the network and via a cabled connection and the result is the same. I have deleted and reinstalled the printer, and reinstalled the Canon drivers, but it doesn't make any difference. Canon are not maintaining Linux drivers for this printer so the drivers are the same ones I downloaded when I first bought the printer, and it used to work, so I can only assume something has changed elsewhere. Since it is affecting both Adobe Reader 9 and Evince I wonder if it is in CUPS?

I have discovered that if I set the pdf to print as an image it will actually print OK.  It's costing me a fortune in black cartridges when I forget, though!

---

### Post by pdc on 2014-04-27
sorry to hear of your problems; one thing folks suggest with pdf is "print as image": a tab in the advanced settings of Adobe printer; as in thumbnail below;

_____________

you felt Canon didn't provide drivers for  your MX880 series printer: they actually provide 32bit and 64bit versions in debian. rpm and source code formats 

as per here [http://support-asia.canon-asia.com/P/search?model=PIXMA+MX886&menu=download&filter=0&tagname=g_os&g_os=Linux](http://support-asia.canon-asia.com/P/search?model=PIXMA+MX886&menu=download&filter=0&tagname=g_os&g_os=Linux)

so a debian driver for you would come from here [http://support-asia.canon-asia.com/contents/ASIA/EN/0100329802.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100329802.html) as a cnijfilter-mx880series-3.50-1-deb.tar.gz and install commands would be:
[COLOR="#FF0000"][B]cd Downloads
tar -zxvf cnijfilter-mx880series-3.50-1-deb.tar.gz
cd cnijfilter-mx880series-3.50-1-deb
./install.sh [/B][/COLOR]

that should get the Canon driver installed for you;

and a **Linux MX880 Guide** comes from here [http://support-asia.canon-asia.com/contents/ASIA/EN/0300468601.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0300468601.html)

.............using the Canon driver gives you a printer config tool that you can load from a terminal > [COLOR="#FF0000"]cngpij -P MX8800USB[/COLOR]

that allows you to edit various of the printer's features ..........as per thumbnail below ....

________

and Canon provide a scanner driver from here [http://support-asia.canon-asia.com/contents/ASIA/EN/0100330802.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100330802.html) installed in the format above

---

### Post by Mercedes99 on 2014-04-28
Thanks for taking the time to reply to my post.    

If you re-read my post, you will see that I have already found that setting the print to "print as image" will work.  I was just hoping that somebody had found a fix for the 'black sheet' bug in normal print mode. 

   I didn't say either that  Canon didn't provide drivers for the MX880 series printers. What I said was that Canon were not maintaining the driver software, so that I thought there was no point in removing and reinstalling the Canon drivers, as the software on their website was identical to what I had originally downloaded when I bought the printer. However, I decided to try downloading it and reinstalling it again, in case something else had altered the default configuration in the initial install, and thereby had broken something. I tried this, but it didn't fix anything.

---

### Post by HermanAB on 2014-04-28
If this works, then it is NOT the printer driver or CUPS:
$ lpr filename.pdf

---

### Post by Mercedes99 on 2014-04-28
If WHAT works, Herman?

---

### Post by marcwiesner on 2014-07-26
I recently starting having this error crop up. I'm trying to diagnose another error (a page full of dots printing behind the PDF). Running lp to print a PDF on a Canon MF4350 with the latest drivers (2.9) produces a solid black page (sans an inch at the top of banded lines).

---

### Post by Keith_Beef on 2014-12-28
I also have this problem, with Ubuntu 14.04 64 bit and an old Epson Stylus Photo 890.

As usual, the problem occurs at exactly the wrong time; my daughter has to print a project she has done during the Christmas holidays.

It's a simple file, two pages long with a small image on page 1, prepared in Libre Office.

I tried printing straight from Libre Office, the page comes out plain black. If I stop the print job and eject the paper, I can see that the text is being printed, but it seems as if it is being printed "in negative", i.e. the white space is being printed in black, and the black text is being printed in pale grey.

This also happened when I generated a PDF that looks fine on the screen; it prints just the same.

From the printer settings, I can print a test page that looks OK.

After looking at a few different settings, I found that in CUPS the printer was set to use the CMYK colour model. When I changed that to RGB and also set the colour model to RGB in Libre Office's settings, printing worked.

---

