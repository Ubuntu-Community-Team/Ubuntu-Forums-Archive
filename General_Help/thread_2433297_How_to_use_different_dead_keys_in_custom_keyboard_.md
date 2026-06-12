---
title: "How to use different dead keys in custom keyboard layout"
date: 2019-12-17
forum: General Help
---

### Post by aik099 on 2019-12-17
Hi,

I'm creating custom keyboard layout to replicate behavior of LetterZu app on the Windows, that allow:

* typing "zh" will produce "&#1078;" (the "z" being a dead key, but pressing z+space will show "&#1079;")
* typing "sh" will produce "&#1096;" (the "s" being a dead key, but pressing s+space will show "&#1089;")
* typing "sx" will produce "&#1097;" (the "s" being a dead key, but pressing s+space will show "&#1089;")
* typing "yo" will produce "&#1105;" (the "y" being a dead key, but pressing y+space will show "&#1099;")
* typing "jo" will produce "&#1105;" (the "j" being a dead key, but pressing j+space will show "&#1081;")

Basically you type transliterated text without need to use Compose key and it's converted to Cyrillic text on the fly. The "phonetic" keyboard layouts, as far as I can tell, doesn't support that at the moment.

What should I change in "[COLOR=#000000][FONT=monospace]/usr/share/X11/xkb/symbols/ru" file (say "Russian (phonetic)" layout) to make this work as described?


Thank you.[/FONT][/COLOR]

---

