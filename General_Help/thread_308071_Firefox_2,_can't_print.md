---
title: "Firefox 2, can't print"
date: 2006-11-27
forum: General Help
---

### Post by jefrat72 on 2006-11-27
I just set up Firefox 2 on my 6.06 dapper machine, but I can not print. I go to print and my only choice is "PostScript/default". I am trying to print to a networked printer that all my other programs do currently print to.

Any help would be appreciated.

---

### Post by dbott67 on 2006-11-27
What printers appear in SYSTEM > ADMINISTRATION > PRINTING?

How is the network printer attached to the network (HP JetDirect, Windows/SMB share, etc.)?

-Dave

---

### Post by jefrat72 on 2006-11-27
under Sys > Admi > Print shows my HP4050.

HPJetDirect is the connection.

---

### Post by invisibastard on 2006-11-27
I have the same problem, I have an HP PSC1350. I have no problem printing from other programs, firefox only gives me the option of postscript/default. I haven't run into this before, at a loss at how to fix it. 

I'm running 64 bit Edgy. 

thanks,
rich

---

### Post by dbott67 on 2006-11-28
The printer does show up in my version of Firefox.  I'm running Edgy:
```
dbott@edgy:~$ uname -a
Linux edgy 2.6.17-10-386 #2 Fri Oct 13 18:41:40 UTC 2006 i686 GNU/Linux
```

@jefrat72: Are you running 64-bit on Dapper?

Create a PDF printer as per these instructions
[http://www.ubuntuforums.org/showthread.php?t=283198](http://www.ubuntuforums.org/showthread.php?t=283198) and let me know if the new printer shows up in FF.

-Dave

---

### Post by jefrat72 on 2006-11-29
Didn't work.  Thanks though.

---

### Post by jefrat72 on 2006-11-29
Got it.  Open a new window in FF and type  "about:config"

type or copy/paste "print.printer_PostScript/default.print_command" into filter.

Right click on print.printer_PostScript/default.print_command and choose Modify.

type in or copy/paste  "lpr ${MOZ_PRINTER_NAME:+-P"$MOZ_PRINTER_NAME"}"

(minus outside quotes of course)

originally I only had "lpr" in there.  The rest of the code I found in another tread but it must tell firefox to use the computers default printer.

Sweet, thanks all.

---

### Post by dbott67 on 2006-11-29
Good work... glad you got it working.

-Dave

---

