---
title: "alphabet issues - Cyrillic Latin"
date: 2014-12-11
forum: General Help
---

### Post by alek5a on 2014-12-11
at the beginning seem interesting to give a familiar Cyrillic alphabet a go but having issue with certain programs reading folder names and files. any solution to make it readable or just get back to English alphabet[IMG]https://m.ak.fbcdn.net/sphotos-h.ak/hphotos-ak-xpf1/v/t34.0-12/10427995_860282067364631_1572600414928085206_n.jpg?oh=af7151cb8dc133ad3a7fa22ebbbcfa4c&oe=548D70B3&__gda__=1418495372_5ab94cc860e887c1a7863980b8072497[/IMG]

---

### Post by grahammechanical on 2014-12-11
When you installed this operating system what language did you chose to be default? How did you change to this other language? Surely, you can go to System Settings>Language Support and there Install/Remove Languages. Did you remove the English Language? If not then surely all you need to do is "Drag languages to arrange in order of preference - Changes take effect next time you log in."

Regards.

---

### Post by schragge on 2014-12-12
Filenames on your disk are encoded in UTF-8, while the program you're opening them with (is it Adobe Fireworks?) seems to expect them to be encoded in ISO 8859-5. Thus, &#1064;&#1072;&#1073;&#1083;&#1086;&#1085;&#1080; (Templates) gets displayed as &#1072;&#1032;&#1072;&#1040;&#1072;&#1041;&#1072;&#1051;&#1072;&#1054;&#1072;&#1053;&#1072;&#1048;.

You need to select correct encoding for Windows programs launched through wine.

Hopefully [this]("http://unix.stackexchange.com/questions/38876/how-to-fix-russian-letters-in-a-wine-application-when-adjusting-lang-does-not-he") could be of some help. There's also [thread=665485]this old thread[/thread].

You can also directly specify encoding when launching the program. Something like
```

LANG=sr_CS.UTF-8 wine Fireworks.exe

```
With full path specified it looks like
```

LANG=sr_CS.UTF-8 wine ~/'.wine/drive_c/Program Files (x86)/Adobe/Adobe Fireworks CS6/Fireworks.exe'

```

---

### Post by alek5a on 2014-12-12
Thanks for bouth advice . Got it back to English. One interesting thing happened tho . My main folders doubled . Have old one in Cyrillic and same in English. :popcorn:

---

