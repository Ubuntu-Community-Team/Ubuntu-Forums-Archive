---
title: "Issue printing document from Lotus Notes v8.0"
date: 2007-10-19
forum: General Help
---

### Post by chouf on 2007-10-19
Hi all,

I've installed Lotus Notes v8.0 on my laptop running Ubuntu (upgraded yesterday to the new version). The issue is not related (I think), but I'm not able to print from Lotus Notes. I've a USB Deskjet HP printer and a PDF printer. Any document I print from other applications such as Firefox, OpenOffice etc... works perfectly only from Lotus Notes 8, I get nothing.

If I print to PDF from Lotus Notes, I get a blank PDF labelled "champs.pdf"
If I print to the USB Deskjet, the job is sent but automatically switches to status "stopped" in the printer queue window.
Even exporting a document from Lotus Notes in TIFF format for example doesn't work.

I've no clue if this is related, but Lotus Notes is based on Eclipse.

Would anyone have clue where/what the problem could be?

Thanks in advance

Chouf

---

### Post by chouf on 2007-11-15
even after the upgrade to Gutsy, I'm still experiencing the same printing problem.
would anyone have a clue what the issue could be?

---

### Post by mrat on 2007-12-03
Hi

Same issue on 7.10...

If I get anywhere I will let you know.

Regards
Mark

---

### Post by chouf on 2007-12-03
yeah it's weird.
even when I use File > Export, an email or an expense (basically any document) from Lotus Notes, it still doesn't give me anything.
I tried to select everything, and the print preview works fine; but when I print to PDF or to a small deskjet it just doesn't work.
I have of course no problem printing from other programs

---

### Post by mrat on 2007-12-10
Getting warmer but not much time spent on this at the moment... 

I think Champs is short for Cham(?) Post Script. When I look at the Complete Jobs in the queue, I see loads of "ChamixPrintDefault", which are docs printed from Notes. Stuff does come out to printers, but all streched. If I can recall correctly, the other chap at work on 7.04 is having the same issue. When printing to CUPS PDF, does like we are experiencing... blank "champs.pdf".

---

### Post by mrat on 2007-12-12
Got it, so you need to not only have Firefox, and maybe an additional Firefox with Iced Tea JRE for Notes to use, but also "xulrunner-gnome-support" to get printing to work. Release Notes state XulRunner Support or Firefox GTK.

Maybe I went about it "****-about-face".

All is now happy !

Regards
Mark

---

### Post by mrat on 2007-12-13
Nope... it has gone again. Worked for a short while perfectly, till this moring.

Just after installing XulRunner support the print queue showed Notes docs as htm's, which worked fine (see "working_printqueue.png")

This morning had a look at the "/usr/lib/xulrunner" files and they have found some IBM stuff which may be because I have it in the PATH. (see "xulr_slinks.png")

Maybe narking up the wrong tree.

Regards
Mark

---

### Post by mrat on 2007-12-13
OK, so this is when it works and doesn't...

If there is a MIME message or a document that is HTML based, and is open in its' own tab, then the print dialogue is not the usual Notes one, but eveything prints perfectly.

All other ways of printing the document, like : right-clicking in the view, printing it from the preview plane whether is a HTML/MIME message or not, then presents the proper Notes Print dialogue, which will not print nicely to a physical printer, and does the "champs.pdf" if printed to the Cups PDF.

I have attached the different print dialogues. 1st is the working non-Notes dialogue.

---

### Post by mrat on 2008-01-14
Sorry, been on a pause as I think 8.0.1 (out this month) will be a bit more compatible, as IBM are looking to support Ubuntu... maybe.

Didn't want to waste time with things that are way out of my depth at the present stage.

Regards
Mark

---

### Post by chouf on 2008-01-16
ok, thanks for the follow up.

I do not think I'll be able to get that new version of Lotus Notes for Ubuntu straight away. I'm actually the only one using it on a Linux machine. The rest of my company is with Windows XP and Lotus Notes 6.5.

But OK let's wait and see... if you have the chance to test it out, let me know and I'll bug IT support to get the latest version ;-)

---

### Post by mrat on 2008-01-17
Here and attached is a little hope....

[http://www.rayd.co.uk/blogs/rayblog.nsf/d6plinks/Notes8Ubuntu](http://www.rayd.co.uk/blogs/rayblog.nsf/d6plinks/Notes8Ubuntu)

Had to export the JPG from a ODP file that was too big to upload. Found at a different source than above, but both show an effort.

Regards
Mark

---

