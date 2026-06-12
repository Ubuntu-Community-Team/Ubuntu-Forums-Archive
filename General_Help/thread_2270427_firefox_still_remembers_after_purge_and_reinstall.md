---
title: "firefox still remembers after purge and reinstall"
date: 2015-03-22
forum: General Help
---

### Post by haplorrhine on 2015-03-22
Firefox leaves the luancher bar when I purge it with apt-get, yet it remembers everything -- add-ons, history, etc. -- once I reinstall it.  I've tried purging it from a virtual console.  In fact, I just purged it from tty1 while typing this, and it only gave me a notice that I should restart the browser.
I tried tightening its AppArmor permissions to disable it, and it disabled accordingly.

How would I check its downlaod mirror?

---

### Post by Yellow Pasque on 2015-03-22
Purging the package gets rid of system-wide configuration, but the user's mozilla profile remains.
If you're sure you want to start with a clean profile:
```
cd ~/
mv .mozilla .mozillabak
```

---

### Post by haplorrhine on 2015-03-23
That did it.  Thank you.

by the way, what are the files titled ~/.mozilla/firefox/........\.default

---

### Post by Yellow Pasque on 2015-03-23
[https://support.mozilla.org/en-US/kb/profiles-where-firefox-stores-user-data?redirectlocale=en-US&redirectslug=Profiles](https://support.mozilla.org/en-US/kb/profiles-where-firefox-stores-user-data?redirectlocale=en-US&redirectslug=Profiles)

---

### Post by deadflowr on 2015-03-23
> **haplorrhine said:**
> That did it.  Thank you.

by the way, what are the files titled ~/.mozilla/firefox/........\.default

Those are the actual profile folders.
You can remove,rename or even delete profiles with the command from a terminal or run dialog box:
```
firefox -ProfileManager
```
cool thing is the same -ProfileManager command is applicable to thunderbird.

The settings for which ever profiles you setup are stored in the profile.ini file.
Typically name, path, isrelative, and whether or not it is set as the default/the one that opens when you launch firefox/thunderbird.

---

