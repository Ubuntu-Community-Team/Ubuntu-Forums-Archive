---
title: "multilingual support: dead keys and scim"
date: 2007-12-10
forum: General Help
---

### Post by jjatria on 2007-12-10
there are a number of other posts out there that deal with either the need for dead keys or the frustration of not knowing how to disable them. however, i deem my case to be particular enough to start a new thread, so here i go. sorry if this is old news, but i'm stumped, and starting to get annoyed.

i've been using different flavours of kubuntu ever since dapper, and with all of them i've used the same multilingual setting: the system is in english, i alternate the use of an english and a latin american keyboard layout, and i use scim to enter japanese text. this setup has worked flawlessly in every release i've used.

until gutsy.

here's my problem. i updated to kubuntu gutsy with a fresh install. i set up scim, and it worked like a charm (it was a lot easier to set up than before), but when i set the latin american layout, no matter what variant, the dead keys (like the ones needed to input á, é, í, ó, ú, etc...) did not work (depending on the keyboard layout variant, they either print ´a or just a instead of á, for example). i had this problem system-wide (on konsole, on openoffice, on kate, etc) i read up on some posts about dead key issues, and figured out it had to do with my locale, so i changed my /etc/environment to include the line ```
LC_CTYPE="es_ES.UTF8"
```, and to my surprise, that solved the dead keys: i can now input spanish accented characters and keep my system in english. scim, however, ceased to work (trigger hotkeys do not enable it nor is there any other way to enable anthy).

so far, i can survive with the current setup and restart X with different variations of /etc/environment every time i need to use either spanish or japanese, but since i tend to use this languages constantly, it won't be long before i lose it.

so here's my question: is there any way to enable the use of spanish dead keys with an all english locale setting, or enabling scim with an LC_CTYPE="es_ES.UTF8" one?

thanks a bunch.

---

### Post by jjatria on 2007-12-10
just in case anybody is interested, i noticed the locale setting was supposed to be es_ES.UTF-8 instead of es_ES.UTF8, so i changed it. but everything behaves the same.

i also thought that maybe i could modify the LC_CTYPE definitions in /usr/share/i18n/locales/en_US or /usr/share/i18n/locales/es_ES, but it turned out that both of them were exactly the same (or at least i think so): while en_US had

```
LC_CTYPE
copy "en_GB"
END LC_CTYPE
```

both es_ES and en_GB had

```
LC_CTYPE
copy "i18n"

translit_start
include "translit_combining";""
translit_end
END LC_CTYPE
```

i then thought that maybe commenting out the translit routine might help, but it didn't. so i reverted all those changes and await further enlightenment and/or suggestions.

---

