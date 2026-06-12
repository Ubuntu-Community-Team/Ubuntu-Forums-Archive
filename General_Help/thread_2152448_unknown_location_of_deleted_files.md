---
title: "unknown location of deleted files?"
date: 2013-06-07
forum: General Help
---

### Post by lightsaberlesbian on 2013-06-07
I just tried to delete over 15 gb of files.  Unfortunately none of them went to the trash.  Evidently they're still taking up space because I'm still low on it.  Does anyone know where they could have gone?

---

### Post by lightsaberlesbian on 2013-06-07
okay apparently they're in .local/share/Trash but they refuse to be deleted...

---

### Post by kostkon on 2013-06-07
Can you see the files after giving:
```
ls ~/.local/share/Trash/files
```
if you do, then just go into that folder and delete them again.
EDIT:
try with sudo, i.e.
```
sudo nautilus ~/.local/share/Trash/files
```

---

### Post by lightsaberlesbian on 2013-06-07
I saw them under "ls" but i couldn't delete them in root

---

### Post by lightsaberlesbian on 2013-06-07
the following is the output > sushi@X:~$ sudo dolphin ~/.local/share/Trash/filesFontconfig warning: "/etc/fonts/conf.d/50-user.conf", line 9: reading configurations from ~/.fonts.conf is deprecated.
Error: "/var/tmp/kdecache-sushi" is owned by uid 1000 instead of uid 0.
KUrl("file:///home/sushi") KUrl("") 
KUrl("file:///home/sushi") KUrl("file:///home/sushi") 
KUrl("file:///home/sushi") KUrl("file:///home/sushi") 
KUrl("file:///home/sushi/.local/share/Trash/files") KUrl("") 
Error: "/tmp/ksocket-sushi" is owned by uid 1000 instead of uid 0.
Error: "/tmp/kde-sushi" is owned by uid 1000 instead of uid 0.
QPixmap::scaled: Pixmap is a null pixmap
QPixmap::scaled: Pixmap is a null pixmap
QPixmap::scaled: Pixmap is a null pixmap
kio_trash(869) TrashProtocol::createUDSEntry: couldn't stat  "/home/sushi/.local/share/Trash/files/Amour (2012) Love HQ AC3 DD5 1.1 (Externe Eng Ned Subs)" 
kio_trash(869) TrashProtocol::createUDSEntry: couldn't stat  "/home/sushi/.local/share/Trash/files/Amour (2012) Love HQ AC3 DD5 2.1 (Externe Eng Ned Subs)" 
kio_trash(869) TrashProtocol::createUDSEntry: couldn't stat  "/home/sushi/.local/share/Trash/files/Amour (2012) Love HQ AC3 DD5 3.1 (Externe Eng Ned Subs)" 
kio_trash(869) TrashProtocol::createUDSEntry: couldn't stat  "/home/sushi/.local/share/Trash/files/Bakemonogatari 1" 
kio_trash(869) TrashProtocol::createUDSEntry: couldn't stat  "/home/sushi/.local/share/Trash/files/Bakemonogatari 2" 
kio_trash(869) TrashProtocol::createUDSEntry: couldn't stat  "/home/sushi/.local/share/Trash/files/Bakemonogatari 3" 
kio_trash(869) TrashProtocol::createUDSEntry: couldn't stat  "/home/sushi/.local/share/Trash/files/Bakemonogatari 4" 
kio_trash(869) TrashProtocol::createUDSEntry: couldn't stat  "/home/sushi/.local/share/Trash/files/Bakemonogatari 5" 
kio_trash(869) TrashProtocol::createUDSEntry: couldn't stat  "/home/sushi/.local/share/Trash/files/Bakemonogatari 6" 
kio_trash(869) TrashProtocol::createUDSEntry: couldn't stat  "/home/sushi/.local/share/Trash/files/Bakemonogatari 7" 
kio_trash(869) TrashProtocol::createUDSEntry: couldn't stat  "/home/sushi/.local/share/Trash/files/DIT  Step 3" 
kio_trash(869) TrashProtocol::createUDSEntry: couldn't stat  "/home/sushi/.local/share/Trash/files/DIT  Step 4" 
kio_trash(869) TrashProtocol::createUDSEntry: couldn't stat  "/home/sushi/.local/share/Trash/files/DIT  Step 5" 
kio_trash(869) TrashProtocol::createUDSEntry: couldn't stat  "/home/sushi/.local/share/Trash/files/DIT  Step 6" 
kio_trash(869) TrashProtocol::createUDSEntry: couldn't stat  "/home/sushi/.local/share/Trash/files/DIT  Step 7" 
kio_trash(869) TrashProtocol::createUDSEntry: couldn't stat  "/home/sushi/.local/share/Trash/files/DIT Videos 2013" 
kio_trash(869) TrashProtocol::createUDSEntry: couldn't stat  "/home/sushi/.local/share/Trash/files/DIT Videos 2014" 
kio_trash(869) TrashProtocol::createUDSEntry: couldn't stat  "/home/sushi/.local/share/Trash/files/DIT Videos 2015" 
kio_trash(869) TrashProtocol::createUDSEntry: couldn't stat  "/home/sushi/.local/share/Trash/files/DIT Videos 2016" 
kio_trash(869) TrashProtocol::createUDSEntry: couldn't stat  "/home/sushi/.local/share/Trash/files/DIT Videos 2017" 
kio_trash(869) TrashProtocol::createUDSEntry: couldn't stat  "/home/sushi/.local/share/Trash/files/reflection 1.odt" 
kio_trash(869) TrashProtocol::createUDSEntry: couldn't stat  "/home/sushi/.local/share/Trash/files/reflection 2.odt" 
kio_trash(869) TrashProtocol::createUDSEntry: couldn't stat  "/home/sushi/.local/share/Trash/files/reflection 3.odt" 
kio_trash(869) TrashProtocol::createUDSEntry: couldn't stat  "/home/sushi/.local/share/Trash/files/reflection.odt" 
kio_trash(869) TrashProtocol::createUDSEntry: couldn't stat  "/home/sushi/.local/share/Trash/files/SOAP_card 1.pdf" 
kio_trash(869) TrashProtocol::createUDSEntry: couldn't stat  "/home/sushi/.local/share/Trash/files/SOAP_card 2.pdf" 
kio_trash(869) TrashProtocol::createUDSEntry: couldn't stat  "/home/sushi/.local/share/Trash/files/SOAP_card 3.pdf" 
kio_trash(869) TrashProtocol::createUDSEntry: couldn't stat  "/home/sushi/.local/share/Trash/files/SOAP_card.pdf" 
kio_trash(869) TrashProtocol::createUDSEntry: couldn't stat  "/home/sushi/.local/share/Trash/files/zzzDIT Incomplete Videos 2013" 
kio_trash(869) TrashProtocol::createUDSEntry: couldn't stat  "/home/sushi/.local/share/Trash/files/zzzDIT Incomplete Videos 2014" 
kio_trash(869) TrashProtocol::createUDSEntry: couldn't stat  "/home/sushi/.local/share/Trash/files/zzzDIT Incomplete Videos 2015" 
kio_trash(869) TrashProtocol::createUDSEntry: couldn't stat  "/home/sushi/.local/share/Trash/files/zzzDIT Incomplete Videos 2016" 
Fontconfig warning: "/etc/fonts/conf.d/50-user.conf", line 9: reading configurations from ~/.fonts.conf is deprecated.
Error: "/var/tmp/kdecache-sushi" is owned by uid 1000 instead of uid 0.


---

### Post by kostkon on 2013-06-07
Did it open a new window?

---

### Post by SeijiSensei on 2013-06-08
> I saw them under "ls" but i couldn't delete them in root 

Does that mean you tried

```

cd /home/sushi/.local/share/Trash/
sudo rm -rf *

```

and could not delete the files?

---

### Post by lightsaberlesbian on 2013-06-08
Seiji's advice worked.  I thought I could delete the files after loading dolphin as root in terminal.  would that have required gksudo?  I've never really known what that code was for.

---

