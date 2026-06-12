---
title: "CUPS command line Duplex Multiple Documents"
date: 2015-10-26
forum: General Help
---

### Post by deerewright2 on 2015-10-26
Is there a command line option in CUPS to print two documents on opposite sides of same page.  I have 2 single-page documents that I would like to print to opposite sides of the same page.  I want to be able to do this from the command line, so that I can add it as a CRON job.  If there is not an 'lpr' command option, anyone have a script that might work?

---

### Post by tgalati4 on 2015-10-26
Welcome to the forums.  What printer are you using?  So, I presume that you want landscape mode with two single pages.  First unite the two PDF files into a single, 2-page document using *pdfunite*.  From there:

My HP Officejet 7310 can do it with page settings, which you can save as a custom page layout.  

Try the Print-to-File printer and setup a landscape page, with 2 pages per page, which created this file:  [ATTACH]265175[/ATTACH]

To create a cronjob, make a script which merges your two single pdfs, then print with a fancy *lp* command.  Getting all the options correct will take a few tries.

Otherwise there are several PDF tools in your system and in the repos to create the PDF for simple printing:

```
apropos PDF
apt-cache search PDF
```

Other tools:

[http://community.coherentpdf.com/](http://community.coherentpdf.com/)

Putting it all together:

```
#!/bin/sh
#
# Super cheesy script to print two PDF files onto one page, side by side.
#
# Expecting files named Page1.pdf and Page2.pdf
# 
cd Documents
pdfunite Page1.pdf Page2.pdf side-by-side.pdf
lp -d Officejet_7300 -o landscape -o number-up=2 -P 1-2 side-by-side.pdf
exit 0

```

---

