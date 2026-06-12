---
title: "What software can edit PDF files?"
date: 2006-10-21
forum: General Help
---

### Post by brynjarh on 2006-10-21
I'm looking for software that can edit pdf files.

It would be nice if it where open source, GNOME, but it doesn't have to be nice..

help?

---

### Post by Rydel on 2006-10-21
PDF is a format intended for sharing documents, not for editing. As such, only minor changes can be made and require specific software. I do not know of an open source application that can do this, sorry.

---

### Post by cmost on 2006-10-21
A lot of people seemed confused by what a PDF document is and how it can be manipulated.  (You'd be surprised at the number of times someone calls me to ask how they can convert a PDF document to an Excel worksheet or other editable form.)  A PDF is essentially a photograph of a document; sort of like a digital Zerox.  The words you see are not words to the program, but rather merely part of one big image.  Commercial software is available that can scan a PDF image and recognize words and phrases and subsequently convert the PDF to an editable Rich Text Format (RTF) which can be edited in Word or OpenOffice.org Writer.  This type of software runs between $30.00 to $100.00 depending on features and accuracy of conversion.  More advanced software can do the same to create spreadsheets and other more complicated but editable documents; for a price of more than $200.00.  Basically i'm talking about character recognition software.  Unfortunately, Linux lacks good support for such software and therefore you'll have a hard time converting your PDF's into editable versions on the Linux platform.  There is a relatively inexpensive, but pretty good Windows app called PDF2Word that you could try.  You can find it here:

[http://www.verypdf.com/pdf2word/index.html](http://www.verypdf.com/pdf2word/index.html)

Good luck!

---

### Post by galamud on 2006-10-21
> **cmost said:**
> The words you see are not words to the program, but rather merely part of one big image.

This isn't necessarily true.  Some PDF files are simply images of text, but most contain the text as text.

There are many ways you can edit PDF files.  If you're looking to fill out forms, there's a package in synaptic called "pdftk" that claims to be able to.  If you want to get the text out of a PDF and into a readable format, you could either try a package such as "pdftohtml" and then read the html, or open up the pdf in a text editor and copy/paste the text from it.

Searching synaptic for "pdf" gives lots of pdf-manipulation tools.

---

### Post by Bloch on 2006-10-21
There are commercial programs out there that will do a good job of re-creating a word document out of a pdf. All the ones I know combine OCR (opical character recognition) capability with the (more simple) ability to extract any embedded text.

I don't know of any without OCR  which will extract embedded text and preserve the format and fonts. 

But there are plenty which will just extract plain text. In fact on the Adobe website there is an email address to which you can send your pdf file and the text will be extracted.

ABBYY FineReader runs well under wine and I use it professionally for re-creating pdfs, both ones with embedded text and ones with text stored as image.

---

### Post by patrickthebold on 2006-10-21
Not sure how much editing you have to do, but the GIMP can open PDF files and at that point you can technically do anything, its just kinda a pain.

---

### Post by aysiu on 2006-10-21
KWord can edit PDFs.

---

### Post by maniacmusician on 2006-10-21
but not very reliably. especially when there are lots of images and styling mixed in with the text.

but it is definitely the most advanced thing we have right now. koffice rocks.

---

### Post by earobinson on 2007-05-24
[http://www.getdeb.net/release.php?id=730](http://www.getdeb.net/release.php?id=730)

---

### Post by john_spiral on 2007-08-12
I've just spent the last 3 hours trying to edit a PDF under Ubuntu.

my findings:

kword - bad
scribus - bad

PDFedit 0.3.1 - lovely !!!!!!

Download the rpm file from [sourceforge.net]("http://sourceforge.net/projects/pdfedit/") then use alien (use synaptic to install it) to convert the beast into a deb.

[B][SIZE="3"]sudo alien pdfedit-0.3.1-1.i386.rpm 
sudo dpkg -i pdfedit_0.3.1-2_i386.deb [/SIZE][/B]

I think it's always risky to download a deb from an arbitrary site on the net.

happy pdfing!

John

---

### Post by john_spiral on 2007-08-12
"PDFedit 0.3.1 - lovely !!!!!!"

I must have been on drugs!

I've been trying to insert some text on a pdf for the last hour without any success. 

It's beginning to feel like opening a letter with a fork.

If you need to edit a pdf on Linux use Windows or MacOS!

harsh but true!

---

### Post by john_spiral on 2007-08-12
In all fairness Acrobat 8 on Windows is better but still a pain in the ***.

If you have a single pdf you need to fill out, print it off and use a pen.

---

### Post by SabrinalovesUbun2 on 2007-09-27
> **john_spiral said:**
> I've just spent the last 3 hours trying to edit a PDF under Ubuntu.

my findings:

kword - bad
scribus - bad

PDFedit 0.3.1 - lovely !!!!!!

Download the rpm file from [sourceforge.net]("http://sourceforge.net/projects/pdfedit/") then use alien (use synaptic to install it) to convert the beast into a deb.

[B][SIZE="3"]sudo alien pdfedit-0.3.1-1.i386.rpm 
sudo dpkg -i pdfedit_0.3.1-2_i386.deb [/SIZE][/B]

I think it's always risky to download a deb from an arbitrary site on the net.

happy pdfing!

John

Sorry which package am i supposed to download? the .exe one?

---

### Post by jshurst on 2007-09-27
Check this out.  Just download and double click.

[http://www.howtoforge.com/editing_pdf_files_pdfedit_ubuntu_feisty](http://www.howtoforge.com/editing_pdf_files_pdfedit_ubuntu_feisty)

---

### Post by CoolRat33 on 2008-04-12
HI
I also searched for a long time to find a good PDF editor for Linux. PDFedit seems to be developing nicely, but it was just not easy enough to use for my purposes. I needed a tool that would allow me to add highlighting and notes to PDF documents as I read them AND be able to search for words within the document.

Finally after months of trying different things, I found Qoppa Software's PDF Editor. Its not free, but until an Open Source alternative is available, maybe many of us will find this program useful

Qoppa PDF Editor offers a lot of features including:
- add highlighting,
- add comments,
- crossout-text,
- extract text embedded in the file,
- scan to PDF (can scan and insert directly into a PDF document),
- modify pages,
- add or remove pages from a document,
- add hyperlinks
- and other etc. etc. features

I tested it in my Ubuntu 7.10 and found all its features to be fully compatable with Adobe Acrobat -- when I created highligting or notes in Qoppa PDF Editor and then opened it inside Adobe Acrobat 7, all of the highlighting and notes were intact! Great! Perhaps more researchers and students can switch to Linux now that a good PDF tool that allows highlighting and comments is available!

Check out Qoppa Software at [http://www.qoppa.com/psindex.html](http://www.qoppa.com/psindex.html)

---

### Post by Dhammikae on 2008-05-26
I have been looking for a tool to edit pdf files for a long time and found partial solution. It is called PDF-XChange Viewer and they say it is free and it can do most what CoolRat wanted. It runs on Windows but works identical on Ubuntu as well (Hardy)under Wine. 
Make sure you copy your Windows fonts to .wine/c_drive/windows/fonts folder as in Windows.

Hope I helped some one.

---

### Post by Dhammikae on 2008-05-26
Forgt one more thing about PDF-XChange Viewer. I used the portable single .exe download of the free viewer.

You can download it at 
[http://www.docu-track.com/home/prod_user/PDF-XChange_Tools/pdfx_viewer](http://www.docu-track.com/home/prod_user/PDF-XChange_Tools/pdfx_viewer)

---

### Post by edc80 on 2008-05-29
If you're trying to open a PDF file to "fill out" a form... try opening it in Gimp (specify which pages or you'll get a whole lot of windows!).  Then, save each page as a jpg file, and use pdftk to re-assemble them into a new pdf.

---

