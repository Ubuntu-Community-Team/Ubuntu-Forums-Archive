---
title: "font rendering problem"
date: 2007-10-28
forum: General Help
---

### Post by kikke on 2007-10-28
I have a serious problem with font rendering, I read the discussions about new patched freetype in Gutsy but the problem is seems unsolved to me. I tried old patched libraries and the latest official, I tried to change the font rendering settings with dpkg-reconfigure fontconfig-config.

Look at this picture: 
[IMG]http://kepfeltoltes.hu/071028/K_perny_k_p_www.kepfeltoltes.hu_.gif[/IMG]

This rendering problem occurs between 10-14pt with the calibri and cambria fonts.
Anybody can solve this?

---

### Post by kikke on 2007-10-28
SOLVED!!!!

With 1.0 version of font!
The 1.02 seems patched against Linux, so be careful and keep safe place of your fonts!
(I found here: [http://www.microsoft.com/uk/office/preview/beta/converter.mspx](http://www.microsoft.com/uk/office/preview/beta/converter.mspx))

---

### Post by WorLord on 2007-11-04
SWEET BABIES

I thought there was something wrong with my renderer, also.  You just solved a problem that's been bugging me for hours!!  Thanks a million!

(Now using Calibri 12pt as my system font!)

Although I have to wonder what it is about Gnome, specifically, that doesn't like this font.  Firefox and K-applications will render this just fine at any point size - only the Gnome font manager seems to refuse to render Calibri 1.02 at the specified sizes, but I've got my fonts backed up now anyway.

---

### Post by wersdaluv on 2007-12-12
> **kikke said:**
> SOLVED!!!!

With 1.0 version of font!
The 1.02 seems patched against Linux, so be careful and keep safe place of your fonts!
(I found here: [http://www.microsoft.com/uk/office/preview/beta/converter.mspx](http://www.microsoft.com/uk/office/preview/beta/converter.mspx))

Hmmm... Which is the file?? :)

:guitar:

---

### Post by kikke on 2007-12-13
Here (on that page):

---
Updating Previous Releases of Microsoft Office with the Compatibility Pack (Beta 2 Technical Refresh)
1.	
(Recommended) Bookmark this page to your Internet browser.

2.	
Ensure your system is up to date by installing all high-priority/required updates on Microsoft Update (required for Office XP and Office 2003 users).

3.	
Download the Compatibility Pack by clicking the preferred language version below and saving the file to your hard disk.&#8226;	
[COLOR="RoyalBlue"]English Microsoft Office Compatibility Pack for Word, Excel, and PowerPoint 2007 File Formats (Beta 2 Technical Refresh)[/COLOR]
---

---

### Post by wersdaluv on 2007-12-13
> **kikke said:**
> Here (on that page):

---
Updating Previous Releases of Microsoft Office with the Compatibility Pack (Beta 2 Technical Refresh)
1.	
(Recommended) Bookmark this page to your Internet browser.

2.	
Ensure your system is up to date by installing all high-priority/required updates on Microsoft Update (required for Office XP and Office 2003 users).

3.	
Download the Compatibility Pack by clicking the preferred language version below and saving the file to your hard disk.•	
[COLOR="RoyalBlue"]English Microsoft Office Compatibility Pack for Word, Excel, and PowerPoint 2007 File Formats (Beta 2 Technical Refresh)[/COLOR]
---

How do I install it? :(

hehehe

:guitar:

Thanks so much for the quick reply!!!!

:guitar:

---

### Post by kikke on 2007-12-13
Download the file from link.
Create a directory (cfonttemp or anything) and move the file to there.

Then open a terminal and 'cd' to that dir.
---
#~/Desktop/cfonttemp
---

expand the files from the exe with cabextract! (Install it with sudo apt-get install cabextract.)
---
#cabextract O2007Cnv.exe
Extracting cabinet: O2007Cnv.exe
  extracting EULA
  extracting eula.txt
  extracting O12Conv.cab
  extracting O12Conv.msi
  extracting README.HTM

All done, no errors.
---

expand the files from O12Conv.cab
---
#cabextract O12Conv.cab
---

create a dir for fonts and move all .TTF and .TTC to there
---
#mkdir cfonts
#mv *.TTF cfonts
#mv *.TTC cfonts
---

You can move the cfonts directory to /usr/share/fonts/truetype/
---
#sudo mv cfonts /usr/share/fonts/truetype
#sudo chown -R root:root /usr/share/fonts/truetype/cfonts/
---

Now you can remove the cfonttemp directory from your desktop.
That's all.

Best wishes! :)

---

### Post by wersdaluv on 2007-12-13
Thank you very very very very very much!

Very comprehensive instructions! You should make a howto in the howto section of this forum. People will love it!

---

