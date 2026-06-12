---
title: "network unbuntu, mac osx, windows"
date: 2005-10-25
forum: General Help
---

### Post by rplantz on 2005-10-25
I have the ubuntu (amd64) machine, a Mac running OSX, and a windows machine all connected through a router.

I've installed samba and have tried several methods given in this forum and one given in [http://help.ubuntu.com/starterguide/C/faqguide-all.html](http://help.ubuntu.com/starterguide/C/faqguide-all.html)
to allow me to share files and printers.
Several almost do it, but none seems to be quite complete.

Most seem very clear, except for a couple of confusing things. For example, the faq cited above says that I should create the file:
```
/etc/samba/smbusers
```
that contains the line ```
system_username = "network username"
```
The syntax is not consistent here, so I can't figure out exactly what to do. I saw in another place that the correct statement for user joe is ```
joe = "joe"
```
but that didn't work for me.

The weird thing (to me) is that they all seem to differ significantly.

Can anyone point me to one that will work, can be read, and gives a secure LAN in my home? Ideally, the instructions would refer me to the corresponding description in the appropriate man page. (Okay, we don't live in an ideal world, but I can dream. :-) ) I'm trying to do more than simply get it to work; I want to understand what's going on.

Bob

---

