---
title: "Apache is ignoring .htaccess files"
date: 2007-02-18
forum: General Help
---

### Post by Xzenome on 2007-02-18
I installed apache2 via apt-get (along with php5 and mysql) to use a development server. Anyway, Apache seems to be ignoring an .htacess files I make. I first noticed this when I was trying to use mod_rewrite and whatever I did had no effect. I also tried some parts of htaccess which I knew were pretty standard and they didn't do anything either. I even tried things that normally would give an Error 500, but still nothing. I've tried chowning it to root and chmoding it to plenty of dangerous (insecure) permissions but still I get nothing.

Any ideas?

---

### Post by LotsOfPhil on 2007-02-18
It might be because access is spelled differently than the way you spell it:

"ignoring an .htacess files"

Try looking into that.

---

### Post by Xzenome on 2007-02-18
My htaccess file was spelt correctly. So it isn't that. And it is any I create not just one.

---

### Post by LotsOfPhil on 2007-02-18
Sigh, not that easy. I don't do much with .htaccess. Here are the permissions on mine:

$ ls -l  .htaccess
-rwxrwxrwx 1 root root 26 2007-02-13 17:41 .htaccess

---

### Post by Xzenome on 2007-02-24
Nope still no luck.

---

### Post by lefthand on 2007-02-26
This worked for me 

[https://help.ubuntu.com/community/EnablingUseOfApacheHtaccessFiles](https://help.ubuntu.com/community/EnablingUseOfApacheHtaccessFiles)

which I found in this thread

[http://www.ubuntuforums.org/showthread.php?t=359126&highlight=htaccess](http://www.ubuntuforums.org/showthread.php?t=359126&highlight=htaccess)

Hope it works out for you, Xzenome

---

