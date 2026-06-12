---
title: "Problem with OpenOffice and Printer, Please Help"
date: 2006-12-31
forum: General Help
---

### Post by nexus_2006 on 2006-12-31
I just bought a Canon PIXMA iP6600d printer to use with my Latitude laptop.  After a little bit of searching the web I figured out how to get and install drivers for this printer.  Not too hard, even though it is fairly new.  The printer prints fine with PDF viewer, Image Viewer, prints test pages, CUPS detects it - basically there shouldn't be any problems.

When I try to print a text document with OpenOffice, however, printing is a no-go.  It shows the printer in the print menu and it gives windows that look like it is sending the pages to print, but nothing ever comes out of the printer.  I would appreciate any sort of help anyone can give me, I have serched for this a little bit, but I've got some other things I need to work at the moment.

BTW, just discovered nethack.  Who knew such things could be so much fun?:D

UPDATE:  Just tried it with gedit, prints fine.  This looks more and more like an OpenOffice setting issue, though I still have no idea how to fix it.

---

### Post by puneit on 2007-01-04
I am using Canon Pixma ip1000 and I am facing the same problem. Printing with everything else except Openoffice.
What I am doing to get my work done is I first convert my Oo files into pdf and then print them
](*,) 
Please someone help us....:confused:

Edit: I am using Ubuntu edgy eft

---

### Post by puneit on 2007-01-06
I was searching the Internet for this problem, and it seems that one needs to install a printer in Open office seperately
[Link]("http://www.oooforum.org/forum/viewtopic.phtml?t=37399&highlight=printing")
This guide says to install a printer using ./spadmin
First of all I cannot locate the installation directory of open office nor I can locate this command.
Secondly, I saw /etc/open office contains a file psprint.conf

The part of the file which mentions printer, I am pasting here
```

[Generic Printer]
; for every printer a group with at least the keys
; "Printer" and "Command" is required

; Printer: contains the base name of the PPD and the Printer name separated by /
Printer=SGENPRT/Generic Printer

; DefaultPrinter: marks the default printer
DefaultPrinter=1

; Location: a user readable string that will be shown in the print dialog
Location=

; Comment:  a user readable string that will be shown in the print dialog
Comment=

; Command: a command line that accepts PostScript as standard input (pipe)
; note: a shell will be started for the command
Command=

```
I am using a Canon ip 1000 Pixma printer. Should the printer details show up in the above file.
When I am attempting to  print from Openoffice, I can see in the printer state Stopped: job-stopped

Any workouts

---

### Post by puneit on 2007-01-08
Finally, I got my printer working in Openoffice.
This is what I did. I called a program called spadmin
```
/usr/lib/openoffice/program/spadmin.bin
```
Here I clicked on new printer.
Then it asked me " Do you want to"
[LIST]
[*]Add a printer
[*]Connect a fax device
[*]Connect a PDF converter
[/LIST]
Add a printer was unavailable, so I went on with Connect a fax device. There I selected the option "A specific driver, to adapt the format to another printer" Under that I selected Generic printer and clicked import
It asked for driver location
Canon postcanonbj drivers are located at
```
/usr/share/ppd/pstocanonbj
```
Clicked ok and closed the application spadmin
Then I reinstalled the printer (it may not be necessary, I didn't check the printer before this step)
After re installation, a .doc file was printed successfully.

---

### Post by danforth_toronto on 2007-05-21
Thank you for posting your solution!  It worked for my ip6000D printer that was not printing when using Open Office.  Works fine now!  I did not do a printer reinstall just closed spadmin.

Cheers!

---

