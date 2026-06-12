---
title: "Firefox  Issue"
date: 2007-03-27
forum: General Help
---

### Post by OracleUK on 2007-03-27
Hi,

Wonder if anyone can help, jut come back from a 2 day break booted up opened FireFox and all the settings and bookmarks have gone!!!!  I now cant add any bookmarks! where have they gone I haven't updated it at all or added any plugins.

Cheers.

---

### Post by 1/0 on 2007-03-27
Is your drive full (df -h)? What's in .mozilla?

---

### Post by OracleUK on 2007-03-27
No drive isnt full.

in .mozilla we have,

default
firefox
plugins
appreg
mozver.dat
pluginreg.dat

Thanks

---

### Post by OracleUK on 2007-03-27
Please can anyone help?

---

### Post by 1/0 on 2007-03-27
First, make a safety copy of .mozilla (cp -r). Then move .mozilla and start firefox. A clean firefox should be started. Copy your bookmarks that was in .mozilla/firefox/xxxxxxxx.default/bookmarks.html replacing the new one. 

You'll need to reinstall the add-ons. Maybe there's an easier way of doing this but this is the only one I can think of at the time. You got a copy of .mozilla so you can always go back.

---

### Post by strabes on 2007-03-27
firefox --ProfileManager

---

