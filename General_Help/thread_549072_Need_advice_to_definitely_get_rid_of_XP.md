---
title: "Need advice to definitely get rid of XP"
date: 2007-09-12
forum: General Help
---

### Post by nvteighen on 2007-09-12
Hi,
I'm so fascinated with Linux (in general, not just Ubuntu) and I hate Windows so much that I really feel I can get rid of XP and make this dual-boot machine into a pure-Ubuntu. But, I fear I can be too risky, specially before starting university.

My doubt is this: I study philology, so what I need is a good text processor and a good pdf creator...  I use Open Office since long time (from Windows) and know it has a great Word-compatibility, but I'd like to appreciate to know if there's any major compatibility issue regarding texts, fonts, footnotes and tables. Also, would like to know how reliable is Ubuntu's OpenOffice PDF's export... I've had some minor errors with spaces between characters, but don't know whether the issue is the conversion (weird, because in Windows Open Office converted to PDF without problems).

If the problems are minor, Windows will be history to me.

---

### Post by dcstar on 2007-09-12
> **nvteighen said:**
> Hi,
I'm so fascinated with Linux (in general, not just Ubuntu) and I hate Windows so much that I really feel I can get rid of XP and make this dual-boot machine into a pure-Ubuntu. But, I fear I can be too risky, specially before starting university.

My doubt is this: I study philology, so what I need is a good text processor and a good pdf creator...  I use Open Office since long time (from Windows) and know it has a great Word-compatibility, but I'd like to appreciate to know if there's any major compatibility issue regarding texts, fonts, footnotes and tables. Also, would like to know how reliable is Ubuntu's OpenOffice PDF's export... I've had some minor errors with spaces between characters, but don't know whether the issue is the conversion (weird, because in Windows Open Office converted to PDF without problems).

If the problems are minor, Windows will be history to me.

Are the font issues with the various Windows fonts that you need to install separately (due to licensing issues)?

---

### Post by p_quarles on 2007-09-12
The OpenOffice.org PDF export is usually adequate, but it's more reliable to use a dedicated PDF virtual printer. You can set one up thusly:
```
sudo apt-get install cups-pdf
```
Then:
```
gksudo gedit /etc/cups/cupsd.conf
```Change "RunAsUser Yes" to "RunAsUser No."
Once that's taken care of, go to System >> Administration >> Printing, select "Add a Printer," and then choose "local printer." Under the "detected printers" area, you should see the option to select "PDF printer." Use that, and when it asks you to select a printer driver, select "postscript color printer." 

Anyway, give that a try, and that should clear up any issues with making PDFs. This works as a normal printer, by the way: you'll have to select the printer from the printing menu in Writer or whatever program you want to use. The only difference is that it makes a document instead of printing to paper.

---

### Post by nvteighen on 2007-09-12
> **dcstar said:**
> Are the font issues with the various Windows fonts that you need to install separately (due to licensing issues)?

I may have not been clear enough. I was trying to ask if there are font issues in Open Office for example, at rendering (it's very important when working with Ancient Greek to see all diacritics!) or any other major issue regarding fonts.

> **p_quarles said:**
> The OpenOffice.org PDF export is usually adequate, but it's more reliable to use a dedicated PDF virtual printer. You can set one up thusly:
```
sudo apt-get install cups-pdf
```
Then:
```
gksudo gedit /etc/cups/cupsd.conf
```Change "RunAsUser Yes" to "RunAsUser No."
Once that's taken care of, go to System >> Administration >> Printing, select "Add a Printer," and then choose "local printer." Under the "detected printers" area, you should see the option to select "PDF printer." Use that, and when it asks you to select a printer driver, select "postscript color printer." 

Anyway, give that a try, and that should clear up any issues with making PDFs. This works as a normal printer, by the way: you'll have to select the printer from the printing menu in Writer or whatever program you want to use. The only difference is that it makes a document instead of printing to paper.

I've installed cups-pdf, but /etc/cups/cupsd.conf didn't had any "RunAsUser" line. I tried to do a PDF and now I don't know where it is so I can see if it's better to me or not!

EDIT: I found the PDF file... it was on a new PDF folder at my home. Wow. Much better than Open Office's export... The problem had to do with text in tables. Thanks!

Thanks!

---

### Post by Tautoa on 2007-09-12
I'm in a similar position - about to start Uni, recently switched to Ubuntu (actually, it was in June, but I'm still not as proficient with Linux as I was with Windows)

Last week I got rid of my XP partition, so I'm now running pure Kubuntu. Two days after I did this, my University sent out it's welcome pack on USB sticks..., which Linux refuses to recognise...

This isn't a request for help, I got the welcome pack emailed to me by a friend, I'm just saying that maybe you should keep XP until you start Uni, just in case...

---

### Post by nvteighen on 2007-09-12
> **Tautoa said:**
> I'm in a similar position - about to start Uni, recently switched to Ubuntu (actually, it was in June, but I'm still not as proficient with Linux as I was with Windows)

Last week I got rid of my XP partition, so I'm now running pure Kubuntu. Two days after I did this, my University sent out it's welcome pack on USB sticks..., which Linux refuses to recognise...

This isn't a request for help, I got the welcome pack emailed to me by a friend, I'm just saying that maybe you should keep XP until you start Uni, just in case...

Hmm... Well, my Uni won't do that; they use other methods (a lot of postmail, letters... it's annoying; it's almost like spam!). If eventually it happens that they send me something occasional that has to be read in XP, I can use the computers at the Uni. My concern is more about regular work, specially if I have to make a team-work, for example (anyway, there seems to be a pro-Mac culture...).

---

### Post by aot2002 on 2007-09-12
I use KDE virtual printer for PDF and convert office WORD docs to PDF for saving them and sending them to my gmail account I havent had any issues with fonts or wierd characters 

EXCEPT when converting company visio type designs the arrows never seem to line up

---

### Post by nvteighen on 2007-09-12
So, it seems that I can delete XP, as I use my computer for browsing and text-processing... and as I never had the rest of MS Office (Excel, PPoint), I can use OpenOffice for that as I have done always when ocassionally have to do an oral presentation.

---

