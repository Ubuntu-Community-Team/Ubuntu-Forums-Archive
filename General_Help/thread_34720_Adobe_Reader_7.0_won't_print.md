---
title: "Adobe Reader 7.0 won't print"
date: 2005-05-16
forum: General Help
---

### Post by Bo Rosén on 2005-05-16
Acroread won't print. The README says to add -c to the print command, but all that happens is that I get a quick 'printing'-type window from acroread, the print icon appears briefly in the systray and then nothing.

Anyone else have problem with this?

---

### Post by Alexander Kirillov on 2005-05-16
[QUOTE=Bo Rosén]Acroread won't print. The README says to add -c to the print command, but all that happens is that I get a quick 'printing'-type window from acroread, the print icon appears briefly in the systray and then nothing.

Anyone else have problem with this?[/QUOTE]
 Does it happen with all the files or only wiht some files? Does the printer light blink (at least briefly)?

---

### Post by Bo Rosén on 2005-05-16
[QUOTE=Alexander Kirillov]Does it happen with all the files or only wiht some files? Does the printer light blink (at least briefly)?[/QUOTE]

Only some files it would seem. And for those that won't print, there's no 'blink' ;-)
XPDF seems to work fine, but I want to print both sides. (you know, first odd then even sides)

---

### Post by lorap on 2005-05-16
hi buddy!
it's being still a bug.
to fix it you've to deal with cups (native unix printing services).
all you've to do is to add your printer via cups.
go here and read how to do that:

[http://www.cups.org/documentation.php](http://www.cups.org/documentation.php)

---

### Post by Bo Rosén on 2005-05-16
[QUOTE=lorap]hi buddy!
it's being still a bug.
to fix it you've to deal with cups (native unix printing services).
all you've to do is to add your printer via cups.
[/QUOTE]

Sorry if I'm a bit thick here but are you saying that it's not enough to add the printer through the Gnome Cups interface (system --> administration --> printer) and that i'll have to add it again through some other means? The web interface is disabled of course, so lpadmin?

---

### Post by Alexander Kirillov on 2005-05-17
[QUOTE=Bo Rosén]Sorry if I'm a bit thick here but are you saying that it's not enough to add the printer through the Gnome Cups interface (system --> administration --> printer) and that i'll have to add it again through some other means? The web interface is disabled of course, so lpadmin?[/QUOTE]
 Gnome cups interface is quite enough - no need to do it elsewehere.

---

### Post by Bo Rosén on 2005-05-18
[QUOTE=Alexander Kirillov]Gnome cups interface is quite enough - no need to do it elsewehere.[/QUOTE]

Thanks. It seemed a little odd as the printer works well otherwise.

---

