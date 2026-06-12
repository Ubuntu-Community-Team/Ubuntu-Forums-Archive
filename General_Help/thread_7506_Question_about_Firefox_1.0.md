---
title: "Question about Firefox 1.0"
date: 2004-12-08
forum: General Help
---

### Post by infornography on 2004-12-08
I have just done a fresh install of Ubuntu. I would like the latest Firefox but I don't want to use hoary, so I was wondering.

If I empty the firefox directory (/usr/lib/mozilla-firefox), and then install the new version of Firefox (downloaded from mozilla.org) to that same directory, shouldn't everything keep going just as before, but with the newer Firefox? I haven't installed any plugins yet so they can't break.

I wanted to ask before I tried though, I don't want to end up breaking anything.

---

### Post by poofyhairguy on 2004-12-08
[QUOTE=infornography]I have just done a fresh install of Ubuntu. I would like the latest Firefox but I don't want to use hoary, so I was wondering.

If I empty the firefox directory (/usr/lib/mozilla-firefox), and then install the new version of Firefox (downloaded from mozilla.org) to that same directory, shouldn't everything keep going just as before, but with the newer Firefox? I haven't installed any plugins yet so they can't break.

I wanted to ask before I tried though, I don't want to end up breaking anything.[/QUOTE]

I've gotten it to work without deleting anything- just make a new laucher on your bar. Be sure to install all pluggins through firefox though.

---

### Post by infornography on 2004-12-08
Yeah, I've been keeping that as a last resort. I really don't want two of them installed if I don't have to.

---

### Post by Readis on 2004-12-08
[QUOTE=poofyhairguy]I've gotten it to work without deleting anything- just make a new laucher on your bar. Be sure to install all pluggins through firefox though.[/QUOTE]

Or just change the destination of the firefox button.  I changed that along with the icon inside of 'Applications'.  Been working great since.

-Readis

---

### Post by OrangeSlice on 2004-12-08
Enabling the debian.org repositories will allow you to install/upgrade to Firefox 1.0 via apt-get, just make sure to comment/delete the lines from your sources.list afterwards or before you run a dist-upgrade (I made that mistake once, heh.)

```
deb http://ftp.debian.org/debian/ unstable main 
deb http://ftp.debian.org/debian/ testing main 
deb http://ftp.debian.org/debian/ stable main 
```

There's all 3, Firefox 1.0-4 is in testing, so the other two lines can be left out if you want.  After adding the line(s), run apt-get update, and then apt-get install mozilla-firefox.

---

