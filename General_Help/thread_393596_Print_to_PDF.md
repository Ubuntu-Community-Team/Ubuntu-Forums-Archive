---
title: "Print to PDF?"
date: 2007-03-25
forum: General Help
---

### Post by jakev383 on 2007-03-25
I do not currently have a printer setup in Ubuntu. Is there a way to have a "print to PDF" option for things I currently want to print out?
If so, can someone point me in the right direction? I'm runny Edgy.
Thanks in advance.

---

### Post by defishguy on 2007-03-25
Install cups-pdf by using:
> sudo apt-get install cups-pdf

Edit /etc/cups/cupsd.conf and change the line that says:
RunAsUser Yes
to
RunAsUser No

Restart cupsys:
> sudo /etc/init.d/cupsys restart

Add a new printer (System->Administration->Printing) selecting the “Local Printer” “PDF Printer” option. In the next step choose “Generic Printer” and then used the “Postscript Color Printer (Ver 3)” driver.

Now you should be able to print to pdf by selecting the newly setup printer.

Cribs:
1) The output .pdf files are stored in your “Home” directory. I can’t find a way to change this output directory to something of my liking
2) The output files are named with pre-defined names (job_8-untitled_document.pdf is an example). It would have been nice to select a name while printing.
3) One shouldn’t have to edit the cupsd.conf file to enable printing! (I found that I might have to edit the configuration file by visiting the homepage of the package, and trying out what I did). At the very least, the README.Debian file for the package should have informed me of the need to edit the configuration file.

This information came from:
[This Ubuntu Blog]("http://ubuntu.wordpress.com/2006/03/23/print-to-pdf-using-cups-pdf/")

I hope it works!  Good luck!

---

### Post by Takmadeus on 2007-03-25
of course!

not as good as PDF creator but....

[http://www.ubuntuforums.org/showthread.php?t=188860&highlight=cups+pdf](http://www.ubuntuforums.org/showthread.php?t=188860&highlight=cups+pdf)

---

### Post by jakev383 on 2007-03-26
Thanks guys. I installed cups-pdf, and then selected add-printer. Saw the PDF printer as an option in there so I selected it, and told it that it was a Generic Postscript printer. That was all.
It now spits the PDFs out in my home dir, in a folder called PDF.
Appreciate it!

---

### Post by AphisOne on 2007-03-29
To change the settings for the CUPS-PDF output directory:

[INDENT]$sudo edit /etc/cups/cups-pdf.conf[/INDENT]

change the Out line from
[INDENT]Out ${HOME}/PDF[/INDENT]
to a location of your choosing.

Save the file and restart cupsys
[INDENT]$sudo /etc/init.d/cupsys restart[/INDENT]

---

### Post by pkh106 on 2007-05-25
hmm, i type that in and get this:

Warning: unknown mime-type for "cups-pdf.conf" -- using "application/*"
Error: no "edit" mailcap rules found for type "application/*"

Warning: unknown mime-type for "/etc/cups/cups-pdf.conf" -- using "application/*"
Error: no write permission for file "/etc/cups/cups-pdf.conf"

---

### Post by darell_m on 2007-05-28
I tired this and see the pdf printer option and selected then chose for virtual pdf printer and then it wants a driver? I am on Ubuntu FF 7.04. Where am I going wrong?

---

### Post by darell_m on 2007-05-28
> **jakev383 said:**
> Thanks guys. I installed cups-pdf, and then selected add-printer. Saw the PDF printer as an option in there so I selected it, and told it that it was a Generic Postscript printer. That was all.
It now spits the PDFs out in my home dir, in a folder called PDF.
Appreciate it!

Problem - I also installed cups-pdf and did as above and selected virtual printer but then it as forward button I am asked for a driver? And installation all fails. Maybe so obvious I cannot see the problem.

Thanks for any help

---

### Post by darell_m on 2007-05-28
:(> **darell_m said:**
> Problem - I also installed cups-pdf and did as above and selected virtual printer but then it as forward button I am asked for a driver? And installation all fails. Maybe so obvious I cannot see the problem.

Thanks for any help

Sorry - I found my stupid noob error - thanks anyway - all is now good and working.;)

---

### Post by ugm6hr on 2007-06-12
For Xubuntu7.04:

```
sudo apt-get install cups-pdf
```

Then (from Menu):
Applications->Settings->Printing
Click "New Printer"
Printer Name: "PDFPrinter" / Description: "PDF Printer"
Select: Virtual Printer: "cups-pdf:/"
Select: Generic
Models: postscript color printer rev4 / Drivers: cups-pdf/PostscriptColor.ppd
Apply

Then it just works - select CUPS/PDFPrinter in Printer Name when printing.

As stated, the output goes to ~/PDF/ and you have no control over the file name (although Firefox sensibly names it after the Webpage Title).

---

### Post by dustigroove on 2007-06-16
[FONT=Arial][SIZE=2][COLOR=Black]**pkh106**:  Try replacing "edit" in the example with "gedit", that should do the trick.

**AphisOne**: Thanks for that! I have been wanting to change the default output location for some time now.

Cheers

[/COLOR][/SIZE][/FONT]

---

### Post by scohar70 on 2007-06-19
I installed the printer (easy as pie, thanks!), and it works pretty well.

Question:  Is there a way once it's installed to tweak the options to produce lower quality files?

For example, I wanted to create a pdf of multiple jpeg images, so I did something like this:

```

lp -d PDF_Printer scans*.jpeg

```

Which worked fine, but the resulting file is 102 MB.  If I could set the dpi to 72 (which I could do with similar Windows-based PDF utilities in the past), then the file could be as small as 2 MB.  

Does anybody know how to set the PDF printer options?

---

### Post by euler_fan on 2007-06-19
I used:
```
sudo aptitude cups-pdf
```
and then:

System->Administration->Printing->Add Printer, selecting
Generic Postscript Color Printer rev 4

When printing in OOo and FF2 I would go to print and check "Print to File", which let me tell it where to put the output file and what to call it. Didn't need any of this editing config file stuff.

At this point I am going to call it a success and keep testing other apps for compatibility on a time permitting basis.

Good luck to all of you.

---

### Post by Shiva88 on 2007-06-19
> **scohar70 said:**
> I installed the printer (easy as pie, thanks!), and it works pretty well.

Question:  Is there a way once it's installed to tweak the options to produce lower quality files?

For example, I wanted to create a pdf of multiple jpeg images, so I did something like this:

```

lp -d PDF_Printer scans*.jpeg

```

Which worked fine, but the resulting file is 102 MB.  If I could set the dpi to 72 (which I could do with similar Windows-based PDF utilities in the past), then the file could be as small as 2 MB.  

Does anybody know how to set the PDF printer options?


Tried editing the printer preferences from the printer dialogue?  Looks to me like System > Administration > Printing, then right-clicking on the PDF printer and selecting Properties, gives you access to an option to change the DPI.  I haven't tried it because I'm in class, but it looks like it would (might?) work.

---

### Post by tico on 2007-07-13
> **euler_fan said:**
> I used:
```
sudo aptitude cups-pdf
```
and then:

System->Administration->Printing->Add Printer, selecting
Generic Postscript Color Printer rev 4

When printing in OOo and FF2 I would go to print and check "Print to File", which let me tell it where to put the output file and what to call it. Didn't need any of this editing config file stuff.

At this point I am going to call it a success and keep testing other apps for compatibility on a time permitting basis.

Good luck to all of you.

File doesn't open with Adobe Reader.

---

### Post by trak87 on 2007-07-13
Here's another way to convert images to a pdf document:

Convert a bunch of tif files to one pdf document:

```
tiffcp *.tif output.tif
tiff2pdf -j output.tif -o pdfoutput.pdf
```

Another convert from jpg to tif using gif as intermediary:

```
for i in *.jpg; do convert "$i" "$i.gif"; done
for i in *.gif; do convert "$i" "$i.tif"; done
tiffcp *.tif output.tif
tiff2pdf -j output.tif -o pdfoutput.pdf
```

The 'convert' utility is part of the imagemagick package. The tiff conversion utilities come from the libtiff-tools package.

In the second example, the conversion to jpg to gif then to tif is strange, but as I recall I was encountering a bug and that was one way to solve the problem. The gif format has a 256 color limitation, while jpg is millions, but for my purpose this was fine.

---

