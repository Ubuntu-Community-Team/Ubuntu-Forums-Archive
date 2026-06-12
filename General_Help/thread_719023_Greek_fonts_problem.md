---
title: "Greek fonts problem"
date: 2008-03-08
forum: General Help
---

### Post by clueless on 2008-03-08
Hello to all!

I did something, I changed something, I have no idea what it was, while trying to get optimal fonts for my gtk and qt applications on KDE.

I use Kubuntu 8.04 in greek but I don't think it has anything to do with Ubuntu's version, that's why I am posting in general help.

The problem:
I can't put accents on greek vowels any more, something that I was able to do until I messed with the settings.
Before my intervention (normal behavior): typing first ";" and then "a" would result in "&#940;".
Now ";" gives me a " ' " and  "a" gives me an "&#945;".
But when I right click on the application where I am typing and select --> input method --> Simple Compositing Input Method (where the other two options that I have are XIM and SCIM) then I can type normaly. But I have to do this in every application, every time.

I had installed SKIM, to see what it was and messed around a bit with the settings, but then I uninstalled it, along with SCIM. But even after reinstalling it, I still cannot go back to how my system was before. 

Any suggestions?

---

### Post by clueless on 2008-03-08
Solved!

I uninstalled skim and scim and deleted the ~/.scim folder, logged out and back in and returned to normal.

Just posting the solution here in case somebody else has the same problem.

---

