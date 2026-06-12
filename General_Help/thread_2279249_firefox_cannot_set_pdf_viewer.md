---
title: "firefox: cannot set pdf viewer"
date: 2015-05-22
forum: General Help
---

### Post by fillemon on 2015-05-22
hello   got myself a problem that i can't fix...  

system: ubuntu 10.04lts
firefox 38   

when i click a pdf file in firefox:   
a) i can save them : problem:  when i want to open them for firefox it opens it with gimp...     (if i open them from nautilus : eviewer pops up and works great) 
 b)i can choose the option "open with"  there is only gimp as software, i can choose "other" but i cannot find the place where eviewer and adobe are stored.  

thanks fillemon  when

---

### Post by SeijiSensei on 2015-05-22
You can set the applications Firefox uses by choosing Edit > Preferences > Applications and selecting from the drop-down box next to the type of file.

Most every application is stored in /usr/bin.  I use Kubuntu which comes with the Okular PDF reader; it's stored as /usr/bin/okular.  To find a particular file's location use "which filename".  If you use "which acroread" it should return /usr/bin/acroread if it is installed.

I'd never use acroread, though.  It's been a major source of security problems on all platforms for some time now.  Firefox 38 comes with its own built-in PDF viewer which appears as "Preview in Firefox" in the drop-down box.

---

