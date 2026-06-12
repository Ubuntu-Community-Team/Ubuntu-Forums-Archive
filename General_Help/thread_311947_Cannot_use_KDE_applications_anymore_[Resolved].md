---
title: "Cannot use KDE applications anymore [Resolved]"
date: 2006-12-03
forum: General Help
---

### Post by erdalronahi on 2006-12-03
I am running Ubuntu 6.10 with GNOME, but I used to work with KDE applications like Konqueror, Ktorrent and Kbabel also. Since yesterday I cannot start any KDE application anymore. If I try, the hard disk works, but nothing happens. The apps do not show up in the process list, too.

I uninstalled and reinstalled a lot of stuff, deleted the whole .KDE directory, but nothing helped.

Any idea, anyone?

---

### Post by aysiu on 2006-12-03
Can you post the output of this terminal command? ```
konqueror
```

---

### Post by erdalronahi on 2006-12-03
Sure:

```
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kdecore (KLocale): WARNING: Definition of PluralForm is none of NoPlural/TwoForms/French/OneTwoRest/Russian/Polish/Slovenian/Lithuanian/Czech/Slovak/Arabic/Balcan/Macedonian/Gaeilge/Maltese: Kurdish
kdeinit: Communication error with launcher. Exiting!
kdecore (KLocale): WARNING: Definition of PluralForm is none of NoPlural/TwoForms/French/OneTwoRest/Russian/Polish/Slovenian/Lithuanian/Czech/Slovak/Arabic/Balcan/Macedonian/Gaeilge/Maltese: Kurdish
```

Maybe it's due to the new langpack that came yesterday?

---

### Post by aysiu on 2006-12-03
Yeah, it does look locale-related... not sure what the solution is.

Unfortunately, [a Google search on the error](http://www.google.com/search?num=100&hl=en&lr=lang_en&safe=off&q=kdecore+%28KLocale%29%3A+WARNING%3A+Definition+of+PluralForm+is+none+of+&btnG=Search) doesn't turn up much.

---

### Post by erdalronahi on 2006-12-03
Removing language-pack-kde-ku and language-pack-kde-ku-base solved the problem. 

I had updated the language packs from the Martin Pitt's daily-langpack repository. After installing the "official" version it worked again. I will report this to the translators mailing list.

Strange, though, that the language pack should determine how KDE handles plurals, and that this should produce a bug.

Thanks for your help.

---

