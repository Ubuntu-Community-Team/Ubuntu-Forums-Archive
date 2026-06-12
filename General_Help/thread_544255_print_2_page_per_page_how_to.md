---
title: "print 2 page per page how to"
date: 2007-09-06
forum: General Help
---

### Post by HenkHarmsen on 2007-09-06
My HP4100n laser printer could print 2 pages per page under Windows XP. 
Under Ubuntu the printer works fine, but the 2 page per page feature has disappeared. 
It does not show up in any window [printer properties; open office, firefox etc].
Who has an idea how I can get this feature back on the radar?
Thanks
Henk

---

### Post by southernman on 2007-09-06
When you select File > Print and the print dialog box opens, select the "job" tab and change the default number of copies to print...

---

### Post by anaconda on 2007-09-06
eg. Adobe reader can print multiple pages per sheet in ubuntu..  But not all programs can do that.

Just search for programs that can do the job

---

### Post by ubuntukerala1980 on 2007-09-06
System -> Administration -> Printing
Select your printer
Click properties 
Click the tab paper
Layout 
        Double sided 
                             Long edge (standared) 
This is what i did
For my printer

---

### Post by HenkHarmsen on 2007-09-06
Thanks all !

Southernman: after file>print, there is no 'job' tab, I can only select 'properties' [firefox]; in oo writer there is 'properties' and 'options'. but none of these give me the 2 page/page option.

anaconda: indeed, after trying out a few programs i discovered the desired option in scribus and abiword, but not in open office or in firefox. 

kiran.bhaskaran.nair: just tried your option, this just gives me 2 pages of print, not the 2-up option. 

is the conclusion that windows provides this option via the driver and linux via the application itself?

---

### Post by southernman on 2007-09-06
HenkHarmsen - In my suggestion it was using gedit (should have specified) however, doing the same thing in Firefox (File > Print) the option to select the number of copies is in the window that opens on the right hand side. I just looked in Oo writer, and I see the same thing. The option to set the number of copies is indeed there on my system, which is Feisty.

Screeny attached has FF print window on left and Oo on right.

---

### Post by HenkHarmsen on 2007-09-06
Hi Southernman, that option gives me 2 copies of the document that i want to print. What I want is 2 pages on 1 page, now I get 2 x 2 pages = 4 pages...

---

### Post by southernman on 2007-09-06
Well, I wasn't exactly clear what you wanted to do... obviously.

---

### Post by yabbadabbadont on 2007-09-06
> **southernman said:**
> Well, I wasn't exactly clear what you wanted to do... obviously.

Was to me.  "2 page per page"  ;)

---

### Post by rickfitz on 2007-09-20
Not a perfect solution, but works for me on Feisty:
Install cups-pdf. Then from any application, print to the CUPS/PDF-printer, and a pdf file appears in your ~/PDF directory.
Open the pdf file using the standard "Document Viewer" (evince), and you can print 2 (or 4 or whatever) pages per sheet, using the "Page Setup" tab ("Pages per sheet" option).
So the trick is to print to a pdf file first, then you've got proper control of your printing.
HTH,
Rick.

---

