---
title: "How do I find an installed font?"
date: 2016-10-12
forum: General Help
---

### Post by Evil Wayz on 2016-10-12
Recently I found a free TTF font and installed it into Ubuntu.  Several weeks passed by and I wanted to use that font, only now I don't recall its name.  I went thru the entire font list by hand and I don't see it there.  Is there some part of ubuntu that can tell me fonts I have installed besides the defaults?

---

### Post by CantankRus on 2016-10-12
There is the default font viewer but I find it quite kludgy to use.
I prefer to use gnome-specimen.

**[COLOR="#B22222"]Edit[/COLOR]**: Sorry, I misread your post but if it helps ...
fonts installed using the Font Viewer are placed in **~/.local/share/fonts** rather than  **~/.fonts**

```
sudo apt install gnome-specimen
```

---

### Post by vasa1 on 2016-10-12
> **Evil Wayz said:**
> ... Is there some part of ubuntu that can tell me fonts I have installed besides the defaults?
```
apt list --installed | grep -i font

WARNING: apt does not have a stable CLI interface. Use with caution in scripts.

fontconfig/xenial-updates,xenial-security,now 2.11.94-0ubuntu1.1 amd64 [installed,automatic]
fontconfig-config/xenial-updates,xenial-security,now 2.11.94-0ubuntu1.1 all [installed,automatic]
fonts-dejavu-core/xenial,now 2.35-1 all [installed,automatic]
fonts-freefont-ttf/xenial,now 20120503-4 all [installed]
fonts-guru/xenial,now 2:1.2 all [installed]
fonts-guru-extra/xenial,now 2.0-3 all [installed,automatic]
fonts-liberation/xenial,now 1.07.4-1 all [installed]
fonts-lohit-guru/xenial,now 2.5.3-2 all [installed,automatic]
fonts-opensymbol/xenial,now 2:102.7+LibO5.2.2-0ubuntu1~xenial0 all [installed,automatic]
fonts-sil-gentium/xenial,now 20081126:1.03-1 all [installed,automatic]
fonts-sil-gentium-basic/xenial,now 1.1-7 all [installed]
fonts-stix/xenial,now 1.1.1-4 all [installed,automatic]
fonts-symbola/xenial,now 2.59-1 all [installed,automatic]
gsfonts/xenial,now 1:8.11+urwcyr1.0.7~pre44-4.2ubuntu1 all [installed,automatic]
gsfonts-x11/xenial,now 0.24 all [installed,automatic]
libfontconfig1/xenial-updates,xenial-security,now 2.11.94-0ubuntu1.1 amd64 [installed,automatic]
libfontembed1/xenial-updates,now 1.8.3-2ubuntu3.1 amd64 [installed,automatic]
libfontenc1/xenial,now 1:1.1.3-1 amd64 [installed,automatic]
libxfont1/xenial,now 1:1.5.1-1 amd64 [installed,automatic]
ttf-ancient-fonts-symbola/xenial,now 2.59-1 all [installed]
ttf-ubuntu-font-family/xenial,now 1:0.83-0ubuntu2 all [installed,automatic]
xfonts-base/xenial,now 1:1.0.4+nmu1 all [installed,automatic]
xfonts-encodings/xenial,now 1:1.0.4-2 all [installed,automatic]
xfonts-utils/xenial,now 1:7.7+3 amd64 [installed,automatic]

```Some fonts have *[installed]* and most others have *[installed,automatic]*. You could "grep -v" to eliminate the lines with "automatic". Would that help?

---

### Post by Bashing-om on 2016-10-12
Evil Wayz; Hey ...

And yet a 3rd .
```

fc-list | less

```

Many paths
[INDENT][INDENT]can lead to one end
[INDENT][INDENT][INDENT][INDENT]'buntu
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by vasa1 on 2016-10-12
> **Evil Wayz said:**
> Recently I found a free TTF font and installed it into Ubuntu.  Several weeks passed by and I wanted to use that font, only now I don't recall its name. ... I have installed besides the defaults?
Well, OP wants to look through *only* user-installed fonts.

Assuming it was installed via a regular package manager or apt or apt-get and so is registered with the system, and depending on what OP means by "Recently" and "Several weeks passed by", the following may be lengthened or shortened to find the font:```
zgrep -i " install " /var/log/dpkg.log /var/log/dpkg.log.1 /var/log/dpkg.log.2.gz  /var/log/dpkg.log.3.gz | grep -i font
```

---

