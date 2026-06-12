---
title: "convert .run files to deb package?"
date: 2007-09-26
forum: General Help
---

### Post by kcy29581 on 2007-09-26
Hi all,

I know how to install .RUN files, but obviously the installed application will then be outside of the package manager.

Is there a way to either convert the .RUN file to a deb package, or install it and allow the package manager to remove it when needed?

I think I did this ages ago...

Thanks

---

### Post by dabl on 2007-09-26
Do you mean .rpn ?  The package is Alien for that. :)

---

### Post by kcy29581 on 2007-09-26
> **dabl said:**
> Do you mean .rpn ?  The package is Alien for that. :)
I think you mean .RPM packages.

No, I mean .RUN files; they are installed like this:```
sudo sh *filename*
```

---

### Post by wirelessmonkey on 2007-09-26
Well..... a .run file is actually a shell script.  I 'THINK' it's possible to turn one into a .deb, at least in some circumstances.  In fact I think I saw a post about that a week or two ago, I'll see if I can find it.

---

### Post by wirelessmonkey on 2007-09-26
This link is for Ruby, but may work for your script.  [http://ubuntuforums.org/showthread.php?t=406069&highlight=shell+script+package](http://ubuntuforums.org/showthread.php?t=406069&highlight=shell+script+package)

---

### Post by kcy29581 on 2007-09-26
I'll have a look at epm, thanks. :)

---

### Post by paul.sijpkes on 2008-04-10
Did you have any success with this?

I would like to convert a .RUN script to a .DEB package too.

---

