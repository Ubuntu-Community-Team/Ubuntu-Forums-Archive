---
title: "Wubi reinstalling problems"
date: 2007-07-12
forum: General Help
---

### Post by lewix on 2007-07-12
"Hello world!"
First really congratulation, wubi is a great project.
So this is my problem:
- i installed wubi (with ubuntustudio) in my pc where was installed winXP
- ubuntustudio was installed correctly and it worked, but i had to disinstall it because i would to reinstall with bigger space
- then i removed wubi installation from xp, and i relaunched wubi installation selecting more space to install
- when i rebooted the system, during ubuntustudio installation (the first steps!) an fatal error of installation occured.

Has anybody any suggestion to give me? Maybe when i disinstall  wubi, i have to remove other tmp files before reinstall it?
I hope somebody can help me please! :cry:

Regards,
Lewix

---

### Post by ago on 2007-07-12
Run wubi, when you uninstall check the box to backup the ISO, but uncheck the box to backup home. Then run wubi again

---

### Post by abn91c on 2007-07-12
you probably need to defrag XP if you havent done so

---

### Post by lewix on 2007-07-13
> **ago said:**
> Run wubi, when you uninstall check the box to backup the ISO, but uncheck the box to backup home. Then run wubi again

Thank you for your help.
I tried also this way, keeping, during the uninstall, only the iso. But the result is the same.
I also tried remove all (iso e home backup files), making a complete disinstall.

---

### Post by lewix on 2007-07-15
I tried to clean all tmp files by CCleaner but no news.
The error i get is the follow (i translated it, original was italian):
"Fatal error: can't load installation files from cd".
I tried also to mount the real cd od ubuntustudio (i have a copy on a real cd) but no way.

Have you any suggestions?

Thank you!
Lewix

---

### Post by ago on 2007-07-15
Have a look into /var/log/syslog when it jams, and attach here the relevant section (you can copy files to /media/host and see them in windows).

---

### Post by lewix on 2007-07-16
Et Voilà!
The attachment is a txt file of SYSLOG (truncated, sigh, i can't attach the whole 79k txt stream).
Wow, i used Nano as txt editor to view the content of this file :)
Syslog was successfully copied to /target directory, /media/host wasn't yet created at that time.
I hope this syslog will help you.

P.S.: i think really my problem is the same of RaigyCar
[http://ubuntuforums.org/showthread.php?t=502207]("http://ubuntuforums.org/showthread.php?t=502207")

Thank you again for your help :popcorn:
Lewix

P.S.(2): ago, are you italian i think... if so "Grazie ancora da parte di uno sviluppatore italiano di Mantova"!

---

### Post by ago on 2007-07-16
I need all the log, if you zip it, you can  attach it here.

PS si sono Italiano, tanti saluti a Mantova.

---

### Post by lewix on 2007-07-16
Ok the attachment now is full (zip)

Thank you
Lewix

---

### Post by ago on 2007-07-16
Hai un floppy o usb key inserita? Se cosi' togli tutto.

---

### Post by lewix on 2007-07-17
No davvero.
Tra l'altro non utilizzo nemmeno nessun mouse usb, uso il touchpad.
Il floppy non è inserito, il lettore floppy però è montato sul mio notebook.

---

### Post by ago on 2007-07-17
Do you have a CD insterted?

---

### Post by lewix on 2007-07-17
No, but i remember the last time i booted to install, cd slot was open.
If you want i will retry with cd slot closed (and no cd inserted), but i'm sure i already tried to boot installation without any cd or floppy or usb plugged in.

---

### Post by lewix on 2007-07-18
Ok i tried to reinstal and i checked there wasn't no cd, floppy and usb.
I also unplugged my pcimca wifi card.
Result is the same.
Last chance is to install UbuntuStudio by the normal procedure (with real partiitons)? I'm able but I'm sorry, Wubi for me is great and more safety. :frown:

Lewix

---

