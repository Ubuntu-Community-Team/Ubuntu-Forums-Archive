---
title: "[SOLVED] Dosemu, HP LJ5 printing, russian charset (cp866) problem"
date: 2007-10-19
forum: General Help
---

### Post by Voland on 2007-10-19
I've googled nearly all russian forums, but nothing solved. Here is my trouble:
I have got an old MS-DOS application called MARC (library catalogue program). I need to print book cards (ISBN and so on) on HP LJ 5l connected via LPT. The problem is: this God damn printer haven't got any DOS cyrillic fonts. I've tried HP's native [utility]("ftp://admin.tomsk.ru/drivers/printer/hp/lj/5l/dos"), but nothig happened. I've uncommented printer section in /etc/dosemu/dosemu.conf, but this tool wrote to me "Unable to open LPT1". How can I config this utility to download cyrillic fonts to printer?

---

### Post by emendelson on 2007-10-20
OK, this is a general DOS/LaserJet problem, not a DOSEMU problem, but here goes.

I doubt anyone here has ever used MARC. You might ask on this forum:

[http://www.loc.gov/marc/marcginf.html#marcforum](http://www.loc.gov/marc/marcginf.html#marcforum)

Also, you may be able to find Linux-based solutions so that you don't have to use DOSEMU.

With the LaserJet that you have, you will certainly need either Cyrillic soft fonts or add-in hardware (a SIMM) that adds Cyrillic fonts to the Latin-alphabet ones in the printer.

---

### Post by Voland on 2007-10-22
**emendelson**, thank you for your reply. The problem is that I have got Cyrillic soft fonts. I want to download them via HP's utility into printer's memory. In pure DOS I succeeded. But in DOSEMU I've got message "Unable to open LPT" :(

---

### Post by emendelson on 2007-10-22
You should get a quick answer from the mailing list at:

[http://dosemu.sourceforge.net/mailinglist.html](http://dosemu.sourceforge.net/mailinglist.html)

---

### Post by Voland on 2007-10-22
Thank you, but I have solved this problem. I made script containing this:
```

#!/bin/bash
cat ~/crr00cpo.sfs ~/default.pjl | lpr -l -P LaserJet-5L
xdosemu

```
where crr00cpo.sfs  and default.pjl are taken from [here]("ftp://admin.tomsk.ru/drivers/printer/hp/lj/5l/dos")
Then I edited /etc/dosemu/dosemu.conf like this:
```

$_printer = "LaserJet-5L"
$_printer_command = "lpr -l"
$_printer_timeout = (20)

```
And it works perfect.

---

### Post by emendelson on 2007-10-27
Is there a login/password for that download site?

EDIT:

No need to reply - a quick search for that font file produced other, accessible copies.

---

