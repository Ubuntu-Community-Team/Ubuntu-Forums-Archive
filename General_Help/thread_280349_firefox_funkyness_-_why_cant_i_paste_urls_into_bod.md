---
title: "firefox funkyness - why cant i paste urls into body"
date: 2006-10-19
forum: General Help
---

### Post by destro on 2006-10-19
with ubuntu firefox i cannot simply just grab a url text and paste it into the body of the firefox window and open the url automatically.

in a standard (non ubuntu) install i can do this feature.

is this something turned off in ubuntu's version of firefox or an option in firefox... in all honesty i don't even know what to call it.

---

### Post by metalheart on 2006-10-19
URL as a text or as a URL [http://www.ubuntu.com]("http://www.ubuntu.com") The latter is working fine for me (click on the link and drag to the address bar or on tab bar).

---

### Post by destro on 2006-10-19
no literally taking text i have copied and pasting it into the body section.  like clicking the center mouse button and it pasting the url or a search term for google.

---

### Post by metalheart on 2006-10-19
I guess Firefox in Ubuntu is missing something? [http://kb.mozillazine.org/Keyconfig_extension:_Firefox](http://kb.mozillazine.org/Keyconfig_extension:_Firefox) has Paste and Go function.

---

### Post by chizang on 2008-03-24
Navigate to about:config

Find the setting for middlemouse.contentLoadURL, and set it to 'true'.

That should fix it for you.

---

