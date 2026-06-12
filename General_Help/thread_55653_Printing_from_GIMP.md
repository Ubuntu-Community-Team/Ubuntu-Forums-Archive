---
title: "Printing from GIMP"
date: 2005-08-09
forum: General Help
---

### Post by Irony on 2005-08-09
I've installed the printer driver for my HP deskjet 720c and it prints fine from openoffice.

However when I use GIMP and go to print it goes through to an export screen and then to a print button. The printer icon appears next to the clock but nothing happens. If I click on the printer icon it says it is printing but it isn't, I can select a test print which works.

How do I get a picture to actually print from GIMP?

---

### Post by coolclassic on 2005-08-09
If you are trying to print a large file it will take a while to print. How long are you giving it before you start printing. Maybe try a small file and see if this prints.

---

### Post by Irony on 2005-08-10
Good point. I'll give it a go.

---

### Post by jeremy on 2005-08-10
have you set up your printer in Gimp (you obviously have in ubuntu, but you have to do so seperately in Gimp), when you click 'print' you should get a dialogue with a 'printer settings' tab; chose your printer from the drop down list.

---

### Post by matthew on 2005-08-10
Thanks to OP for the question. I've had the same problem, but haven't had time to play around and find a solution so I didn't ask yet. I have printed pictures using other programs so it wasn't an issue yet.

Thanks to jeremy for the tip...I'll try that when I am home at my computer.

---

### Post by Irony on 2005-08-11
I think jeremy maybe right as I haven't set up the printer for gimp - I looked at the settings and they looked right so I didn't do anything but maybe I have to okay them.

Interestingly gimp prints straightaway in windows but doesn't have a print preview option like in ubuntu, I don't think a print preview plugin is available in windows.

---

### Post by matthew on 2005-08-11
Hmm... I apparrently tried to do this previously and forgot as the printer was already entered. However, my specific printer model (HP PSC-1210) is not in the drop down list and Gimp is trying to use the generic "Postscript printer" which didn't work. I'm going to do some fooling around and see if I can get it to use the hp driver I installed that gave me global printing available in Gnome and KDE-specific programs. More to come if successful...

---

### Post by matthew on 2005-08-11
Well, I read through and tried everything I could think of related to these pages...

[http://linux.seindal.dk/item33.html](http://linux.seindal.dk/item33.html)
[http://www.linuxprinting.org/ppd-doc.html](http://www.linuxprinting.org/ppd-doc.html)
[http://linuxprinting.org/show_printer.cgi?recnum=HP-PSC_1210](http://linuxprinting.org/show_printer.cgi?recnum=HP-PSC_1210)
[http://linuxprinting.org/show_driver.cgi?driver=hpijs&fromprinter=HP-PSC_1210](http://linuxprinting.org/show_driver.cgi?driver=hpijs&fromprinter=HP-PSC_1210)

I must be missing something simple, but I just can't see it. I've put a copy of the appropriate ppd file in my home directory and told Gimp where to find it in printer setup. I read the man pages for the ls and gs commands and tried fiddling with the settings to no avail.

Quoting from the first web page listed above:
> Gimp-Print generates all the necessary printer instructions directely, instead of just sending a PostScript file to the print spooler and filters.

It does annoy me a bit that I cannot get Gimp-Print to print photos simply by pointing it to a PPD file, but at least now the photos are printing and my WAF is, if not increasing, at least in a slower decline.  

That would seem to explain why I can print in EVERYTHING else except Gimp. Now to discover how to get Gimp set up the same as other stuff.

---

### Post by matthew on 2005-08-11
Okay. I got it working. Here's what I did. 

1. In Gimp I selected Print->Printer Settings->Setup Printer

2. In the dialog box that came up I did the following:
a. As my printer model was not listed I selected "Postscript Level 2"
b. I modified the command by removing the "-oraw" option even though the program warns not to by saying "printing will probably fail."
c. I found the PPD file for my printer by going to the Gnome taskbar and selecting Places->Search For Files and entering "hpjis.ppd" This returned a long list of PPD files that were archived as .gz files. I looked for the one matching my printer, found it and unarchived it into my /home directory. Then I put the file's name/location into the PPD File spot in the dialog.

3. Hit "OK" and test. If it works, do it again and hit "save on the Printer Settings dialog. If it doesn't work, your setup will will automatically return to however it was before you tried this because you didn't save it yet.

This page gave me the final clue I needed:
[http://sourceforge.net/mailarchive/forum.php?thread_id=3381269&forum_id=6142](http://sourceforge.net/mailarchive/forum.php?thread_id=3381269&forum_id=6142)

Hope that helps somebody. By the way, th most helpful thing I did in looking for the solution was to search for "printing gimp psc 1210" in Google. If you are having trouble try the same thing using your printer's name.

---

### Post by matthew on 2005-08-11
Okay. I got it working. Here's what I did. 

1. In Gimp I selected Print->Printer Settings->Setup Printer

2. In the dialog box that came up I did the following:
a. As my printer model was not listed I selected "Postscript Level 2"
b. I modified the command by removing the "-oraw" option even though the program warns not to by saying "printing will probably fail."
c. I found the PPD file for my printer by going to the Gnome taskbar and selecting Places->Search For Files and entering "ppd" and telling it to Search In Folder: "Filesystem." This returned a long list of PPD files and I looked for the one matching my printer, found it put the file's name/location into the PPD File spot in the dialog. In my case it was in /etc/cups/ppd

3. Hit "OK" and test. If it works, do it again and hit "save on the Printer Settings dialog. If it doesn't work, your setup will will automatically return to however it was before you tried this because you didn't save it yet.

This page gave me the final clue I needed:
[http://sourceforge.net/mailarchive/forum.php?thread_id=3381269&forum_id=6142](http://sourceforge.net/mailarchive/forum.php?thread_id=3381269&forum_id=6142)

Hope that helps somebody. By the way, the most helpful thing I did in looking for the solution was to search for "printing gimp psc 1210" in Google. If you are having trouble try the same thing using your printer's name.

---

### Post by Zhukov on 2005-09-11
Man, you saved my day :D
Thanks a lot
This should go sticky

---

### Post by bernardfrancois on 2005-12-14
None of it helped me, though I also have a PSC1210 (actually a PSC1215, but it is well supported by the 1210 driver). I just solved it by printing to a postscript file, and then printing the postscript file afterwards.

Maybe something's wrong with the print command I entered in the Gimp. I don't know what's the original anymore, but I replaced it by 'lpr' (without any options). Now it prints in rasterized black&white.

Which print command are you guys using?

---

### Post by Suzan on 2005-12-14
I've got a HP 1410 an my print command in GIMP is


> lp -s -dHP-PSC-1400

---

### Post by stream303 on 2006-11-07
Oh man you made my day!  I had some wedding prints to do on my new Edgy install and was trying to use a "compatible" driver.  The results were awful.

After following your directions, I now have some great prints.

Initially I went brain-dead and forgot that the Postscript Level2 is in the ADOBE drop down. :)

Thanks again - this was the last nail I needed to go 100% Ubuntu!

---

### Post by diego1188 on 2008-07-17
Thank you very much! Three years later, still a very useful thread! \\:D/

---

