---
title: "AMD64, Firefox32 fail to start, can't find progressbar_through.png"
date: 2006-08-23
forum: General Help
---

### Post by ehoffman on 2006-08-23
Hello

I have installed Firefox32 on an AMD64 platform, and it worked well.  However, lately, I realised it was no longer working (I mainly use 64-bit firefox unless I need Flash).

After some taught, I came to the conclusion that it stopped working after I selected 'Crux' desktop theme.

When I type firefox32, I get

** ERROR **: No such image: /usr/share/themes/Crux/pixmaps/progressbar_through.png
aborting...
/usr/local/firefox32/run-mozilla.sh: line 131: 19571 Aborted                  "$prog" ${1+"$@"}

Now, the png image DOES exist.  It is like firefox can't see it.  Could this ba a 'path too long' bug in firefox?  Or is it something else?  Has anyone saw this problem before?

Thanks

Eric

---

### Post by ehoffman on 2006-08-26
Anyone?

---

### Post by ifokkema on 2006-08-26
Not sure it's the shown error which makes Firefox fail to start up, but could you please type:
```
ls -l /usr/share/themes/Crux/pixmaps/progressbar_through.png
```
and post the output?

---

