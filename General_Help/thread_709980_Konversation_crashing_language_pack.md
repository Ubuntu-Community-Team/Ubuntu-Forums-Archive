---
title: "Konversation crashing? language pack?"
date: 2008-02-28
forum: General Help
---

### Post by Sonja on 2008-02-28
I get this error:

sonja@sonja:~$ konversation
kdecore (KLocale): WARNING: Definition of PluralForm is none of NoPlural/TwoForms/French/OneTwoRest/Russian/Polish/Slovenian/Lithuanian/Czech/Slovak/Arabic/Balcan/Macedonian/Gaeilge/Maltese: Definition of PluralForm - to be set by the translator of kdelibs.po
kdeinit: Communication error with launcher. Exiting!
kdecore (KLocale): WARNING: Definition of PluralForm is none of NoPlural/TwoForms/French/OneTwoRest/Russian/Polish/Slovenian/Lithuanian/Czech/Slovak/Arabic/Balcan/Macedonian/Gaeilge/Maltese: Definition of PluralForm - to be set by the translator of kdelibs.po
DCOP aborting call from 'anonymous-29380' to 'konversation'
ERROR: Communication problem with konversation, it probably crashed.

How do I fix0r it? :( :(

---

### Post by Sonja on 2008-02-28
I even went in System > Admin > Language support and uninstalled every non-English language, rebooted, and still get the crash. :(

---

### Post by Sonja on 2008-02-28
Somebody told me this:

A recent update broke some KDE language packs, leaving the user unable to login. ([http://launchpad.net/bugs/195647](http://launchpad.net/bugs/195647)) To fix this, remove the updated packages (language-pack-kde-en, language-pack-kde-en-base) and restart KDE.

---

