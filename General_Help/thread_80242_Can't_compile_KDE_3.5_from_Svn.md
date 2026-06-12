---
title: "Can't compile KDE 3.5 from Svn"
date: 2005-10-21
forum: General Help
---

### Post by ragol on 2005-10-21
Hi!

After upgrading to Breezy, I can't compile KDE 3.5 from Svn anymore. It seems that some libraries broke down (or something else) during upgrade. Here's the output of make in kdelibs:

grep: /usr/lib/libXrender.la: No such file or directory
/bin/sed: can't read /usr/lib/libXrender.la: No such file or directory
libtool: link: `/usr/lib/libXrender.la' is not a valid libtool archive

And here's the output in kdebase:

grep: /usr/lib/libXcursor.la: No such file or directory
/bin/sed: can't read /usr/lib/libXcursor.la: No such file or directory
libtool: link: `/usr/lib/libXcursor.la' is not a valid libtool archive

So, before the upgrade I was able to compile it, but not anymore. *sigh* And it seems that there is some other problems with rendering, too: [http://ragol.kattila.org/kongueror_with_bugs.png](http://ragol.kattila.org/kongueror_with_bugs.png) And this too started after I had done the upgrade.

Any ideas or thoughts are welcome. 

-- 
Olli Rajala <><
Tampere, Finland

---

### Post by Seth on 2005-10-21
[quote=ragol]Hi!

After upgrading to Breezy, I can't compile KDE 3.5 from Svn anymore. It seems that some libraries broke down (or something else) during upgrade. Here's the output of make in kdelibs:

grep: /usr/lib/libXrender.la: No such file or directory
/bin/sed: can't read /usr/lib/libXrender.la: No such file or directory
libtool: link: `/usr/lib/libXrender.la' is not a valid libtool archive

And here's the output in kdebase:

grep: /usr/lib/libXcursor.la: No such file or directory
/bin/sed: can't read /usr/lib/libXcursor.la: No such file or directory
libtool: link: `/usr/lib/libXcursor.la' is not a valid libtool archive

So, before the upgrade I was able to compile it, but not anymore. *sigh* And it seems that there is some other problems with rendering, too: [http://ragol.kattila.org/kongueror_with_bugs.png]("http://ragol.kattila.org/kongueror_with_bugs.png") And this too started after I had done the upgrade.

Any ideas or thoughts are welcome. 

-- 
Olli Rajala <><
Tampere, Finland[/quote] This is caused by a library transition. I had the exact same problem this summer when trying to compile some Qt apps. Get the ubuntu-specific KDE diffs and apply them against SVN.

---

### Post by ragol on 2005-10-22
[QUOTE=Seth]This is caused by a library transition. I had the exact same problem this summer when trying to compile some Qt apps. Get the ubuntu-specific KDE diffs and apply them against SVN.[/QUOTE]

Oh, thanks for the info. It would be nice to know where to get those diffs, though. I tried some googling, but without a success. But that just can mean, that I don't know how to do it. :)

So, if someone could tell me the right place where to look at, I would be very grateful.

-- 
Olli Rajala <><
Tampere, Finland

---

