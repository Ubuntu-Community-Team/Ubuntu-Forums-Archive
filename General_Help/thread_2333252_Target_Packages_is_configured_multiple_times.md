---
title: "Target Packages is configured multiple times"
date: 2016-08-08
forum: General Help
---

### Post by LaughingHorse on 2016-08-08
I just installed 16.04.01 LTS and installed some packages using Terminal and some packages using Synaptic and Ubuntu Software Store (or whatever it's called : )

While installing another package using Synaptic after the install I got this message:

```
W: Target Packages (partner/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:52 and /etc/apt/sources.list:97
W: Target Packages (partner/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:52 and /etc/apt/sources.list:97
W: Target Packages (partner/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:52 and /etc/apt/sources.list:97
W: Target Translations (partner/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:52 and /etc/apt/sources.list:97
W: Target Translations (partner/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:52 and /etc/apt/sources.list:97
W: Target DEP-11 (partner/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:52 and /etc/apt/sources.list:97
W: Target DEP-11-icons (partner/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:52 and /etc/apt/sources.list:97
W: Target Packages (partner/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:52 and /etc/apt/sources.list:139
W: Target Packages (partner/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:52 and /etc/apt/sources.list:139
W: Target Packages (partner/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:52 and /etc/apt/sources.list:139
W: Target Translations (partner/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:52 and /etc/apt/sources.list:139
W: Target Translations (partner/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:52 and /etc/apt/sources.list:139
W: Target DEP-11 (partner/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:52 and /etc/apt/sources.list:139
W: Target DEP-11-icons (partner/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:52 and /etc/apt/sources.list:139


```

How do I clean this up?

Thank You in advance for your help and suggestions!

---

### Post by deadflowr on 2016-08-08
Perhaps looking at the sources.list file would help.
Are there multiple partners repositories listed in it?
You might also look in the lists folder for duplicates: /var/lib/apt/lists

---

### Post by LaughingHorse on 2016-08-08
Is there a command I can use to let me know multiple partners repositories listed in sources.list

---

### Post by deadflowr on 2016-08-08
Well, something like
```
 grep partner /etc/apt/sources.list
```
will output all lines containing partner, though you may only have one line enabled like so
```
deb http://archive.canonical.com/ubuntu xenial partner
```
and other lines like
```
# deb-src http://archive.canonical.com/ubuntu xenial partner
```
the # means the system ignores that line.

Another way is to open the file in Ubuntu's text editor gedit and run the find command (ctrl + F)
then type partner and it'll highlight and list all varients of partner in the file and you can easily toggle your way through them.

---

### Post by CantankRus on 2016-08-09
This command will show duplicate sources...
```
S="/etc/apt/sources.list" ; S2="$S ${S}.d/*.list" ; grep -b "^deb`cat $S2 | grep -i "^deb[[:space:]]http" | sort | uniq -dc | sed -e 's;[[:space:]]\+[[:digit:]]\+[[:space:]]\+deb\(.\+$\);\1;g'`$" $S2
```

---

### Post by LaughingHorse on 2016-08-09
Thank You deadflowr and CantankRus

---

