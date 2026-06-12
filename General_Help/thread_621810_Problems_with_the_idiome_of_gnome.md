---
title: "Problems with the idiome of gnome"
date: 2007-11-24
forum: General Help
---

### Post by hraposo on 2007-11-24
I've a problem:

I use an disto: gNewSense, based in ubuntu, the gnome theme is the ubuntu theme, and all works like ubuntu.
**But the language is not totally in portuguese but both portuguese and english, special int pannel and desktop.**
In the begin I've all in portuguese, the problem appears recentlly...

**If I do dpkg-reconfigure locales, the output is:**
 
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "pt_PT:pt:pt_BR",
        LC_ALL = (unset),
        LC_MONETARY = "pt_PT.UTF-8",
        LC_NUMERIC = "C",
        LC_TIME = "C",
        LANG = "pt_PT.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_ALL to default locale: Arquivo ou diret&#65533;&#65533;rio n&#65533;&#65533;o encontrado
Generating locales...
  en_US.UTF-8... done
  pt_BR.UTF-8... done
  pt_PT.ISO-8859-1... done
  pt_PT.UTF-8... done
Generation complete.
Current default timezone: 'Europe/Lisbon'.
Local time is now:      Sat Nov 24 08:21:48 WET 2007.
Universal Time is now:  Sat Nov 24 08:21:48 UTC 2007.
Run 'tzconfig' if you wish to change it.
[B]
I think tha's the problem is this:

 en_US.UTF-8... done

Because I have that my ubuntu is all in portuguese : pt_PT[/B]

**Who can hel me?**

---

### Post by Toet on 2007-11-24
Try:

Go to System - Manage - Language Support

Click Portugese box in list.

---

### Post by hraposo on 2007-11-24
I just do that, but this don't change nothing. The english languase stills in desktop.

---

### Post by theheadlessrabbit on 2008-01-02
have you restarted your system?

you have to restart your computer before the new language settings take effect.

---

