---
title: "italics in pdf format"
date: 2008-05-10
forum: General Help
---

### Post by Wingrave on 2008-05-10
Hey, gang.  I've been using Ubuntu for a little over a year, and this is the first time I've run into this problem.

I just upgraded to Hardy, and now, when I open any PDF document, it shows up on my screen in italics.  This happens with both the default document viewer and with KPDF.  When I print the document, however, the format is normal.

Has anyone else run into this, and if so, how in the world do I fix it?

Thanks.

---

### Post by gradysghost on 2008-08-25
I have come across this myself.  When I open mine, it's all in italics and bold.

For what it's worth, I can render a document to PDF under Ubuntu and it will appear in bold/italics under any OS (I dual-boot with WinXP, and have experimented with Mint and other *nix flavors).  But if I create the PDF in Windows, it'll show up normal in Windows, but still be bold/italics in Ubuntu.  The same holds true if I use an alternate *nix PDF reader.

What's up with this?

Here's something maybe special: I thought this was maybe a problem with some screenwriting software I use called Celtx, so I got with Celtx's support.  The generous aid there told me something odd: all the PDF rendering is done on their end using LATEX and using some HTML markup as the source.  So this must be something funky with evince or who know what else?  I am also baffled by this issue.

---

### Post by gradysghost on 2008-08-26
I just installed the additional package "epdfviewer" and found that PDFs are being rendered in just the same unnatural way under that in lieu of Evince.

---

### Post by gradysghost on 2008-08-29
I downloaded PDFEdit last night, and all PDFs that otherwise have problems show up in PDFEdit flawlessly.  This confuses me even more.

---

### Post by gradysghost on 2008-08-30
Okay, so it all displays correctly in PDFEdit, and so I thought I'd try saving a copy with PDFEdit to see how it displays, but that didn't work either.

I thought that maybe this is a problem with my msttcorefonts package, so I did a complete and full removal and reinstalled it with fresh downloads from the Hardy repository.  This also did not work.

So I took the Courier font (which is the sole font used in this one particular PDF) and embedded it into the PDF, then saved a copy, and it still didn't do anything.  The font might actually be Courier New, but I need to fenagle the app a bit before I'll be allowed to embed it.

---

### Post by gradysghost on 2008-09-22
So I noticed that both Evince and ePDFviewer use poppler for their PDF rendering.  I reinstalled three packages related to poppler:

[LIST]
[*]libpoppler2
[*]libpoppler-glib2
[*]poppler-utils
[/LIST]

This did not solve the problem.  I tried installing a package called *poppler-data* which was not present before like the previous three.  This also does not appear to have solved anything.

I installed two packages:

[LIST]
[*]libpoppler-qt2
[*]libpoppler-qt4-2
[/LIST]

Again, problem not solved.  So I reinstalled Evince with these new packages installed, just in case they needed to reread any behind the scenes apps.  No change again.

My next step in resolving this obnoxious little problem is to try booting to a live CD (a thereby 100% clean "install" of Ubuntu) and try to open the file from the live OS.  I will post back when I've done that.

---

### Post by retrow on 2008-09-22
You can also install Adobe Acrobat reader (acroread). If I encounter display inconsistencies in a PDF document, I usually open that file using Acrobat reader. Opening with LiveCD etc. would help you pin point where the problem lies and aid in improving the upcoming packages.

---

### Post by gradysghost on 2008-09-22
I'm back, and glad to see that somebody other than me responded here.

I tried under two live discs: Ubuntu Hardy x64 and XUbuntu Hardy x86.  The results under each are the same: it's in italics.  I rebooted to my WinXP install (begrudgingly) and copied the file over using Explore2FS, a Windows app that reads EXT3 filesystems, since Windows is too locked down to do this for me, and the file rendered beautifully under Acrobat Reader.  I am about to try your suggestion with the official Adobe Acrobat Reader for Linux.

---

### Post by gradysghost on 2008-09-22
Couldn't find acroread.  The command

```
sudo apt-get install acroread
```

returns this:

```
Reading package lists...
Building dependency tree...
Reading state information...
Package acroread is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
```

However, I installed XPDF

```
sudo apt-get install xpdf
```

And it installed itself, a reader, and some other tools.  When I ran xpdf and fed it my document:

```
xpdf /home/ryan/Desktop/Eminent\ Domain.pdf
```

It rendered beautifully.  Something's going on with the doppler packages.  That would be my guess.  My programming skills are intermediate, not what you would call l33t h@X0rz sk1llz, but my diagnostic skills are active.  Both Evince and ePDFviewer use Poppler as their PDF renderer.  Neither works.  XPDF and PDFEdit apparently do not, and they render perfectly.

Any idea where I can post this information directly to developers of Doppler, Evince, and ePDFviewer so I know the info gets into the right hands?

---

### Post by retrow on 2008-09-22
> sudo apt-get install acroread

This would return an error if you haven't added medibuntu repositories to your sources list.

I assume you are running Hardy - this should give you access to a working acroread under ubuntu.

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
```
```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

And finally -
```
sudo apt-get install acroread
```

---

### Post by gradysghost on 2008-09-22
So, in summary, here's how you solve the problem.

1 - Install xpdf

(From terminal)
```
sudo apt-get install xpdf
```

(From GUI)
Click System -> Administration -> Synaptic Package Manager
Click Edit -> Search (or press Ctrl+F)
Type "xpdf" and press Enter.
Check the box for xpdf and click Apply.

2 - Redirect the default program for PDFs.

Find a PDF file.
Right-click it -> Properties
Go to the Open With tab.
Select XPDF.
Click Close.

Problem solved.

---

### Post by gradysghost on 2008-09-22
Or you can just follow retrow's instructions to install acroread.  I haven't tested that myself.

---

