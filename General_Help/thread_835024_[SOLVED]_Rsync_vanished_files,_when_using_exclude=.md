---
title: "[SOLVED] Rsync vanished files, when using exclude="
date: 2008-06-20
forum: General Help
---

### Post by robklg on 2008-06-20
As you hopefully know (otherwise you cannot help me), rsync first searches the filesystems for files to copy, before it continues to actually copy them.

Now, the problem is that when I backup our webserver, the /var/www rsync returns an error 24 status. Several files in there vanish.

The vanished files are session files, that start with sess_*

I would expect when I exclude those, there will be no code 24 (vanished files) errors or return values, right ? Such as: rsync -avz --exclude=svn_* root@server:/var/www /backup/server/

This is not the case! Even when I exclude these files, it still complains about them.

I could simply ignore the return value of 24 ofcourse. But that is not a pretty way to do things. Also because I only don't want to copy any session files; If something else causes this error than my session files, I would like the non-null return value.

Does anyone have an idea on how to fix this cleanly? Or do I need to hack the source?

The rsync version I use is from Ubuntu 8.04 Server.

---

### Post by imneo on 2008-06-20
do :
```
rsync --help
man rsync
```

and try to see how to do this

---

### Post by robklg on 2008-06-20
> **imneo said:**
> do :
```
rsync --help
man rsync
```

and try to see how to do this

:|
spare yourself and me the time of this post...

---

### Post by robklg on 2008-07-03
Turns out the path in --exclude is relative to the path being copied. I.e.:

You want to backup /var/log, but nog /var/log/apache2, then;

you cannot: rsync -a --exclude=/var/log/apache2 user@host:/var/log /backup

but you must: rsync -a --exclude=/apache2 user@host:/var/log /backup

This is not at all obvious from the man-page. In fact there is no mention of it.

Well thanks again for your "help"

---

### Post by kevdog on 2008-07-03
Great find, thanks for the info.

---

