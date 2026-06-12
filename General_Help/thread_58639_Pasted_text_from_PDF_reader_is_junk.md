---
title: "Pasted text from PDF reader is junk"
date: 2005-08-21
forum: General Help
---

### Post by buldir on 2005-08-21
I have tried kprinter -stdin, cups-pdf, and print to postscript then convert using ps2pdf from Firefox. When I open the resulting PDF in any PDF reader, select text in the PDF, then paste it into any other program (including the CLI), the text looks like:



I don't know what's going on. I can see the text in the reader, but when I copy and paste it, I get junk. Any thoughts? Thanks.

---

### Post by buldir on 2005-08-21
OK, something fishy is going on.  In Ubuntu, I printed to postscript using the generic print to file option in Firefox.  I converted it to PDF using ps2pdf13, opened it the PDF in Adobe Reader 7 in both Ubuntu and Windows, and tried to paste text into Gedit and Word Pad...got junk.  So, I fired up Knoppix 3.7, and repeated this process using Mozilla and again ps2pdf.  I opened up the "Knoppix/Mozilla" PDF in Adobe Reader in both Ubuntu and Windows, copied and pasted text into the text editor...and...the flippin' text was readable!  What the helicopter is going on that this process does not work in Ubuntu?

---

### Post by buldir on 2005-08-22
Isn't it great when there's a thread with 3 posts and they're all from the same person.  So, I can repeat the following when using a version of Firefox available in the Ubuntu reps:

1) Printing to postscript in (Ubuntu) Firefox 1.0.6 and converting the .ps to .pdf via kprinter -stdin, cups-pdf, and ps2pdf13 produces a PDF with no text when opened with gpdf, kpdf, or xpdf.  The PDF text can be read in Adobe Reader 7 (Linux and Windows).  The postscript file is readable.

2) Pasted text out of the resultant PDF (when viewing in Adobe Reader 7) is gibberish.

I removed the Ubuntu Firefox version and installed the Firefox-installer 1.0.6 tarball from Mozilla.org.  The problem goes away.  Can anyone else repeat the problem?  Please let me know, so I can post a bug report if need be.  Thanks.

Here's my sources.list:

```
## Uncomment the following two lines to fetch updated software from the network
deb http://us.archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu hoary universe
deb-src http://us.archive.ubuntu.com/ubuntu hoary universe

deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

deb http://security.ubuntu.com/ubuntu hoary-security universe
deb-src http://security.ubuntu.com/ubuntu hoary-security universe

deb http://archive.ubuntu.com/ubuntu hoary multiverse
deb-src http://archive.ubuntu.com/ubuntu hoary multiverse

## Backports
deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted
```

---

