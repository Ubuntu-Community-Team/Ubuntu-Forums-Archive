---
title: "Username over a networked printer"
date: 2007-09-17
forum: General Help
---

### Post by gib on 2007-09-17
Ok, this is sort of a complicated question and requires some background (even though the answer is probably going to be extremely simple.  I'm new to Linux, so be patient).

The university I'm studying at has a large system of networked printers called ePrint.  Any computer in a computer cluster here can submit files to the user's ePrint queue (after submitting a username), which can then be printed at any of about a million networked printers by swiping our ID cards.

We can also set up our own personal computers to submit to ePrint.  On Windows and Mac this is done through a downloadable client program.  They don't have one available for Linux; however, they do have written instructions on how to set it up.  Basically, you just set up a networked printer, which I've done.  However, you also have to submit your username so it knows which queue to submit to.  On a command line, this is easy -- just add a -U [username] parameter to the print command:

lpr -P ePrint-OIT -U [username] [filename]

For printing files from the hard drive, this works no problem.  However, I can't get it working for printing from a GUI application (e.g Firefox).  The instructions provided say that you can change the print command from within the Printer Properties of the application, but no such field exists.  How do I add that parameter to Firefox's print command?

---

