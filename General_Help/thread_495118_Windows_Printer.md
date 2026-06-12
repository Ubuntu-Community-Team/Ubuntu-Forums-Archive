---
title: "Windows Printer"
date: 2007-07-07
forum: General Help
---

### Post by posterberg on 2007-07-07
I have one of those fancy Windows (tm) only pritners. This one happens to be a OKI C5100n.

Anyway seems completely impossible to get this one working directly from Linux so I was thinking of printing via a Windows share. That didn't help me much since I am asked for a .ppd-file anyway.

But... Wouldn't it be possible to have some daemon sitting on the Windows machine. One that could pick up a Postscript document from a Postscript printer in Linux. Then have that daemon parsing the postscript document and redirect it thru the windows printer driver?

I think that would work just great... Next problem is... Do you guys know if anyone have created such a setup before? Is there something available or do I need to create such a solution myself? ;o)

/p

:popcorn:

---

### Post by geraldm on 2007-07-07
winprinters are usable in Linux.  
espgs package provides a gdi device for such printers.
The postscript file is run through espgs ghostscript by a bash script.

The command:
printgdi letter.ps

the file printgdi:
#!/bin/bash
gs -q -dBATCH -dPARANOIDSAFER -dQUIET -dNOPAUSE \
  -sDEVICE=gdi  -sOutputFile=/dev/usb/lp0   $1

The parameter "letter.ps" becomes the value $1 above.
The winprinter, a Samsung, is on /dev/usb/lp0.
If you do not use cups, you will not need the .ppd file.  
There is an abundance of information on printing in linux.

Gerald

---

### Post by HermanAB on 2007-07-08
Well, here is a Rube Goldberg method, which I don't think anyone has thought of yet: Install Qemu or VMware with WindozeME, install the printer, enable printer and file sharing, then print from the Ubuntu host to the virtual Windows machine and its printer.

La Voila!

---

### Post by posterberg on 2007-07-09
Sweet... Thanks for your replys guys!!

I'll go for the espgs solution since I don't want to waste system resources on having a WinME image running just for printing... But I see that would work as well... =) Creative I must say...

---

### Post by DrMega on 2007-07-09
I have the same problem. I have a piece of crap Lexmark that I was more or less conned into buying under the lies that it was a good quality printer (it is shockingly bad in Windows even).

In Linux, it doesn't work at all (no fault of Linux of course).

Here's an idea I haven't tried yet. The reason I haven't bothered yet is, to be honest, because I can't be bothered to search for the stup disk. Does anyone think this will work: If I run the standard install via WINE, run the little print manager that comes with it, also through WINE, print to a PDF/PostScript file, and have some process shovel those files to the WINE'd print manager?

---

### Post by arrrghhh on 2007-08-30
posterberg, i have this same printer at my work (oki c5100) and i can't get it to work in linux.  i see on openprinters.org it's listed as "paperweight"

so my question to you is did you get the printer working in linux?  if so, can you tell me your secret?

---

### Post by Missle Launch on 2007-10-10
> **geraldm said:**
> winprinters are usable in Linux.  
espgs package provides a gdi device for such printers.
The postscript file is run through espgs ghostscript by a bash script.

The command:
**printgdi letter.ps**

the file printgdi:
[B]#!/bin/bash
gs -q -dBATCH -dPARANOIDSAFER -dQUIET -dNOPAUSE \
  -sDEVICE=gdi  -sOutputFile=/dev/usb/lp0   $1[/B]

The parameter "letter.ps" becomes the value $1 above.
The winprinter, a Samsung, is on /dev/usb/lp0.
If you do not use cups, you will not need the .ppd file.  
There is an abundance of information on printing in linux.

Gerald

:confused:

I'm a beginner, so I need this clarified; I run the commands you've specified that I've boldened, and then the printer will operate normally?

---

### Post by evilpenguin on 2007-11-02
This espgs method is new to me. To date, I have used the information here:

[http://geekinfo.net/article.php?story=20030209135156781](http://geekinfo.net/article.php?story=20030209135156781)

To use a Windows box to "print for me." I just use a generic Poscript PPD file as a driver in CUPS. This espgs GDI method looks like it should work, though. If you are a complete newbie, I'll take a stab at elaborating on what is being said here.

First off, it assumes that what you want to print has been saved as a Postscript file.
Ubuntu automatically provides a "printer" called "Postscript" that, when you print to it, will write the output as a Postscript file.

He is then suggesting that you put those three last bolded lines in a file you will name "printgdi" (It's a shell script) which you will make executable ("sudo chmod +x printgdi") and which you will put somewhere on your executable path.

You would have to change the "-s" argument to name the device file on which your printer is actually attached. My oki c5100 is on the network right now. If you connect it with a USB cable, though, this method should work for you. You'll have to get the /dev name right for your printer. If the oki is the only attached printer, this is probably right as-is.

Now that I know this exists, it should probably be not too much more work to integrate this into CUPS so you can "print directly." But this two step method should work if you don't mind taking the two steps!

---

### Post by arrrghhh on 2007-11-02
hrm... i'm still lost.  the oki c5100 is on a network as well... it's a work printer, so hooking it up to just my computer is out of the question.  strangely the new gutsy printer detection detected the networked c5100 right away... but when it went to print to it the printer just had an error "invalid data" - and nothing would actually print.

---

### Post by evilpenguin on 2007-11-08
You don't have to hook the printer to your machine.

The method that worked for me was to use "redmon" and "ghostscript" installed on a Windows box.

Basically what you do is find a Windows box, any Windows box, that can print to the printer. Then you set up a "fake" Postscript printer on that Windows box that uses "redmon" to grab the output from the fake printer and redirect it to ghostscript, configured to render the Postscript and print it to the "real" c5100 printer on the same box. Then you make the "fake" postscript printer available as a network share. You then print to the "fake" shared printer on that Windows box and it comes out on the c5100.

It works, but man, is it a pain in the backside.

---

### Post by arrrghhh on 2007-11-08
yea that sounds like way more trouble than it's worth.  i'll look into it, but i don't really want to setup a shared printer - the damned thing is already on the network!  at any rate, i have a vm for windows xp always running, so i just print thru that.  maybe i could setup something with that virtual machine?

i'll look into it.

---

### Post by posterberg on 2007-12-13
> **evilpenguin said:**
> You don't have to hook the printer to your machine.

The method that worked for me was to use "redmon" and "ghostscript" installed on a Windows box.

Basically what you do is find a Windows box, any Windows box, that can print to the printer. Then you set up a "fake" Postscript printer on that Windows box that uses "redmon" to grab the output from the fake printer and redirect it to ghostscript, configured to render the Postscript and print it to the "real" c5100 printer on the same box. Then you make the "fake" postscript printer available as a network share. You then print to the "fake" shared printer on that Windows box and it comes out on the c5100.

It works, but man, is it a pain in the backside.

This is the type of solution I was looking for from the start I just didn't find out a working way. Your solution sounds like something that would work. Need to set that up, thanks a lot!!
:guitar:

---

### Post by arrrghhh on 2007-12-13
i have a virtual machine that's running winXP and that is what i use to print.  i'm assuming that this'll work, but i have no idea how to setup a postscript on a windows box, or 'redmon' to grab output, etc.  i'll try to muttle thru it when i get back to work, but a better description of exactly what needs to be done would be appreciated.

thanks!

---

### Post by posterberg on 2007-12-14
I'll get back with that when I got it working myself. I won't have any time to play around with it this week though...

---

