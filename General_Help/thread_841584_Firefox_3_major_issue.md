---
title: "Firefox 3 major issue"
date: 2008-06-26
forum: General Help
---

### Post by thomsany on 2008-06-26
Hey guys!!
I was using my Firefox 3 without problems until now.
Evertime I open up firefox, it does not go to my homepage. 
The buttons are not working at all (Back, forward, stop, refresh).
The icons for the bookmarks, etc are gone completely.
The status bar is blank.

Also when I enter a link, firefox usually changes it to the full http... link. That does not happen. I can't see the accessed websites when I click on the down arrow on the address field. Nothing is there.

I tried removing firefox 3 and reinstalling with no luck.
Still the same problem.
Any suggestions?

Thanks much,
Teo

---

### Post by NT4usB on 2008-06-26
Sounds like your profile is corrupted.
Uninstalling doesn't touch the profile so reinstalling won't change anything.
Your profile is in your home folder...
.mozilla or .firefox or .something in a folder called profiles, random foldername like gcim354c.default

Create a new profile:```
$firefox -p (or -ProfileManager or something)
```
Then you can copy over bookmarks, etc. until it breaks or just use it.
See if it works, anyway.

---

### Post by thomsany on 2008-06-26
Ok I solved it.. 
Here is the issue that was happening.
I ran firefox as root once and when I closed the window, Firefox asked me if I wanted to save the opened tabs, etc. I chose yes by mistake.
When I ran firefox as my user, I would get the error.
After I did everthing I tried once logging in as root into firefox and I found out that it prompted me to restore the previous versions.
After that I closed everything and restarted firefox and everything went back to normal.

Hope this helps whoever runs into this issue again.

Regards,
Teo

---

### Post by cnr437 on 2008-06-26
u could remove hidden profile directory of "~/.mozilla/firefox"

---

