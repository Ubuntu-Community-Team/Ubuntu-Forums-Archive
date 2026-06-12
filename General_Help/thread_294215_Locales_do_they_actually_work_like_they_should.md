---
title: "Locales: do they actually work like they should?"
date: 2006-11-06
forum: General Help
---

### Post by wolve on 2006-11-06
Hi,

SHORT QUESTION:

How do I get my all locales to fi_FI@EURO (ISO-8859-15) without having my software in finnish. This should include remote console (ssh) and local console (not x-terminal but the real deal) working with those locales too. /etc/environment doesn't seem to affect anything really.


LONG VERSION:

Let's start with something really simple. I wanna use iso-8859-15 character set (fi_FI@EURO) and finnish time, paper and other standards, but I wanna keep all software still in english. 

(Okay, I glued this together quite manually so it works only in gnome it seems, by generating that finnish locale and copying the correct parts from it to the english locale directory overwriting the wrong. But I'd like to get it working properly).

What I'm finding frustrating that even after running dpkg-reconfigure for 'locales' and tweaking /etc/environment when I actually log in using remote console (ssh) or local console (not x-terminal) I get different locales, when I log on root I get en_US.UTF-8 and as a normal user fi_FI.UTF-8. There is nothing like this at /etc/environment or anywhere. I don't wanna have anything to do with uft-8, I just wanna have fi_FI@EURO (ISO-8859-15) everywhere except I want all software in english.


Cookies to those who answer.

---

### Post by garba on 2006-11-06
this is an interesting problem, i wonder why you get different locales when you log in as root, try taking a look into .bashrc and .profile in /root, i seem to remembe default settings in /etc/skel are not copied to root's home folder... for what concerns your problem with ssh, bear in mind that the LANG env variable set in the bash shell you're starting the ssh client on will be "carried over" to the bash shell which will be spawned on the remote machine (unless it gets overridden on login of course)

---

### Post by elettronicha on 2006-11-09
Is there any guide about handling locales? 

I found many files on the system concerning with locales and I'd like to know what those files mean each one. In particular there are:

/var/lib/belocs/locales.dep
/var/lib/belocs/list
/var/lib/locales/supported.d/en
/var/lib/locales/supported.d/local
/usr/share/i18n/locales/
/usr/share/X11/locale/locale.alias

/etc/locale.alias
/usr/share/gettext/intl/locale.alias
/usr/share/locale/locale.alias

/etc/environment

---

### Post by garba on 2006-11-09
@elettronicha

chi è il personaggio che usi come avatar?

---

### Post by elettronicha on 2006-11-09
I've found a good [link in the wiki]("https://help.ubuntu.com/community/LocaleConf"), though it isn't too detailed.

> **garba said:**
> @elettronicha

chi è il personaggio che usi come avatar?
My avatar is not me, of course, neither my grandpa, it represents [James Clerk Maxwell]("http://it.wikipedia.org/wiki/James_Clerk_Maxwell"). ;)

---

### Post by garba on 2006-11-09
i figured, but i was unsure, actually i thought he was Ferraris (more so since you're from turin :mrgreen: )

---

