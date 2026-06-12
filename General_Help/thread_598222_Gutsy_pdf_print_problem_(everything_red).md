---
title: "Gutsy pdf print problem (everything red)"
date: 2007-10-31
forum: General Help
---

### Post by nikkkko on 2007-10-31
From a clean install of Gutsy and using a HP color laserjet 2605, printing from Acroread turns everything bright red.  Printing from Evince doesn't produce anything at all,  Printing from OpenOffice is fine.  

Any clues?

---

### Post by nikkkko on 2007-10-31
Am I the only Ubuntu 7.10 user who cannot print pdf's?

---

### Post by nikkkko on 2007-11-01
Getting desperate here.  Not being able to print pdf's is a total breakdown, grinding halt, showstopper.  No print, no work, no money, no eat.

---

### Post by mrtchandler on 2007-11-02
The only way I've been able to get PDF's to print properly on Gutsy is to use XPDF, using Adobe Acrobat or KPDF gives different results on different printers, but neither produce a valid/correct reproduction on the printers.
Tony

---

### Post by nikkkko on 2007-11-02
I had this printer working perfectly under Kubuntu Fiesty with Acroread, (kpdf produced poor colour reproduction and couldn't handle transparencies), but I have not tried xpdf. I will try it next week.

Thanks

---

### Post by Sef on 2007-11-02
> I had this printer working perfectly under Kubuntu Fiesty with Acroread....

Sometimes, upgrades will produce bugs where none existed before.

---

### Post by nikkkko on 2007-11-07
I can now print pdf's, just not from Evince, Adobe Reader or Xpdf.

From Evince - can't print files over a certain size, (9 out of 10 of mine are too big)
From Adobe Reader - everything prints red, (seems to be an Adobe problem but I can't be sure)
From Xpdf - can't print at all, (don't know how to make lpr work and entering the name of the printer - as for Inkscape - does nothing.)

However, I installed the latest version of hplip from the hplip website, having previously uninstalled the version from the Ubuntu repositories and if I open the HP Device Manager toolbox and select the file I can print from there. 

This is not how I imagined printing pdf's and I still believe, (hope), it will be possible to print from at least one of the pdf applications, (preferably Xpdf as it seems to be the only one which displays my pdf's correctly).

---

### Post by jmagsho on 2007-11-07
nikkkko, you're not the only one having issues printing PDF's with Gutsy.  I too have been pulling my hair out over this, and Evince or XPDF are not options for me at this point.

I had it partially working with the latest HPLIP and the HP toolbox, however it would appear that yesterday's CUPS update totally hosed both of them.    Now I am considering re-installin

---

### Post by strange_cathect on 2007-11-07
I can also confirm this. _ But I'm also having the same problem with .tif files_.

---

### Post by nikkkko on 2007-11-09
I finally have Xpdf printing.  I don't know how or why it suddenly decided to print, but it does.  

My next problem is that when it does print an A4 pdf document, it does so in letter format.  Great.  I have set the default paper size to A4, both from localhost:631 and from System>Administration>Printing, (even though localhost:631 defaults were changed, this was not reflected in the Printing toolbox), but that made no difference. I have checked from the HP Toolbox that A4 is the default and it is, (three places to change the same set of options - that can't be right). I have tried printing with the command, 'lpr PaperSize=A4' but that doesn't print anything at all, and anyway, I don't really know what I'm doing there.

As always, any clues would be useful.

---

### Post by jmagsho on 2007-11-09
Guys,

This has been logged as bug 145772 in Launchpad ([https://bugs.launchpad.net/ubuntu/+source/acroread/+bug/145772](https://bugs.launchpad.net/ubuntu/+source/acroread/+bug/145772))

---

### Post by shane2peru on 2007-11-09
Well this is really sorry since I was able to print pdf in Fiesty!  Now I have to go to my wife's computer to print my pdf's from Windows!  Un-impressive to say the least!

Shane

---

### Post by rrwo on 2007-11-10
I can print with Acroread to various HP Network printers, no problem.

But after upgrading to Gutsy, I cannot print with evince though. The pages come out blank. Even when I run print preview, the pages are blank.

---

### Post by nikkkko on 2007-11-12
Ubuntu has a problem with pdf's in general, which is a shame as this format is used widely  in design and print.  Firstly, neither Evince nor Kpdf can display a pdf correctly.  If there is a gradient fill or a transparency, this will not be represented.  Secondlly, it appears some colours may be incorrectly represented, depending on the origin of the document.  (I work with a Mac/Adobe user and light green never looks right).  I have tried most of the pdf viewers and the only one I trust to show me what I think looks like the original document, is Adobe Reader.  Second choice would be Xpdf, which does show transparencies and appears to show the right colours, but produces jagged lines instead of smooth curves.

Then there is printing.  As I've already posted, the only way for me to print correctly is via the HP Printing toolbox.

I moved to Linux about 4 years ago but work more and more with pdfs and I'm starting to dream about shiny new Mac's.  I need help.

---

### Post by frederik.nnaji on 2007-11-24
same here

- newest acroread won't print my pdf at all.. 
- evince crops the lower bit of the document, even if i scale it down to 88% size... always crops the same line...

my printer. HP deskjet 845c  | usb

 i am getting very depressed.

been hoping for a working desktop alternative to windoze since 2001... tried out different linux distros again and again, including mandrake(now mandriva), gentoo, fedora, suse and all.. now i settled with ubuntu, but it disappoints me in certain fields.. unfortunately!

hope the major issues like WLAN, Webcam, Scanners and such elementary things as printing will soon be resolved, this is very painful for me!

thanks..

---

### Post by neha268 on 2007-11-27
Hi Frederik,
Do you get any error message on printing from Adobe Reader? What do the cups logs say?
You could try bumping up the CUPS logging level and check. To do that find cupsd.conf (mostly residing in /etc/cups) and change the "LogLevel" to debug. Then restart the CUPS server (/etc/init.d/cupsys restart). The error logfile would be /var/log/cups/error_log by default (the value of ErrorLog in cupsd.conf). 


Nikkkko,
You are using the HPLIP driver, aren't you? In that case could you check what version of GhostScript you have on your machine? If it is "8.61 pre-release", try upgrading to the stable release of 8.61 (available for download at [http://pages.cs.wisc.edu/~ghost/doc/GPL/gpl861.htm](http://pages.cs.wisc.edu/~ghost/doc/GPL/gpl861.htm)). It is possible that this fixes the red prints you are getting from Adobe Reader.

You could probably try the PostScript driver ([http://www.linuxprinting.org/show_printer.cgi?recnum=HP-Color_LaserJet_2605](http://www.linuxprinting.org/show_printer.cgi?recnum=HP-Color_LaserJet_2605)) and see if that resolves the issue.

It might be a good idea to post queries regarding the Adobe Reader on the official forums ([http://www.adobeforums.com/webx/.3bc433df](http://www.adobeforums.com/webx/.3bc433df)).

Regards,
Neha

---

### Post by nikkkko on 2007-11-28
Hi Neha,

The version of Ghostscript I am using is 8.61, I have tried the linuxprinting.org.ppd file and I have posted in the Adobe forums too.  I have also posted in the HPLIP mailing list and the HP support web site.  HP even rang me to see if they could help 

I am fairly convinced it is an Adobe problem as there was an identical issue with Adobe Reader on the Mac some time earlier this year.  However, I didn't get much luck with my thread on their forums - not too many Linux users with the same issue, I suppose.

---

### Post by 11hjpphty76lkjj on 2007-11-29
Nikkko,

Can you send me the link to the launchpad.net question you submitted?  I'm not seeing it...and I do all the support requests. Maybe I missed it.  I'm also curious who from HP rang you?

Thanks for the info.

Aaron

---

### Post by nikkkko on 2007-11-30
Aaron,

You didn't miss it, I got my facts wrong.  I actually posted to the HPLIP mailing list whilst trying to resolve the red printing problem because I couldn't run HPSetup.  (A problem with the 'Next' button being greyed out).  When I solved this I subsequently posted in the Adobe forum because it appeared not be be a HPLIP problem : printing from HP Toolbox is currently the only accurate way of printing a pdf for me.

I was rung by HP France having posted in the US support section! (I live in France).  I wanted to know if the individual cmyk cartridges could be adjusted on the CLJ 2605 or whether there was a colour profile available.  The support agent wasn't sure on either question and because I wasn't running Windows, we didn't get very far.

---

### Post by 11hjpphty76lkjj on 2007-11-30
Oh okay.  I may recall your post to the mailing list now. Although we aren't using it anymore so I wasn't cross referencing.  Anyway just wanted to make sure that someone wasn't falsely saying they where with HPLIP and calling you. :)
A

---

### Post by erikringmar on 2008-04-07
Hiya, 

I can confirm the red print with HP color laserjet 2605, using Kpdf.  It's really a shame.  My daughter, using Feisty on her computer, is making fun of me.

Why Gutsy, why?

Hoping the next update will improve things.

Erik

---

### Post by shane2peru on 2008-04-07
> **erikringmar said:**
> Hiya, 

I can confirm the red print with HP color laserjet 2605, using Kpdf.  It's really a shame.  My daughter, using Feisty on her computer, is making fun of me.

Why Gutsy, why?

Hoping the next update will improve things.

Erik

yeah, this thread is pretty much dead, since Hardy is coming out in just about 20 days or so.  I did get Adobe printing fine, however you need to download and install the Adobe 8.1 version.  I also got it running well!  It was too slow for me on 32bit, so now I´m running 64bit.  Much better.

Shane

---

### Post by nikkkko on 2008-04-09
Not... quite... dead...

And not an Ubuntu problem, as far as I am aware.  It should be solved in the next version of Acroread.

This from the [Adobe forums]("http://www.adobeforums.com/webx?13@@.3c0533da/13"):

> A workaround has been added in the upcoming version of Adobe Reader (8.1.2). An option has been added in the preferences, namely "brokenCRDs". This value is set to "false" by default and can be modified to "true" if one faces the red background issue.

Then
> This change was made after the program was closed. It would be available in the official release of 8.1.2
It has been added in the preferences file (reader_prefs files). Here the value of "brokenCRDs" cane be changed to "true" when using one of the HP printers showing the red wash issue. 
I'm not sure what version of Acroread is in the repos, but if there should be fixable at some point.

---

### Post by shane2peru on 2008-04-10
> **nikkkko said:**
> Not... quite... dead....

You are right, I forget that some people don't update to the next version.   I'm always sitting on the edge of my seat waiting for it to be released so I can download and install it!  :lolflag:

Anyway, if you would like to download Adobe go here:  [http://www.adobe.com/products/acrobat/readstep2_allversions.html](http://www.adobe.com/products/acrobat/readstep2_allversions.html)

And download the Linux version, you should be able to even download the deb and install it!  If you have a 64bit Ubuntu installed, you will need to download the tar.gz file not the deb.  After downloading the deb you can double click that file and open it with gdeb and it will install it for you.  You will probably need to uninstall the one you already have on your system.  This should get you working correctly.  If you need help just post back here.

Shane

---

### Post by nikkkko on 2008-04-14
> You are right, I forget that some people don't update to the next version.
I was part of a beta testing group for Adobe and I've been using 8.1.2 for a while.  However, the version I have is not the same as the 8.1.2  now available for download on their web site, (so what are version number for then?). Today I downloaded the apparently not so new version of 8.1.2 and changed the reader_prefs file found at ```
/home/'yourhome'/.adobe/Acrobat/8.0/Preferences/reader_prefs
```
and altered the line
```
/brokenCRDs [/b false]
```
to
```
/brokenCRDs [/b true]
```
The reader_prefs file may not contain this line until you try to print, so go through the printing process first.  I simply deleted my old file and printed something out to recreate a new one, altered the line  and finally I can print without seeing red. Literally and metaphorically.

---

### Post by Tomy on 2008-07-16
Thanks nikkko -- I no longer see red. You're my hero today.

We use ubuntu @work and a couple people have had the "red" pdf problem, but not on all pdfs. Most of us have upgraded to Hardy but still have the problem.

---

