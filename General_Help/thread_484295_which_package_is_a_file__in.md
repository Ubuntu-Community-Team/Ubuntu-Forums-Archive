---
title: "which package is a file  in?"
date: 2007-06-25
forum: General Help
---

### Post by j1234f on 2007-06-25
If I have  a file that should be on
my system and got deleted, how do I find
out which package I need to apt-get install?

Thanks
j1234f

---

### Post by rillip on 2007-06-25
You'll have to do a search for the filename, ala Google or here on the forums to find out.  There may be a master file list somewhere but that would be beyond tedious

---

### Post by j1234f on 2007-06-25
Tried the internet search and found Debian has a search
for files in packages webpage at:
[http://www.debian.org/distrib/packages](http://www.debian.org/distrib/packages)

at the bottom of the page.
Seems like ubuntu uses the same names, I guess.

---

### Post by srt4play on 2007-06-25
> **j1234f said:**
> Tried the internet search and found Debian has a search
for files in packages webpage at:
[http://www.debian.org/distrib/packages](http://www.debian.org/distrib/packages)

at the bottom of the page.
Seems like ubuntu uses the same names, I guess.

Ubuntu has the same thing at [http://packages.ubuntu.com]("http://packages.ubuntu.com")

Also ```
dpkg -S /path/to/file
``` will tell you what package provides the file.

---

