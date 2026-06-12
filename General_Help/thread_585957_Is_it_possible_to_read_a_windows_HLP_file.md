---
title: "Is it possible to read a windows HLP file?"
date: 2007-10-21
forum: General Help
---

### Post by Eric the Grey on 2007-10-21
I have a windows help file (HLP) under Ubuntu but I've not been able to find an application to open it up with.  

I found the following thread, and it offers one suggestion (xCHM) but it doesn't work with HLP format, which I believe is an older version (Win95/98 era).

[http://ubuntuforums.org/showthread.php?t=322425&highlight=windows+hlp+files](http://ubuntuforums.org/showthread.php?t=322425&highlight=windows+hlp+files)

I've also found helpdeco, which is suppose to be able to decompile one, but it doesn't seem to work and I only get a single page RTF file, and a bitmap.

Any suggestions on how to read this?  Wine of course doesn't open it up because it's not an executable, although the application it's for runs fine.


:cool: Eric the Grey

---

### Post by radimvice on 2008-01-24
I'm currently searching for an answer to this problem. So far, I've been able to read my file in Wine using "wine winhelp" and loading the .HLP file from the UI, which should be fine if you just want to read the contents. But it seems that some people haven't even been able to get that working. Since I would really like to convert my file to a more flexible format, I'm going to try looking around for a .HLP to .CHM format converter as my next strategy.

---

### Post by radimvice on 2008-01-24
I found a linux command-line program called "HLP2RTF" that worked to convert and properly format my .HLP file.

---

### Post by Eric the Grey on 2008-01-24
> **radimvice said:**
> I'm currently searching for an answer to this problem. So far, I've been able to read my file in Wine using "wine winhelp" and loading the .HLP file from the UI, which should be fine if you just want to read the contents. But it seems that some people haven't even been able to get that working. Since I would really like to convert my file to a more flexible format, I'm going to try looking around for a .HLP to .CHM format converter as my next strategy.

That doesn't work for me.  I suspect it's due to the age of the help file.  For the most part, I've given up on using it and gone to using a web-based file instead.  The company who put this software out made several ways to read through the books in question, but the help file was the easiest because of the search function.

I've not tried HLP2RTF, but I might give it a shot if I can remember to install it.



:cool: Eric the Grey

---

