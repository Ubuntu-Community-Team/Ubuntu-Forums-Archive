---
title: "character set problems"
date: 2004-11-21
forum: General Help
---

### Post by unikum on 2004-11-21
I think my system use UTF-8. How do i change it to ISO-8859-15? 
I have problems with the letter å ä ö in some programs.

---

### Post by p!=f on 2004-11-21
[QUOTE=unikum]I think my system use UTF-8. How do i change it to ISO-8859-15? 
I have problems with the letter å ä ö in some programs.[/QUOTE]
By default sv_SE is aliased to sv_SE.ISO-8859-1.
```

[~] > cat /etc/locale.alias | grep swedish
swedish         sv_SE.ISO-8859-1

```
To change your locales run
```

sudo dpkg-reconfigure locales

```
You'll be prompted which locales to generate and after that which will be the default one so sv_SE.ISO-8859-15 is your choice. 

To check your current settings
```

[~] > cat /etc/environment
LANG=cs_CZ

```
*cs_CZ defaults to cs_CZ.ISO-8859-2*

Which programs don't work?

---

### Post by unikum on 2004-11-21
Ok, thanks i will try it.

When using xchat i can't use system settings. Have to use iso-8859-15. If not i cant see others typing  å ä ö and others can't see my å ä ö.
Same with Jin ([www.jinchess.com](www.jinchess.com)) . People see ? instead of å ä ö.

---

### Post by unikum on 2004-11-23
I found an easier way.
/usr/share/xsessions/gnome.desktop

Change 2nd line to: Encoding=ISO-8859-1

Reboot. Done!

---

### Post by p!=f on 2004-11-23
[QUOTE=unikum]I found an easier way.
/usr/share/xsessions/gnome.desktop

Change 2nd line to: Encoding=ISO-8859-1

Reboot. Done![/QUOTE]
It's not much easier as it will be overwritten during next update not to mention it will probably work only for Gnome. What if I also want to run other desktops/applications?

---

### Post by unikum on 2004-11-23
I change it for kde.desktop too

---

