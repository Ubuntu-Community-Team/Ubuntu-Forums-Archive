---
title: "Firefox cannot display East Asian characters"
date: 2007-07-07
forum: General Help
---

### Post by oldcpu on 2007-07-07
I have installed firefox the same way I have always installed it in Ubuntu.  'sudo aptitude install firefox'  But this time when I installed firefox, it missed out the East Asian characters!  Before, the characters shows in Firefox when I installed it without having me to do anything at all to make it show.

I went to Wikipedia and noticed all these squares with 4 alphanumerics in it when I looked at the language list on the left.  And some language characters were not showing properly.  Most noticably the East Asian ones.  I played around with all the Character Encoding settings and still can not get it to show.  I have changed the fonts around and they still would not show.

I tried it in Opera, and it is working fine.  I do not know why Firefox is not showing it.

Anyone know how to solve this?

Note that I am NOT trying to install an East Asian character input.  I just want them to be displayed properly in Firefox so I do not get all these funny squares.

---

### Post by bettlebrox on 2007-07-07
There are various lang packs for firefox that you can install. I'm not sure which one you need but you can see what ones are available using this command:

apt-cache search firefox lang

and install using:

[INDENT]sudo apt-get install package-name[/INDENT]

E.G. To install the lang pack for "mozilla-firefox-locale-en-gb - Mozilla Firefox English language/region package"

[INDENT]sudo apt-get install mozilla-firefox-locale-en-gb[/INDENT]

---

