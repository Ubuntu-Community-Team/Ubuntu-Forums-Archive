---
title: "Ubuntu and Firefox 3 startup problem"
date: 2008-06-16
forum: General Help
---

### Post by Baasha on 2008-06-16
Running Ubuntu Hardy on an i386 platform.

Ever since I upgraded to Hardy I have a problem starting Firefox.  The Firefox icon on my desktop will start the program ok, but if I select Applications>Internet>Firefox or press the Web/Home button on my keyboard (configured with Keytouch) I get an error message that tells me there is no such file or directory.  How do I alter the properties in the Applications menu to point to Firefox 3 and what would the correct path be?

---

### Post by Happy_Man on 2008-06-16
Hm, right-click on your menu, say "edit menus", go to the Internet section in Applications, right-click on firefox, say "properties", and make sure the command there is either ```
firefox-3.0
``` or ```
firefox
``` or ```
/usr/bin/firefox
``` or ```
/usr/bin/firefox-3.0
```. If it's not, add one of those in, and see if it works.

---

