---
title: "wrong utf encoding in nano"
date: 2014-11-13
forum: General Help
---

### Post by dargaud2 on 2014-11-13
Hello all,
since some recent updates (14.10 ? Or slightly before), I've been having encoding/locale issues on multiple systems. In particular the nano editor cannot use utf characters. If I type 'â' in it, it displays garbage.
```
$ locale
LANG=en_US.UTF-8
LANGUAGE=en_US
LC_CTYPE="en_US.UTF-8"
LC_NUMERIC="en_US.UTF-8"
LC_TIME="en_US.UTF-8"
LC_COLLATE="en_US.UTF-8"
LC_MONETARY="en_US.UTF-8"
LC_MESSAGES="en_US.UTF-8"
LC_PAPER="en_US.UTF-8"
LC_NAME="en_US.UTF-8"
LC_ADDRESS="en_US.UTF-8"
LC_TELEPHONE="en_US.UTF-8"
LC_MEASUREMENT="en_US.UTF-8"
LC_IDENTIFICATION="en_US.UTF-8"
LC_ALL=en_US.UTF-8
```
But something strange:
```
$ echo "âéè°" | chardet
<stdin>: ISO-8859-7 (confidence: 0.99)
```
Why not UTF-8 ?

---

### Post by Impavidus on 2014-11-13
As nano runs in a terminal, check the character encoding of your terminal. I don't know which terminal you use, but there must be a setting somewhere.

---

### Post by dargaud2 on 2014-11-14
OK, thanks, I think I got it. I indeed had trouble in the Konsole, not only in nano (touch â would return garbage with ls). But strangely I had no trouble with the terminal I get when pressing F4 in the Dolphin file manager. 'locale' returned the exact same thing in both cases. I went to the advanced profile options in Konsole and changed the encoding from Default/UTF-8 to UTF-8 and now it works. I have no idea what this changes...

---

