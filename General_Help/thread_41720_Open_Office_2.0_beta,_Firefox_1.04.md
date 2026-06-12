---
title: "Open Office 2.0 beta, Firefox 1.04"
date: 2005-06-14
forum: General Help
---

### Post by orev on 2005-06-14
Are these working for anyone on Kubuntu 5.04?

I have updated my repositories, I don't seem to be able to apt-get either. Maybe I am just using the wrong method or package name?

Can anyone point me to a url, or line me up with some information on this?

OO 2.0 is quite a bit better than previous versions in my opinion (been running it Winstyle), and the Firefox website won't let me download extentions until I upgrade Firefox.

Help please?

Your kindness will be repaid.... :)

---

### Post by angkor on 2005-06-14
```
apt-cache search openoffice.org2
openoffice.org2 - Office suite core, version 2.0
openoffice.org2-calc - OpenOffice.org office suite - spreadsheet
openoffice.org2-common - OpenOffice.org office suite architecture independent files
openoffice.org2-core - OpenOffice.org office suite architecture independent files
openoffice.org2-debian-files - Debian specific parts of OpenOffice.org
openoffice.org2-draw - OpenOffice.org office suite - drawing
openoffice.org2-evolution - Evolution 2 Addressbook support for OpenOffice.org
openoffice.org2-gnome - Gtk UI Plugin and GNOME File Picker for OpenOffice.org
openoffice.org2-impress - OpenOffice.org office suite - presentation
openoffice.org2-kde - KDE UI Plugin and KDE File Picker for OpenOffice.org
openoffice.org2-l10n-en-us - english_american language package for OpenOffice.org
openoffice.org2-math - OpenOffice.org office suite - equation editor
openoffice.org2-writer - OpenOffice.org office suite - word processor
``` 

Okey, now repay me  :grin: 

For firefox extensions read:

[http://www.ubuntuforums.org/showthread.php?t=38697&highlight=firefox+vendorsub](http://www.ubuntuforums.org/showthread.php?t=38697&highlight=firefox+vendorsub)

---

### Post by orev on 2005-06-14
10000 thanks.

OK.  Did the apt-cache search openoffice.org2.  Got the list.

Tried apt-get openoffice.org2, didn't work.  Am I missing something??

---

### Post by orev on 2005-06-14
sorted it out through synaptic

thank you.

---

### Post by angkor on 2005-06-15
[QUOTE=orev]
Tried apt-get openoffice.org2, didn't work.  Am I missing something??[/QUOTE]

To install it using apt you need to type:

sudo apt-get **install** openoffice.org2

You're welcome :)

---

### Post by orev on 2005-06-15
Thanks.  Got it installed through synaptic

---

### Post by Octane on 2005-06-20
[QUOTE=angkor]To install it using apt you need to type:

sudo apt-get **install** openoffice.org2

You're welcome :)[/QUOTE]
Just for the record, openoffice.org2-core is missing and you therefore cannot install the openoffice2.org package.

---

### Post by jdong on 2005-06-20
The betas that come with Hoary universe are old and outdated... I don't recommend it.

---

### Post by angkor on 2005-06-20
[QUOTE=Octane]Just for the record, openoffice.org2-core is missing and you therefore cannot install the openoffice2.org package.[/QUOTE]

 :-? 

```
apt-cache policy openoffice.org2-core
openoffice.org2-core:
  Installed: 1.9.79.2-0ubuntu2
  Candidate: 1.9.79.2-0ubuntu2
```

---

### Post by richpull on 2005-07-23
I tried all the suggestions on the forum but nothing worked. I am a newbie (all i can say atm that ubuntu rocks except for some minor problems) and i really need some guides on how to install rpm and deb packages etc.

I found the beta version of ooo2 on the ooo website. Tried to install it but to no avail (i did follow the installation instructions) Same thing for firefox 1.0.6

If someone can help me I would really appreciate it.

Thanks
Richard

---

### Post by Octane on 2005-07-23
[QUOTE=angkor]:-? 

```
apt-cache policy openoffice.org2-core
openoffice.org2-core:
  Installed: 1.9.79.2-0ubuntu2
  Candidate: 1.9.79.2-0ubuntu2
```[/QUOTE]
not for amd64

---

### Post by Who on 2005-07-23
[QUOTE=richpull]
I found the beta version of ooo2 on the ooo website. Tried to install it but to no avail (i did follow the installation instructions) Same thing for firefox 1.0.6

If someone can help me I would really appreciate it.
Richard[/QUOTE]
Righty,
OOO is not something I am good on, but with Firefox I can give advice from experience. (follow the bold bits if you are in a hurry :) )
**Download** the firefox-1.0.6.installer .tar.gz, and **extract it** to some sensible location (I think using 'extract here' works nicely if you have saved it in your home dir) and then, and here is the key bit, **run the 'firefox-installer' _shell script_ **(scripts=files ending in .sh, and with an icon looking like a shell (but in this case not having the .sh on the end :)) that execute a load of commands at once, basically little brograms, analagous (but far superior :P) to .bat files). **NOT** the firefox-installer-**bin!**. Normally in nautilus this can be done by double clicking on the script and **choosing 'run'**. If not it may be necessary to open a terminal and run the shell script from there (by using using cd to get to the directory and then typing "./firefox-installer"  eg
$ cd /myfirefoxdir/firefox-installer
$ ./firefox-installer
(you said you were a newbie, so forgive me if this is patronising :) )
remember Linux is case sensitive. Another usefull trick when using the command line is that by pressing tab part way through a word you call into effect 'bash auto completion' (you may need to press tab twice if there is more than one possible completion of the word you are typing). Using this is a way of checking you are typing the right stuff (eg not making typos).
Then, again crucially, w**hen you want to RUN firefox**, use the **shell script called firefox** to do so **NOT** the firefox.**bin** (middle click and drag firefox.bin to the desktop and choose 'link here' for easy access in the future)

---

### Post by jdong on 2005-07-23
Don't install Firefox this way unless you know what you're doing. The binary installer from mozilla.org doesn't register chrome registry and development headers compliant with a Debian/Ubuntu system. Later on, this will come back and haunt you.

Backports provides you with Firefox 1.0.4, which is the latest version deemed stable. Both 1.0.5 and 1.0.6 suffer from a problem where the browser will crash if you have any extensions.

---

### Post by richpull on 2005-07-24
To Who
I tried to install the 1.0.6 package but to no avail

root@ubuntu:~/firefox-installer # ./firefox-installer

(firefox-installer-bin:7616): Gdk-WARNING **: locale not supported by Xlib

(firefox-installer-bin:7616): Gdk-WARNING **: can not set locale modifiers

(firefox-installer-bin:7616): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-installer-bin:7616): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-installer-bin:7616): Gtk-WARNING **: /usr/lib/gtk-2.0/2.4.0/engines/libclearlooks.so: cannot open shared object file: No such file or directory

** (firefox-installer-bin:7616): WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
** (firefox-installer-bin:7616): WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
** (firefox-installer-bin:7616): WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
** (firefox-installer-bin:7616): WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
** (firefox-installer-bin:7616): WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
** (firefox-installer-bin:7616): WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
** (firefox-installer-bin:7616): WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
** (firefox-installer-bin:7616): WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
** (firefox-installer-bin:7616): WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
** (firefox-installer-bin:7616): WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
** (firefox-installer-bin:7616): WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-installer-bin:7616): GLib-GObject-CRITICAL **: file gobject.c: line 1561 (g_object_ref): assertion `G_IS_OBJECT (object)' failed

** (firefox-installer-bin:7616): CRITICAL **: file pango-engine.c: line 68 (_pango_engine_shape_shape): assertion `PANGO_IS_FONT (font)' failed

** ERROR **: file shape.c: line 75 (pango_shape): assertion failed: (glyphs->num_glyphs > 0)
aborting...
./firefox-installer: line 56:  7616 Aborted                 ./${BINNAME}-bin $@

To jdong
I did add serveral backport sites to my sources.list but to no avail. When i use Synaptic it just marks as Hit or Ignored.

Thanks for your speedy response
Richard

---

### Post by jdong on 2005-07-24
[QUOTE=richpull]
I did add serveral backport sites to my sources.list but to no avail. When i use Synaptic it just marks as Hit or Ignored.

Thanks for your speedy response
Richard[/QUOTE]

```

deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-backports-staging main universe multiverse restricted

```

That'll enable Backports + the Backports testing tree (-staging)

Currently, the testing tree contains a Firefox 1.0.6 package that some report work with plugins.

---

