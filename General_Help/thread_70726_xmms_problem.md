---
title: "xmms problem"
date: 2005-10-01
forum: General Help
---

### Post by pibar on 2005-10-01
I have installed xmms but it crases everytime i open a mp3 file.My  default language is greek and when i try to open preferences i can read nothing but symbols.Any idea?

---

### Post by nike984 on 2005-10-01
[QUOTE=pibar]I have installed xmms but it crases everytime i open a mp3 file.My  default language is greek and when i try to open preferences i can read nothing but symbols.Any idea?[/QUOTE]
I don't use XMMS, so I can't tell you how to change the locale in XMMS 
but your problem usually happens with two reason as I know.
First,  Enable Alsa soft-mixing as described in post 
[http://www.ubuntuforums.org/showthread.php?t=32063&highlight=howto](http://www.ubuntuforums.org/showthread.php?t=32063&highlight=howto)
Second, If the mp3 player can't read the file name tag which's written in UTF-8 or in other locale, it usually crash. This is the method that I used in BMP.
```
Preferences dialog> Plugins > Media > MPEG Audio Plugin > 
Preferences > Title ;In the "ID3 Tags" configuration dialog, 
enable "Convert non-UTF8 ID3 tags to UTF8" and  enter the encoding
(codeset) name  in the "ID3 encoding" input box.  
For example, "CP1251" is a commonly used Cyrillic encoding. 

```

---

