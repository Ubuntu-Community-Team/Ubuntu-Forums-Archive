---
title: "[SOLVED] Need Help with Music Track plugin for Pidgin"
date: 2007-09-15
forum: General Help
---

### Post by BillyBlue on 2007-09-15
I searched around and found this program
[http://code.google.com/p/musictracker/](http://code.google.com/p/musictracker/)
Downloaded it and want to install it in pidgin but I am not good at compiling and the simple how to ways I found on here aren't working.
I understand I have to move the download to my pidgin plugins but I do not know how.
Currently the download is on my desktop.
can anyone help me with a means to get it from there to my pidgin plugins?


Thank you in advance.

---

### Post by peabody on 2007-09-15
Does not compile with the gaim provided by feisty at least it didn't seem to with the ./configure script:

*** Pidgin 2.0+ is required to build MusicTracker; please make sure you have the
*** Pidgin development files installed. The latest version of Pidgin is always
*** available at [http://pidgin.im/](http://pidgin.im/).

Unless you're using gutsy (and I'm a assuming gutsy probably has pidgin instead of gaim, but I could be wrong) it probably won't work.  Of course, you could try an apt-get remove gaim and then attempt to install pidgin from source yourself, but I'd advise against that since it sounds like you have no experience.

---

### Post by gOLdenHaWK3D on 2007-10-29
MusicTracker does not compile with Gutsy either!
I have Ubuntu Gutsy Gibbon, and I downloaded the MusicTracker plugin from [http://code.google.com/p/musictracker/](http://code.google.com/p/musictracker/) 

Still no luck! :(

---

### Post by gOLdenHaWK3D on 2007-10-29
Sorry, my bad! Got it installed :P
Some PCRE development files were missing!

:guitar:

---

