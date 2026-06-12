---
title: "Setting up Printer for Copy in XSANE on Ubuntu"
date: 2013-06-08
forum: General Help
---

### Post by foberle on 2013-06-08
While I've been scanning successfully using XSane and Simple Scan, when I attempted to use XSane (version 0.998 on 64 bit Ubuntu 12.04 LTS) in Copy mode it told me no printer was defined. I opened the "copy" tab in "xsane setup" and clicked the "Add printer" button, but no dialog appeared.

Apparently, this does not bring up a list of OS printers, as I would have expected, but adds the define an existing CUPS printer with various entries on the dialog box (e.g. "Name," "Command," and so forth). Since it looks like Ubuntu is using CUPS as an intermediary for all printers, I tried using the names I got from the "Printers" dialog from the icon in the upper right corner of the desktop, but none of them seem to be recognized.

Is there a way to use my HP Inkjet printer (which works just fine with Ubuntu) to print out scans directly from XSane? I can, of course, save the scan as a pdf or something and then print it, but it seems like I must be missing something somewhere. If so, how would I go about doing this?

---

### Post by oblong on 2013-08-06
Based on [http://ubuntuforums.org/showthread.php?t=1037201](http://ubuntuforums.org/showthread.php?t=1037201) I was able to figure this out. It's certainly not obvious!

I'm also using  XSane (version 0.998 on 64 bit Ubuntu 12.04 LTS).

I have two printers, one is USB ink jet; the other is network laser. Both use the TurboPrint drivers, but I don't think that matters.

I found the clue is to visit the CUPS page in your browser ([http://localhost:631/](http://localhost:631/) by default). Click the "Administration" tab then "Mange printers" button.
You'll see the left column called "Queue Name". Copy that que name for one of your printers.

In XSane, Preferences|Setup|Copy you'll see it probably has "new printer"in the "Name" field. Paste in your printer queue name to replace "new printer" (although I suspect you can put any meaningful name there).

In the "Command" field, enter:

```
lp -d <queue name>
```

In my case, I have:

```
lp -d iP4850-A4-TurboPrint
```

Click "Apply". That should be it. Repeat for other printers and their queue names. You might need to click "Add printer" to get a new default template.

Note that if you've been clicking "Add printer" often, to add a printer, expecting something meaningful to happen, you'll probaly find you have simply added numerous printers called "new printer". You can check that in the top drop down printer selector. If there are excess printers there, pick one, then click "Delete printer". Repeat for other excess printers.

But I'm new to this, so there may be a better way.

---

### Post by poe503 on 2014-01-14
Worked for me when I unchecked the bottom option (Create zlib..) on the xsane copy setup page.

---

### Post by dallase1 on 2014-01-27
I tried to do this and it did not work this is what I see on the left column called "Queue Name"


[TABLE="class: list"]
[TR]
[TD][HP-LaserJet-200-color-M251nw]("http://localhost:631/printers/HP-LaserJet-200-color-M251nw")[/TD]
[TD]HP LaserJet 200 color M251nw[/TD]
[TD][/TD]
[TD]HP LaserJet 200 color MFP M275 Postscript (recommended)[/TD]
[TD]Idle - "Ready to print."[/TD]
[/TR]
[TR]
[TD][SCX-4623-Series]("http://localhost:631/printers/SCX-4623-Series")[/TD]
[TD]Samsung SCX-4623 Series[/TD]
[TD]taslim-s-Ubuntu[/TD]
[TD]Samsung SCX-4623f, 2.0.0[/TD]
[TD]Idle - "Rendering completed"[/TD]
[/TR]
[/TABLE]

So I click on HP-Laser Jet-200-M251nw and it displays this

[TABLE]
[TR]
[TH]Description:[/TH]
[TD]HP LaserJet 200 color M251nw[/TD]
[/TR]
[TR]
[TH]Location:[/TH]
[TD][/TD]
[/TR]
[TR]
[TH]Driver:[/TH]
[TD]HP LaserJet 200 color MFP M275 Postscript (recommended) (color, 2-sided printing)[/TD]
[/TR]
[TR]
[TH]Connection:[/TH]
[TD]socket://192.168.1.50:9100[/TD]
[/TR]
[TR]
[TH]Defaults:[/TH]
[TD]job-sheets=none, none media=na_letter_8.5x11in sides=one-sided
[/TD]
[/TR]
[/TABLE]
I then copy and pate socket://192.168.1.50:9100 into the command field under Settings Copy in Xsane like this

**lp -d socket://192.168.1.50:9100**

and when I try to Copy something I get a bunch of errors from the program.

Error During Save Broken Pipe

Error During Save Resource temperately unavailable

Error During Save Resource temperately unavailable

Failed to execute command lp -d socket://192.168.1.50:9100

I have Ubuntu Release 12.04 (precise) 64-bit

Kernel Linux 3.2.0-58-generic

GNOME 3.4.2

The version of Xsane I have is 0.998

It copies fine with the default printer which is the Samsung SCX-462 which is the All in One I scan from which is redundent since if I want to make a copy on it I'll just use it's own copy feature instead of going through the extra steps of using Xsane to copy on a machine that already has a stand alone copy feature plus it's a mono printer . I want to use the HP Color Printer to make a color copy of something in  with out having to first scan what I want to copy and then saving it and then loading the file to print it.

---

### Post by RichTheCoder on 2014-02-21
If I read correctly you should use 

```
lp -d [HP-LaserJet-200-color-M251nw]("http://localhost:631/printers/HP-LaserJet-200-color-M251nw")
```

as the command.

I must say, i am no expert . I am trying to do the same with my HP 2600n ;  if I learn more I will update. 

Certainly mine does not support PostScript; don't know about yours.

Mine is working now with my printer queue named "HP-Color-LaserJet-2600n-try5HPLIP"  (I named it after four failed attempts to install). My command is 
```
lp -d HP-Color-LaserJet-2600n-try5HPLIP -t "Copy to HP2600"
```

---

