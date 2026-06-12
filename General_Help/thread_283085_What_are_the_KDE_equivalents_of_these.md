---
title: "What are the KDE equivalents of these?"
date: 2006-10-23
forum: General Help
---

### Post by ianmacgregor on 2006-10-23
I am attempting to switch from gnome to KDE and would like to know the KDE equivalents of these gnome apps:

seahorse (gui for gpg keys)
revelation (password manager)
xchat (IRC)
gftp (gui ftp app)
firefox (web browser)
gnome baker (burning app)
gimp (Does anyone not know what this is?)
grip (cd ripping app)
easytag (mp3 tagging app)
gcolor2 (color picker)
evolution (email, contacts, calendar, todo list, etc)
gaim (IM app)
liferea (RSS feed reader)
grisbi (personal finance manager)
rubrica (address book)
glade (gui designer)
meld (graphical duff viewer)
screem (web/html IDE)
acidrip (rip DVD's to avi/mpeg)


Also, I design apps with python and use glade to design the interfaces. Does KDevelop allow you to design apps with python?

I'll stick with MPlayer/Xine for DVD movies and xmms for mp3's as I am happy with those apps.

Can someone post some equivalents for me to install?

Thanks :)

---

### Post by fritz_monroe on 2006-10-23
I'm not entirely sure, but I think you can use just about everything here with KDE.  Some of them, like Firefox and the GIMP, aren't Gnome apps.  The others that are Gnome apps can run just fine on KDE, but it will use the Gnome "framework."  Synaptic (Don't know if this is Gnome specific) will take care of the dependencies.

---

### Post by skymt on 2006-10-23
Seahorse: KGPG

XChat: Konversation

GFTP: Konqueror, KFTPGrabber

Firefox: Konqueror

Gnome Baker: K3B

Gimp: Krita (though Gimp is much, much better IMO)

GRip: Konqueror (enter "cdaudio://" in the address bar), or KAudioCreator

Easytag: KID3

GColor2: I think the kdewebdev package installs something like this, but I can't find it browsing through packages.ubuntu.com

Evolution: Kontact

Gaim: Kopete

Liferea: Akregator (integrated into Kontact, or standalone)

Grisbi: KMyMoney

Rubrica: Kontact

Glade: KDevelop Designer

Meld: KDiff

Screem: Quanta

Acidrip: K9Copy? I don't rip DVDs, so I don't know.



KDevelop doesn't encourage development with Python. It's very much geared toward C++ development. You can develop Qt applications with python (python-qt3, python-kde3). I don't know whether python-qt3 allows you to load interfaces created in KDevelop Designer, but it should.

---

### Post by ianmacgregor on 2006-10-23
> **fritz_monroe said:**
> I'm not entirely sure, but I think you can use just about everything here with KDE.  Some of them, like Firefox and the GIMP, aren't Gnome apps.  The others that are Gnome apps can run just fine on KDE, but it will use the Gnome "framework."  Synaptic (Don't know if this is Gnome specific) will take care of the dependencies.

Well, I am trying to completely switch all apps to KDE apps. I don't like the idea of loading up gnome libs just for an app or two, and I have never seen anyone get gnome apps and KDE apps using the same exact theme without any difference.. yes, I am that picky about appearance.

---

### Post by TheMatt on 2006-10-23
K9Copy does rip DVDs, quite well at that.

---

### Post by skymt on 2006-10-23
> **ianmacgregor said:**
> Well, I am trying to completely switch all apps to KDE apps. I don't like the idea of loading up gnome libs just for an app or two, and I have never seen anyone get gnome apps and KDE apps using the same exact theme without any difference.. yes, I am that picky about appearance.

Then you'll want Konqueror or Opera (which also uses QT) instead of Firefox. Gimp is the toughest to replace. Krita is nowhere near good enough yet.

---

### Post by tubasoldier on 2006-10-23
revelation - KDE Wallet

grip - You can use Konqueror to rip your disks. just visit audiocd://

easytag - You can tag your files in Amarok

evolution - Kontact

liferea - Akregator

grisbi - Kmymoney

screem - NVU

acidrip - K9copy is great.

---

### Post by ianmacgregor on 2006-10-23
> **skymt said:**
> Seahorse: KGPG

XChat: Konversation

GFTP: Konqueror, KFTPGrabber

Firefox: Konqueror

Gnome Baker: K3B

Gimp: Krita (though Gimp is much, much better IMO)

GRip: Konqueror (enter "cdaudio://" in the address bar), or KAudioCreator

Easytag: KID3

GColor2: I think the kdewebdev package installs something like this, but I can't find it browsing through packages.ubuntu.com

Evolution: Kontact

Gaim: Kopete

Liferea: Akregator (integrated into Kontact, or standalone)

Grisbi: KMyMoney

Rubrica: Kontact

Glade: KDevelop Designer

Meld: KDiff

Screem: Quanta

Acidrip: K9Copy? I don't rip DVDs, so I don't know.



KDevelop doesn't encourage development with Python. It's very much geared toward C++ development. You can develop Qt applications with python (python-qt3, python-kde3). I don't know whether python-qt3 allows you to load interfaces created in KDevelop Designer, but it should.

Awesome! Thank you for the list :)
I may just learn C++ and leave python.

---

### Post by ianmacgregor on 2006-10-23
> **skymt said:**
> Then you'll want Konqueror or Opera (which also uses QT) instead of Firefox. Gimp is the toughest to replace. Krita is nowhere near good enough yet.

Yeah, I have heard good things about Opera, will give it a shot.
Well, my gimp skills kinda suck as it is, so krita will suffice.

---

### Post by ianmacgregor on 2006-10-23
> **tubasoldier said:**
> revelation - KDE Wallet

grip - You can use Konqueror to rip your disks. just visit audiocd://

easytag - You can tag your files in Amarok

evolution - Kontact

liferea - Akregator

grisbi - Kmymoney

screem - NVU

acidrip - K9copy is great.

NVU? Ok, I'll have a look at that one too.

---

### Post by skymt on 2006-10-23
> **ianmacgregor said:**
> NVU? Ok, I'll have a look at that one too.

NVU is GTK, as I recall. So it won't match your KDE theme.

---

### Post by ianmacgregor on 2006-10-23
> **skymt said:**
> NVU is GTK, as I recall. So it won't match your KDE theme.

Ah, hah, thanks for the heads up :)

---

