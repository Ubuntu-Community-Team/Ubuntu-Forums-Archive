---
title: "cannot remove dir â"
date: 2008-03-21
forum: General Help
---

### Post by uberlinux on 2008-03-21
So I somehow made a dir named â.  I can't make that character with my keyboard in order to rm -rf it.  Could anyone please provide me with the key sequence to call it?  It's on a typical 104 key US english installation.  Thanks guys.

---

### Post by jespdj on 2008-03-21
If you can't type it in, then how did you get it into your post?
Can't you navigate to it with Nautilus and delete it by clicking on it and pressing Delete?

You could set your keyboard to US International and then type in ^ (shift-6) and a: â

---

### Post by jonvel on 2008-03-21
> **jespdj said:**
> If you can't type it in, then how did you get it into your post?
Can't you navigate to it with Nautilus and delete it by clicking on it and pressing Delete?


I've had lots of things bomb out in ... interesting ... ways, sometimes dumping junkly named files into a directory.  I've had non-printable characters as file names before, also.  I suppose you could use some weird combination of ls piped to od to get the file and make the octal form of the name, also.

The way I've gotten rid of them is exactly what you suggested:  Use Places -> Home Folder and navigate to wherever the offending thing is, and remove or rename it from there.

---

### Post by uberlinux on 2008-03-21
rm -rf â does not work, doing this as root mind you.  This is on a cli-only box.

Thanks guys

---

### Post by justleen on 2008-03-21
you can use a "?" as a single char wildcard.
just type the file name, replacing the odd char with a ?

---

