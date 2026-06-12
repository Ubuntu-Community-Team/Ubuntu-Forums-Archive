---
title: "PDF printing in Firefox"
date: 2005-10-02
forum: General Help
---

### Post by oakman on 2005-10-02
Hi
I have some problems printing pdf files in Firefox and I have searched the forums but that didn't make me any wiser so here I am. 
I have installed cups-pdf and followed the instructions on [https://wiki.ubuntu.com/forum/software/cups-pdf](https://wiki.ubuntu.com/forum/software/cups-pdf). However, when it comes to create the pdf printer something funny happens (IMO).
I go to System > Administration > Printing. I double-click the "New Printer" button and select "Use a detected printer". I highlight "PDF Printer" and hit Forward. Now to the funny part. The setup asks me to select a manufacturer and model!? Why? Should I just select any of them or what? I did try that but with no luck in Firefox.
I have also tried "Use another printer by specifying a port" and selecting "Virtual Printer (PDF Printer)". This option also asks for manufacturer and model in the next step and again, no luck in Firefox.
Guessing I'm just tired and stupid but would appreciate some help.
Anyone?

---

### Post by oakman on 2005-10-05
Please, please, please :(. Somebody has got to know. I have also tried RAW and Generic printers but none of them works.

---

### Post by mlmurray on 2005-10-05
Okay.  This isn't exactly what you are asking for, but this is a way to create PDF files in Firefox.
You see, all a PDF really is is a compressed Postscript file and Firefox can create postscript files easily - just select Print to:  File instead of Printer when the print dialog comes up.  This will then enable a field a little lower in the dialog box where you can give your file a name and a path to save it.  
Now just go to the command line and enter `ps2pdf *yourfile.ps*` and viola!  You've got a nice pdf file.
More to your question regarding the pdf printer setup:  You can probably select any printer that is a *Postscript* printer.
Good Luck!

---

### Post by pataphysician on 2005-10-05
that's never worked for me. i get images/colors but no text [EDIT, i had that backwards initially]. i've searched about the forums myself and the consenus, at least back when i was looking into it, was that firefox's .ps output is fubar'd and that consequently it was impossible to print to a pdf from firefox under ubuntu. maybe things are different now or i missed something. are you able to produce working .ps files from firefox? and if so, how did you set that up?

---

### Post by mlmurray on 2005-10-05
Well, I don't know what to tell you.  [Here's]("http://home.comcast.net/~69murray/mozilla.pdf") a pdf I created using the method I described above and it worked fine for me.  I'm able to display it just fine using KGhostview. (It's blue due to my trying out the new "Kubuntu blue" theme - selectable at the bottom of the page).

Note that KPDF munges it completely - It shows the graphics (sort of), but no text.  A better test would be to see if acrobat can display it properly (I don't have that installed).

Maybe your choice of viewer is part of the problem?

---

### Post by pataphysician on 2005-10-05
[QUOTE=mlmurray]Maybe your choice of viewer is part of the problem?[/QUOTE]

ah, that seems to be that case. i'm using evince and am unable to view the file you've linked to. here it looks like the other files i've created: colored blocks, no text. i'll try out some different pdf readers.

---

### Post by twowheeler on 2005-10-05
Sorry to butt in here, but that file looks the same in xpdf and gpdf under gnome: colored blocks, some graphical icons, and zero text.  However in ggv it appears correctly with the text shown.  So the common factor seems to be that the pdf readers can't read it, but the ghostscript-derived .ps tools can.

---

### Post by pataphysician on 2005-10-05
[QUOTE=twowheeler]Sorry to butt in here, but that file looks the same in xpdf and gpdf under gnome: colored blocks, some graphical icons, and zero text.  However in ggv it appears correctly with the text shown.  So the common factor seems to be that the pdf readers can't read it, but the ghostscript-derived .ps tools can.[/QUOTE]

that's pretty much what i'm getting, too. pdf readers don't work with the files, but post script/ghost script applications are ok. this article:

[https://wiki.ubuntu.com/forum/software/cups-pdf](https://wiki.ubuntu.com/forum/software/cups-pdf)

and the threads it links too seem to indicate that there is a problem with ps2pdf and firefox. maybe that will also help with the OP's question.

---

### Post by oakman on 2005-10-06
Thanks for the replies. I tried the ps2pdf method which produced a pdf file with graphics but no text. This seems to be a xpdf problem cause the text showed up just fine after installing Acrobat Reader. It also shows up fine when viewed on a Windows machine (using Acrobat Reader).

I guess I will have to settle with this for now. It would be nice to get rid of that ps2pdf step though. Can't anyone of you programming nerds make an extension for Firefox that handles this ;).

Over and out.

---

