---
title: "[SOLVED] How do you Check SHA1 Sums in Ubuntu?"
date: 2008-05-21
forum: General Help
---

### Post by OzzyFrank on 2008-05-21
Occassionally, disc images I check have SHA1sums instead of MD5sums, yet to my knowledge there is no app or even command for this purpose in Ubuntu. I once tried getting the command from Suse or some other distro, but either couldn't set it up or just didn't understand how to use it (I forget - it was a while back). Now I have a couple of Fedora 9 images I would like to verify, so need to know how to use the SHA1 sums.

---

### Post by ptn107 on 2008-05-21
From a terminal:

sha1sum *filename*

---

### Post by OzzyFrank on 2008-05-21
Der! I should have realised the command would be **sha1sum** not **sha1**, like **md5sum**. And that command is to create a sha1 sum, but to check it is similar to the option in md5sum:

**[COLOR="Indigo"]sha1sum -c filename[/COLOR]**

---

### Post by mattjason on 2009-02-13
found example on Fedora:
[http://basiclinuxcommand.blogspot.com/2008/08/check-sha1sum-sha1-checksums-value.html]("http://basiclinuxcommand.blogspot.com/2008/08/check-sha1sum-sha1-checksums-value.html")

on windows:
[http://www.labtestproject.com/win/sha1sum.exe.html]("http://www.labtestproject.com/win/sha1sum.exe.html")

hope that may help

---

### Post by WarmFuzzy on 2011-08-01
There is also sha512sum for those of us who want *really* unique and thorough hashes.  It's more than double the size output of sha1 though.

---

