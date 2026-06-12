---
title: "Ark and deb - no joy!"
date: 2006-10-23
forum: General Help
---

### Post by Nobber on 2006-10-23
On Kubuntu 6.06, if I try to open deb files from within Konqueror, Ark pops up and then complains thus:

"The utility is not in your PATH. Please install it or contact your system administrator."

Helpful error message, that! Install *what*, exactly? I'm a little surprised that on a system built on deb packages, there's apparently no utility that can extract them. :D

So, what do I need to install? :confused:

---

### Post by Jucato on 2006-10-23
Well, you don't use Ark to install .deb files. To install a .deb file from Konqueror, right-click on it and select the Kubuntu Package Menu.

(The reason that Ark tries to open the .deb is because a .deb file is also a sort of archive, something like a self-extracting ZIP file).

---

### Post by Nobber on 2006-10-23
Yeah, I don't want to install it, I just want to see what's inside the archive. (I'm currently figuring out how to create my own deb packages, so it would be useful to see what's inside others.)

I would have thought having the "ar" utility would be sufficient for Ark to be able to handle deb files, but it seems not. :(

---

### Post by Jucato on 2006-10-23
Ah, sorry I left this out. I think you need to install the package called *binutils* to do that.

Hope that helps.

---

### Post by Nobber on 2006-10-24
I already have binutils installed.

Turns out this is a [bug in Ark](https://launchpad.net/distros/ubuntu/+source/kdeutils/+bug/39534), but it does have a workaround: open Ark first, then use Ctrl-O to open the deb.

Annoying!

---

### Post by Jucato on 2006-10-24
Something must be wrong, then. or probably another package is needed, because I can open .deb packages normally in Ark in Dapper by clicking on it. Have you tried installing *unrar* (the one in multiverse) to see if it makes any difference?

---

### Post by Nobber on 2006-10-24
I already have *unrar* (the one from multiverse) installed too. :???:

---

### Post by Jucato on 2006-10-24
Hm.. I'm clueless as to how I'm able to do it on Dapper... :(

---

### Post by santox on 2006-12-04
Same thing is happening to me.

I open Ark and then Ctrl-0, but the popout is the same "install Ark".

Just our luck; I thought a tool like this came be default.

---

