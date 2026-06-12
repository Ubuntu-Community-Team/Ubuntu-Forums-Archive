---
title: "How to edit Gnome's &quot;Open With&quot; list?"
date: 2007-02-15
forum: General Help
---

### Post by Phrawm48 on 2007-02-15
For Gnome 2.14.3, Ubuntu 6.06.

How can I edit the **Open With** choices Gnome displays when I right-click a file?

In addition to the default value displayed at the top of the shortcut menu, I'd like to add or remove the choices in the **Open With** sub-menu.

Can anyone please tell me how to do that?

Cheers & thanks,
Ric
SFO

---

### Post by charl.ie on 2007-02-15
Right click on a file of the type you want to change. Click on properties, then "Open With".

---

### Post by Phrawm48 on 2007-02-15
Thanks.  That tip allowed me to specify the default.  That same dialog box doesn't, however, seem to allow me to remove choices from the secondary **Open With** sub-menu.

For example (and thanks to your tip) right-clicking a file named *example.txt* now shows *Gvim *as the default for *.txt* files.  So far, so good.

But the secondary **Open With** sub-menu still includes choices (e.g., Kate, Kwrite) that I want to remove entirely.

Do you happen to know how I can do that?

Cheers & thanks 'gain,
Ric
SFO

---

### Post by charl.ie on 2007-02-15
There is the remove button, but that seems disabled for any of the defaults.

---

### Post by Phrawm48 on 2007-02-15
*There is the remove button, but that seems disabled for any of the defaults.*

Exactly!

There must be a list somewhere but I can't find it.  That list was what I was originally looking for when I created this post...

Cheers & thanks,
Ric
SFO

---

### Post by 7creature on 2007-02-26
Any progress? I would like to remove obsolete entries too :-(

---

### Post by Phrawm48 on 2007-02-26
*Any progress? I would like to remove obsolete entries too*

I haven't made any progress.  This appears to be yet another of those Linux things that requires a bit more research than I have time to put into it.  Sigh...

---

### Post by 7creature on 2007-02-26
Edit: I am using Edgy.

Seems I found it. I'm researching possible problems at the moment.

It was all about MIME.

Here is the list of MIMEs and associated applications (for all users):
```
/etc/gnome/defaults.list
```
User created (added) applications are stored here:
```
~/.local/share/applications/
```

The best way to remove application from "Open with" would be to edit corresponding application.desktop and remove the MIME from the MimeType section. And after that do
```
sudo update-desktop-database
```

So far for theory - haven't tried it yet (not in Ubuntu atm).

I am not sure which .desktop to modify - there are two depositories - in /usr/share/app-install/desktop and in /usr/share/applications (I'll need to test it ^_~).

Here is required documentation (well, you can read the whole MIME section - [http://www.gnome.org/learn/admin-guide/latest/mimetypes-0.html](http://www.gnome.org/learn/admin-guide/latest/mimetypes-0.html)):

[http://www.gnome.org/learn/admin-guide/latest/mimetypes-registering.html](http://www.gnome.org/learn/admin-guide/latest/mimetypes-registering.html)

---

### Post by Phrawm48 on 2007-02-27
7:

Cool -- that's very helpful information.

The first thing that comes to mind is that I can expunge the names of programs that I never used from one or more "Open With" lists.

Additionally, when I finally do explore it, I'll be curious to see if I can fix things so that in Dapper I can click on an email address in non-default Firefox 2.0 and have it open a new compose Window in Thunderbird.   This "simple" functionality isn't working right now and the term "MIME" reminds me of things email'ish...

Cheers & thanks for your help,
Riley

---

### Post by 7creature on 2007-02-27
Ok, the easy way. By 'easy' I mean - it's working but if you run update-desktop-database the list is reverted back to defaults.

```
gksudo gedit /usr/share/applications/mimeinfo.cache
```

Here is the list of MIME types and asociated applications - which are used in 'Open with' dialogs. Just remove applications you don't want to be present in "Open with".

Kinda 'crude' solution because as far as I know the mimecache is created automatically (probably during installtion of new applications), so I am afraid the only permanent solution is to directly modify application.desktop and to remove the MIME you don't want to be associated with that application (as I've described in earlier post).

---

### Post by Endolith on 2008-05-21
> **7creature said:**
> User created (added) applications are stored here:
```
~/.local/share/applications/
```

Aha!  Does anyone know why I have many multiple copies of the same thing here?  Can I just delete the extras?  They aren't identical, so which should I keep?

> AdobeReader.desktop
alacarte-made-1.desktop
alacarte-made-2.desktop
alacarte-made-3.desktop
alacarte-made-4.desktop
alacarte-made.desktop
defaults.list
displayconfig-gtk.desktop
file-roller-usercreated.desktop
firefox-usercustom.desktop
gdmsetup.desktop
gedit-usercreated-1.desktop
gedit-usercreated-1-usercustom.desktop
gedit-usercreated-2.desktop
gedit-usercreated.desktop
gedit-usercustom-1.desktop
gedit-usercustom-2.desktop
gedit-usercustom-3.desktop
gedit-usercustom-4.desktop
gedit-usercustom-5.desktop
gedit-usercustom-6.desktop
gedit-usercustom-6-usercustom-1.desktop
gedit-usercustom-6-usercustom-2.desktop
gedit-usercustom-6-usercustom-3.desktop
gedit-usercustom-6-usercustom-4.desktop
gedit-usercustom-6-usercustom-5.desktop
gedit-usercustom-6-usercustom-6.desktop
gedit-usercustom-6-usercustom.desktop
gedit-usercustom-7.desktop
gedit-usercustom-8.desktop
gedit-usercustom.desktop
gimp-usercustom.desktop
gksudo-usercreated-1.desktop
gksudo-usercreated.desktop
gnome-keyring-manager.desktop
gnome-terminal-usercustom.desktop
googleearth.desktop
Google-googleearth.desktop
gsynaptics.desktop
gthumb-usercustom.desktop
hal-device-manager.desktop
inkscape-usercustom.desktop
ktechlab-usercreated.desktop
mimeapps.list
mimeinfo.cache
nautilus-usercustom.desktop
octave3.0.desktop
ooo-calc.desktop
ooo-calc-usercustom.desktop
ooo-writer-usercustom-1.desktop
pd-usercreated.desktop
python-usercreated.desktop
sonic-visualiser-usercreated.desktop
TINATSCfile-usercreated.desktop
TINATSCfile-usercreated-usercustom.desktop
userapp-fslint-gui-Y2IXBU.desktop
wine/
wine-usercreated.desktop
wxmaxima-usercreated.desktop


Edit: Oh I see, each gedit file is for a different MIME type.  They don't differ otherwise.  How do I fix this?

---

