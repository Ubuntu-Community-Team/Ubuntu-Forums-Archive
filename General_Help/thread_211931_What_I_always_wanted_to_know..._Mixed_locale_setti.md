---
title: "What I always wanted to know... Mixed locale settings?"
date: 2006-07-09
forum: General Help
---

### Post by matthias_k on 2006-07-09
Hi guys,

do you know where/how I can globally set the locale such that everything is set to my country specifics (e.g. currency, metrics, ...) *except* the GUI language, and the language of system notifications?

The reason is this: Right now, I have set everything to en_US.UTF-8, because I prefer a user interface in English, but then I get all the inconvenient side effects, like English spellchecks in OpenOffice (I usually write in German in OO.org), or US metrics in GIMP (e.g. inch instead of centimeters).

When I dpkg-reconfigure locale I can only set *everything* to German, but that's not what I want. Especially, I don't want to manually set every single tool seperately to a German locale.

Any ideas? I know there are env-vars I can set, but where would I do this to apply globally, and which one is responsible for system output and GUI text?

Thanks!

---

### Post by matthias_k on 2006-07-09
Meh, I think I have found it myself...

It seems I have to set the variable LANGUAGE (or LC_MESSAGES, it seems the former overwrites the latter) to en_US.UTF-8 and LC_ALL to de_DE.UTF-8 in the file /etc/environment. Is that the location where all global env-vars are set? It was empty on my system.

---

