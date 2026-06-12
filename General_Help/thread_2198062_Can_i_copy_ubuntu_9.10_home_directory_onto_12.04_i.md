---
title: "Can i copy ubuntu 9.10 home directory onto 12.04 install?"
date: 2014-01-06
forum: General Help
---

### Post by desconocido on 2014-01-06
Hi everyone,

My current computer runs Ubuntu 9.10. I have a new computer on which I have installed 12.04.
Can I replace my new 12.04 home directory with the contents of my 9.10 home directory without breaking anything?

I want to use my Thunderbird, Sunbird and Firefox data and bookmarks etc and my Nautilus bookmarks.
I also have Wine on 9.10.
Obviously programs that don't get automatically installed with Ubuntu (like Wine, Stellarium, ...) will need me to install them.

I also have LAMP and some databases elsewhere on the 9.10 system, but I will probably reinstall those from scratch.

Thanks in advance.

---

### Post by Impavidus on 2014-01-07
You could try, I don't think it can destroy your system or cause data loss. The software on your 9.10 system is old, as it has been unsupported for almost 3 years, so some incompatibilities can be expected. You could copy everything and hope for the best, and remove the configuration files in case a program doesn't work any more. However, many programs have changed the default location of their config files (often from ~/.application to ~/.config/application) and you'll have config files of programs that have been removed from Ubuntu and replaced by something else, so this will leave a lot of cruft in your home dir, in addition to applications not recognising your old config files.

The clean option would be to copy the home dir except the hidden files and dirs, and only copy config stuff of applications that you still need. If it doesn't work, revert and do it from scratch. Here is how you can copy all firefox settings and bookmarks: [https://support.mozilla.org/en-US/kb/back-and-restore-information-firefox-profiles](https://support.mozilla.org/en-US/kb/back-and-restore-information-firefox-profiles). With some help from google you must be able to find this info for other applications. Some have a backup option. Create a backup file of their settings and data on your old system and restore the backup on the new. Even with a newer version of the software, most of it should work.

I don't know about wine. This may be more complicated than copying your .wine.

---

### Post by Bucky Ball on 2014-01-07
Posted in error. ;)

---

### Post by desconocido on 2014-01-09
@Impavidus

Thanks. I will give it a try.

However, before I "move in", I am going to install Gnome Classic and Gnome Tweak Tool and remove Unity and Zeitgiest.
Can't stand the User Interface, icons and fonts of Unity. I guess Unity would be alright on a smatphone.

I'll post how I get on.

---

### Post by desconocido on 2014-02-10
> **Impavidus said:**
> ...The clean option would be to copy the home dir except the hidden files and dirs, and only copy config stuff of applications that you still need....

Thanks, I followed your advice. I have kept everything important from the old system, especially Thunderbird and Firefox:

> ¶ 20-Jan-2014
Copy contents of ~/.mozilla-thunderbird from 9.10 to ~/.thunderbird in 12.04
This copies 4ab15yor.default  to ~/.thunderbird and makes ~/.thunderbird/profiles.ini point to it.
Run Thunderbird, checks compatability of add-ons
New dictionaries installed, Remember Mismatched Domains disabled, I disabled connections with Unity.
Thunderbird 17.0.8 seems to work fine after that, with all old content and options.

¶ 21-Jan-2014
Copy contents of ~/.mozilla/firefox from 9.10 to ~/.mozilla/firefox in 12.04
This copies vh6aap3d.default  to ~/.mozilla/firefox and makes ~/.mozilla/firefox point to it.
Run Firefox, checks compatability of add-ons
Says AddBlockPlus 1.1.1 and FlashBlock 1.5.11.2 are incompatible; look for new versions:
Installs AddBlockPlus 2.4.1 and FlashBlock 1.5.17 
AddBlockPlus installs latest version of EasyList. I turn off "allow some non-intrusive advertising".
I turn on "Remove Social Media Buttons" which installs Fanboy's Social Blocking List.
I disabled Ubuntu Firefox Modifications 2.7
Fine tuned a few prefs
Firefox 23.0 seems to work fine after that, with all old bookmarks and options.

---

