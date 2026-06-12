---
title: "Help on lyx and new class"
date: 2007-09-25
forum: General Help
---

### Post by wilstar on 2007-09-25
I want to install "lextex" and "ratex" classes in Lyx 1.5.1. (you'll find them in [http://www.ctan.org/tex-archive/help/Catalogue/bytopic.html#law](http://www.ctan.org/tex-archive/help/Catalogue/bytopic.html#law) )
I tried to copy *.cls file with

```
sudo cp Desktop/rtklage/rtklage.cls /usr/share/texmf-tetex/tex/latex/base
```

ant then
```
sudo texhash
```

Then I did Reconfigure in lyx, but it didn't work.

Can anyone help me?
thanks.
wilstar

---

### Post by dakhan on 2007-10-15
General advice:

You'd better place downloaded classes in your home directory with path like this:

\home\user_name\texmf\tex\latex\rtklage

This way you won't be disturbing texlive package list of installed files and will be able to upgrade it from Ubuntu repositories without any problems with manually added TeX packages.

texhash by default will scan this directory as well - and the superuser privileges are not required.

I don't know about your stuff, but I have installed some packages this way and prepared my own LyX layouts for them - works like a charm :)

Best regards,
Andrzej

---

