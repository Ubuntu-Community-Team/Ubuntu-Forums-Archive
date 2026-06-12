---
title: "Canon iP6600D Install Help"
date: 2006-10-23
forum: General Help
---

### Post by undertakingyou on 2006-10-23
I have spent the last several days looking through the forums for answers to what could help me. ](*,) I have a canon iP6600D and have downloaded two files, cnijfilter-ip6600d-2.60-1.i386.rpm and cnijfilter-common-2.60-1.i386.rpm.  I used alien to convert to .deb packages and installed.  Used gnome to install the printer, and then I try a test page.  Nothing happens, CUPS says that it prints, but nothing comes out.  I tried updating CUPS to VER 1.3 from source on the cups website, no change.  It doesn't seem what I do I can't even get a light to flash on the printer.  Any thoughts or help.
Thanks,
Will Smith
Oh, extra info, I am running dapper drake on a i386 machine, and printer is hooked up to a USB port.  Thanks.

---

### Post by Sef on 2006-10-24
On [LinuxQuestions]("https://linuxquestions.org/questions/showthread.php?t=457836") I found this answer to a similar question.

> Unfortunately Canon do not appear to create Linux drivers for that printer. They do for some of their other printers (e.g. Canon PIXMA iP4200D), but not for your model. 

Likely there are no drivers for it.  Even checked [TurboPrint]("http://www.turboprint.de/english.html") and didn't see it listed there either; however, you ask them about it.  There are some free drivers to download, but if you want everything and no turboprint watermark, then you have to pay for it.

---

### Post by undertakingyou on 2006-10-24
I found the drivers in the canon japan site.  And in the gentoo wiki about the pixma printers it says that the driver works for the iP6600D.  Any other thoughts?
Will Smith--

---

### Post by panas on 2006-12-09
It was a reason for me to boot on xp.
Not any more, thanks to [slimdog360]("http://www.ubuntuforums.org/member.php?u=89140")                       discovery.

[http://www.ubuntuforums.org/showthread.php?t=282096&highlight=pixma](http://www.ubuntuforums.org/showthread.php?t=282096&highlight=pixma)

Here is the page with the details
[http://mambo.kuhp.kyoto-u.ac.jp/~takushi/](http://mambo.kuhp.kyoto-u.ac.jp/~takushi/)[LIST]
[*][Canon Pixus/Pixma Printers]("http://mambo.kuhp.kyoto-u.ac.jp/%7Etakushi/#canon")
[*][EPSON Color LASER Printers]("http://mambo.kuhp.kyoto-u.ac.jp/%7Etakushi/#epson")[/LIST]

---

### Post by undertakingyou on 2006-12-10
What did you do to get it to work consistantly.  I can get it to work right off.  And I can always print a test page, but it won't print from openOffice, it will print from the web until I correct the paper size, and then nothing.  And it won't print PDF's that I have saved.  Any thoughts?

---

### Post by patrickfromspain on 2006-12-10
I've never had any luck with canon japan drivers...

---

### Post by panas on 2006-12-12
My fault did not tested with Open office.
It seems that i can print only text documents.

When did a .gif photo print i got only the page filled with black color.
Same result when tried a .pdf file


You have to uninstall any previous driver that 
you installed for the printer.
Because it is working on my new install but not in the old one that 
i had previous installed drivers from canon.jp.

Anyway its better from nothing.

---

### Post by undertakingyou on 2006-12-13
Panas,

What Paper region are you in.  I.E. do you use A4 paper and leave the printer set there?

I am in a US Letter region and use letter paper.  Whenever I tell the printer to use this size paper it will not print.  It doesn't seem to matter what I do, if I change the paper size to Letter it just craps out.

---

### Post by panas on 2006-12-22
i removed the drivers, for the present
i just tried the turbo print deb and even pdf,gif  files is now been printed .

For the present if you can handle the printed logo of the turboprint ...

> Printers Supported by TurboPrint

 Canon PIXMA iP6000D, Canon PIXMA iP6210D, Canon PIXMA iP6220D, Canon PIXMA iP8500

[http://www.turboprint.info/](http://www.turboprint.info/)

Fck canon support.....

---

### Post by undertakingyou on 2007-01-01
Panas, another question.  If TurboPrint doesn't support the IP6600D how did you get it to print?   Did you just use a different driver for the 6600D?  Thanks,

---

### Post by rbmorse on 2007-01-01
The TurboPrint iP6000D or 6220D driver (which ever model is closer to the 6600D paper handling capability) should work.

---

### Post by undertakingyou on 2007-01-01
Thanks for the advise.  I used the ip6000d driver because it has both the same paper capability and it has the same amount and types of ink cartridges.  A strange thing though, it won't print black.  If I print a test page in color it doesn't have any black.  If I try something in B & W it just spits a blank page out.  I'm going to try and email the turboprint people.  Their drive and setup it by far the most impressive.

---

### Post by undertakingyou on 2007-01-30
So, after a much anticipated wait yesterday TurboPrint put out a driver for this printer.  \\:D/   It works perfect.  It is free to use with draft quality printing, and you can use all printing but, they put the TurboPrint Logo in there.  To get rid of that logo it costs 29 Euro.  I don't think that is a bad price at all.  And it supports all of the paper and quality settings that this printer is capable of (not sure about borderless printing, haven't tried that).  So, thanks for all the help and I hope this helps someone else also.

UNDERTAKINGYOU--
------------------------

---

