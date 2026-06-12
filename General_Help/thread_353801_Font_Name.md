---
title: "Font Name"
date: 2007-02-05
forum: General Help
---

### Post by mosestruong on 2007-02-05
Does anyone know how to set the font names? For example, the font "AR PL ShanHeiSun Uni"
in Windows, is referred to using its Chinese name "&#25991;&#40718;PL&#32048;&#19978;&#28023;&#23435; Uni", whereas in Ubuntu its name "AR PL ShanHeiSun Uni".

Are there any way to have the font referred to using its Chinese name?

---

### Post by pseudonym on 2007-02-05
Check that there's not some language support you haven't downloaded yet. FWIW, my system is in German and, while the font selector GUI in my user settings is in German, all the font names and descriptions are in English eg. 'bold', 'italic', 'Ouhod-Bold', 'Tlwg Typewriter' and so forth (though TBH I don't expect the font names to change, but the descriptions should).

I know I'm not missing any language support, so maybe the localisation team hasn't got around to changing this part of the system yet, at least as far as German and, as it looks, Chinese is concerned??

---

### Post by mosestruong on 2007-02-05
Found that this is listed as an unconfirmed bug in ubuntu [https://launchpad.net/ubuntu/+source/fontconfig/+bug/36564](https://launchpad.net/ubuntu/+source/fontconfig/+bug/36564)

I've downloaded fontconfig version 2.4.2-1 from Debian's testing repository - the fonts are now displayed using the correct names now.

---

