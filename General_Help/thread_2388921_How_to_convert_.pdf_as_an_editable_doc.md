---
title: "How to convert .pdf as an editable doc ?"
date: 2018-04-09
forum: General Help
---

### Post by satimis on 2018-04-09
Hi all.

Ubuntu 16.04

I have a .pdf file which consists of 4 pages.  I only need converting P3 as an editable document.

I have tried LibreOffice Write.  It only opened P1.

Please help.  Thanks

Regards
satimis

---

### Post by HermanAB on 2018-04-09
All you need to do anything to PDFs:
sudo apt install pdfshuffler xournal gimp

---

### Post by monkeybrain20122 on 2018-04-09
Can you split them up and then convert? You can use pdfchain to split up a pdf, it is in the repo. Also [calibre ]("https://calibre-ebook.com/download")apparently can convert pdf to txt file according two the second answer [here]("https://ask.libreoffice.org/en/question/43733/pdf-import/").

---

### Post by dragonfly41 on 2018-04-09
I would try installing Foxit Reader.

[https://www.linuxbabe.com/desktop-linux/install-foxit-pdf-reader-ubuntu-16-04](https://www.linuxbabe.com/desktop-linux/install-foxit-pdf-reader-ubuntu-16-04)

Or perhaps Okular.

---

### Post by speartip on 2018-04-09
masterpdfeditor might be what you're looking for.
[https://code-industry.net/free-pdf-editor/#get](https://code-industry.net/free-pdf-editor/#get)

---

### Post by satimis on 2018-04-09
> **HermanAB said:**
> All you need to do anything to PDFs:
sudo apt install pdfshuffler xournal gimp
Hi,

Thanks for your advice.

1)
I have PDF-Shuffler installed.  I can open the pdf file on it, splitting into 4 pages.

Right-click P3 -> Export selection

It exports the file as .pdf.  I can't edit it.

2)
Tried Gimp and it treats the document as photo.  What I expect is an editable document.

Please advise.

Thanks

Regards
satimis

---

### Post by satimis on 2018-04-09
> **monkeybrain20122 said:**
> Can you split them up and then convert? You can use pdfchain to split up a pdf, it is in the repo. Also [calibre ]("https://calibre-ebook.com/download")apparently can convert pdf to txt file according two the second answer [here]("https://ask.libreoffice.org/en/question/43733/pdf-import/").
Hi,

Thanks for your advice.

Install calibre and run pdftk to extract P3.

calibre can convert the pdf but the output is in complete mess.  P3 is a statement with 3 columns.  The output .txt file is not in 3 columns, just a collection of words.

Regards
satimis

---

### Post by eldklot on 2018-04-09
This works If you have a Google account: 
Login to Drive
Upload the pdf-file. Mark it, right-click on it, open with --> Google Docs
Edit the file as you wish
When done go to File in menu bar --> Download: choose the format you want ( .docx, .txt, .pdf, etc)

(Edit: provided that it preserves the structure of the original, the 3 columns)

---

### Post by satimis on 2018-04-09
> **eldklot said:**
> This works If you have a Google account: 
Login to Drive
Upload the pdf-file. Mark it, right-click on it, open with --> Google Docs
Edit the file as you wish
When done go to File in menu bar --> Download: choose the format you want ( .docx, .txt, .pdf, etc)

(Edit: provided that it will preserve the structure of the original, the 3 columns)
Hi,

Thanks for your advice.

I only have a gmail account.

What expect to do is as follow:
It is a credit card statement.  I need to check the items charged against the slips received on shopping.  If it is correct I just strike out the item charged.

Actually I don't need the file.  If it is a hard copy then it makes my life easier.

Regards
satimis

---

### Post by eldklot on 2018-04-09
I am sorry, I should have written Gmail-account. If you want to give it a try, just go to [https://www.google.com/drive/](https://www.google.com/drive/) and login with your credentials. It just might do what you want. Just hoping that it preserves the 3-column structure.

greetings

---

### Post by monkeybrain20122 on 2018-04-09
This may be overkill  [https://www.r-bloggers.com/extracting-pdf-text-with-r-and-creating-tidy-data/](https://www.r-bloggers.com/extracting-pdf-text-with-r-and-creating-tidy-data/)

---

### Post by monkeybrain20122 on 2018-04-09
> **satimis said:**
> Hi,

Thanks for your advice.

1)
I have PDF-Shuffler installed.  I can open the pdf file on it, splitting into 4 pages.

Right-click P3 -> Export selection

It exports the file as .pdf.  I can't edit it.

2)
Tried Gimp and it treats the document as photo.  What I expect is an editable document.

Please advise.

Thanks

Regards
satimis

He also mentioned xournal, did you try that?

---

### Post by yancek on 2018-04-09
[QUOTEI have tried LibreOffice Write.  It only opened P1.][/QUOTE]

In LIbre Office Writer, you should see all the pages of any document in the left pane.  If it isn't there, click the View tab and click on Page Pane and pages should show.  Just click in the left pane for the page you want to view/modify.  I think Master PDF Editor would work just fine.

---

### Post by satimis on 2018-04-10
> **eldklot said:**
> I am sorry, I should have written Gmail-account. If you want to give it a try, just go to [https://www.google.com/drive/](https://www.google.com/drive/) and login with your credentials. It just might do what you want. Just hoping that it preserves the 3-column structure.

greetings
Hi eldklot,

Your advice works for my purpose.

Login in Gmail account
Upload the file (in this case only P3 of the .pdf)
Open the file - right-click and select "DocHup - View Edit & Sign PDFs"
Using "pen" tool on top menu I can mark items which have been checked and found correct.
Done

After checking completed I won't save the file but pay the bill thereafter

Thanks

satimis

---

### Post by satimis on 2018-04-10
Hi all,

Lot of thanks for your advices.

eldklot's advice serves my purpose.  Please read posting #14, my reply to eldklot

Regards
satimis

---

### Post by monkeybrain20122 on 2018-04-10
> **satimis said:**
> Hi eldklot,

Upload the file (in this case only P3 of the .pdf)
Open the file - right-click and select "DocHup - View Edit & Sign PDFs"

After checking completed I won't save the file but pay the bill thereafter


I checkout the [video]("https://dochub.com/pdf-editor"), looks like something you could have done for free with[ xournal]("https://www.youtube.com/watch?v=tncWv1BRfxY") as per HermanAB's post #2.

---

### Post by eldklot on 2018-04-10
Hi satimis,
Reading your post and monkeybrain20122's reply, I am a bit confused about if you had to pay for the conversion of your file. If so, it was not my intention to refer you to a site which charges you for that kind of service. Once in Drive, I don't know if you tried to open the pdf-file in Google Docs as written in my post. That would create an editable text-file from a pdf. For curiosity, I checked DocHub. They seem to have a free-of-charge service as well but for a limited number of files.

greetings
eldklot

---

### Post by satimis on 2018-04-10
> **eldklot said:**
> Hi satimis,
Reading your post, I was a bit confused about if you had to pay for the conversion of your file. If so, it was not my intention to refer you to a site which charges you for that kind of service. Once in Drive, I don't know if you tried to open the pdf-file in Google Docs as written in my post. That would create a editable text-file from a pdf.

greetings
eldklot
Hi,

I only need an editable doc of the monthly e-statement of credit card for checking the items billed against the receipts on shopping.  I need to mark the items found correct.  

If the statement is a hard copy I just mark the items checked with pen.

After checking completed I pay the bill of the e-statement, not conversion service.  Besides I don't need its file thereafter.

Regards
satimis

---

### Post by eldklot on 2018-04-10
Alright, good to hear that you didn't have to pay for the conversion. I got the impression from reading monkeybrain20122's post.

cheers
eldklot

---

### Post by mooremag on 2018-04-27
Hi Satimis,
give this tool a try, it should help [https://www.sodapdf.com/pdf-editor/](https://www.sodapdf.com/pdf-editor/)

---

### Post by satimis on 2018-04-28
> **mooremag said:**
> Hi Satimis,
give this tool a try, it should help [https://www.sodapdf.com/pdf-editor/](https://www.sodapdf.com/pdf-editor/)
Hi,

Thanks for your link.

I found another easy way for my use.

1) Start GIMP
2) Import .pdf file
3) Select -> Tools -> pen
4) Paint the item checked

That is all, not necessary to convert the .pdf file

Regards
satimis

---

