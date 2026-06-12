---
title: "Ubuntu Web Browser appearing when not desired"
date: 2014-06-11
forum: General Help
---

### Post by jeff63 on 2014-06-11
I use Firefox as my browser, and Konsole as my terminal emulator. Konsole offers both clicking of links that appear in terminal, and a right-click websearch. Both of these used to use Firefox, but as of today (and I think a system update, I wasn't really paying attention), these links now open up a new 'Ubuntu Web Browser', which is not desired.

The system default browser (from applications/system tools/system settings/details), $BROWSER and sensible-browser all yield firefox. Konsole doesn't seem to have a setting for which browser to use.

Any suggestions how this happened and how I should resolve it?

---

### Post by mc4man on 2014-06-11
If you are not using unity-webapps then simply remove webbrowser-app as it has no other use in 14.04 other than a semi-functional curiosity.
(- gnome-terminal works fine here, opens links in default browser

---

### Post by jeff63 on 2014-06-12
Removing webbrowser-app resolved the issue. Thanks.

This is something that should probably be resolved in a neater way for future releases.

---

