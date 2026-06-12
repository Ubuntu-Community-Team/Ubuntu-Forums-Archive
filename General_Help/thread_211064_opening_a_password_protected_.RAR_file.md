---
title: "opening a password protected .RAR file"
date: 2006-07-07
forum: General Help
---

### Post by Polygon on 2006-07-07
how is this accomplished? when i double click the password protected rar file , file roller says :

> An error occured while opening the archive. the command line exited abnormally

Encrypted file:  CRC failed in /media/windows/stuff/stuff.rar (password incorrect ?)


obviously that means the password is correct, but no where am i prompted to enter a password... 

is there anyway to open this file?

---

### Post by zhoux on 2006-07-07
go to edit => password
and re-extract

---

### Post by Polygon on 2006-07-07
that option is greyed out.

---

### Post by jimmygoon on 2006-07-07
The password incorrect was simply a guess. It could also mean that during the extraction it found out that the CRC failed meaning that the RAR was corrupted. Try using 7z (does the linux version do all the other archives like the windows version????) and try moving it to a windows pc as well. If you don't have one and the data in it is non-private you can email it to me and I'll try it under windows. (jimmygoon @T [email]gm@!l.com[/email]) w/o all the stupid characters of course...

---

### Post by Polygon on 2006-07-08
> **jimmygoon said:**
> The password incorrect was simply a guess. It could also mean that during the extraction it found out that the CRC failed meaning that the RAR was corrupted. Try using 7z (does the linux version do all the other archives like the windows version????) and try moving it to a windows pc as well. If you don't have one and the data in it is non-private you can email it to me and I'll try it under windows. (jimmygoon @T [email]gm@!l.com[/email]) w/o all the stupid characters of course...

the RAR file is non corrupt as i open it often in windows. i used winRAR to create the archive (in windows) which allows me to set a password on the archive, so without the right password, you cant open the archive.

Now, the archive manager in ubuntu is not letting me specify a passoword so every time i double click it, archive manager is like "error: CRC check failed" because the archive NEEDS a password but none is specified

is there any way to use file-roller (the archive manager) or the command like RAR command to open password protected files?

---

### Post by FredB on 2006-07-08
for those, use the command-line version of unrar. It will ask you for the password.

---

### Post by Polygon on 2006-07-08
thanks, that did it. they really should make it so that it asks you for your password though

---

### Post by pentolino on 2007-06-01
Same thing for 7-zip archives... :-(
No problem with command line but no way with fileroller, it doesn't prompt for password in any way and password from edit menu is greyed out.

---

### Post by soxs on 2007-06-06
after I had installed >>unrar<< from multiverse I was able to open passwd protected .rar archives

simply right-click, extract here
then a passwd input is requested
if the passwd is correct, it gets extracted

so.. , this seems to be the *normal* way (but waht is normal?)

Do have problems with other WinRAR created passwd-protected rar archives on linux, or is it only that special one?

If it is a general problem, thewn create another .rar-archive with a simple .txt-file and mail/PM me.

---

### Post by nightcap79 on 2007-09-20
The only solution at the moment is posted in this page:

[http://ubuntuforums.org/showthread.php?t=249754&highlight=unrar+password+protected](http://ubuntuforums.org/showthread.php?t=249754&highlight=unrar+password+protected)

---

