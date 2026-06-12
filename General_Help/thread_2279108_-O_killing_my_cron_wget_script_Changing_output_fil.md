---
title: "-O killing my cron wget script? Changing output filename"
date: 2015-05-21
forum: General Help
---

### Post by brian70 on 2015-05-21
This should be super simple, no?
But for whatever reason nothing I do seems to fix it.

First of all, the command in and of itself (without cron) works perfect

```
wget --output-document=playlist.xml --directory-prefix=/var/www/html/xml 'http://www.XXXXXXXXX.com/file'
```

Exactly how I want it!

Now, I input this into a cronjob

```
* * * * * root /usr/bin/wget --output-document=playlist.xml --directory-prefix=/var/www/html/xml 'http://www.XXXXXXXXX.com/file' 
```

No output whatsoever.

I remove the '--output-document=playlist.xml' variable in cron...

```
* * * * * root /usr/bin/wget --directory-prefix=/var/www/html/xml 'http://www.XXXXXXXXX.com/file' 
```

And works great. Except its stuck in its hideously long file name, and doesn't overwrite the file once it wgets another instance, leaving me with a super long file name and .1, .2, .3, etc of it.


I realize this isn't the most efficient way to do what I'm doing, but it's part of a test environment, and for the life of me I can't figure out how to do the simple task of changing the wget output filename as a cronjob to my customization. What's the deal here?

Any help would be greatly appreciated!

---

### Post by spjackson on 2015-05-21
> **brian70 said:**
> 
```
wget --output-document=playlist.xml --directory-prefix=/var/www/html/xml 'http://www.XXXXXXXXX.com/file'
```

This outputs to playlist.xml in the **current** directory (which is probably /root), not /var/www/html/xml. What you probably want is
```
wget --output-document=/var/www/html/xml/playlist.xml  'http://www.XXXXXXXXX.com/file'
```

---

### Post by brian70 on 2015-05-21
> **spjackson said:**
> This outputs to playlist.xml in the **current** directory (which is probably /root), not /var/www/html/xml. What you probably want is
```
wget --output-document=/var/www/html/xml/playlist.xml  'http://www.XXXXXXXXX.com/file'
```

That was it!

Thanks so much :-)

---

