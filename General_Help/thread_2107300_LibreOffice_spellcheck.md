---
title: "LibreOffice spellcheck?"
date: 2013-01-21
forum: General Help
---

### Post by foldered on 2013-01-21
Hi everyone,

Recently made the switch to running Ubuntu exclusively and so far it has been pretty nice, but I am running into some spellcheck issues with LibreOffice--it doesn't detect any!  This is pretty major for me as I am a student and work as a research assistant, which involves producing documents for others.  I am a good speller (haha), but type very quickly and often mix up letters, which can be difficult to notice immediately, so I do rely on spellcheck.

Anyone have similar issues and were able to fix it?  Thanks a lot!

---

### Post by Impavidus on 2013-01-21
My libreoffice spell checker works precisely for the languages I have installed (same sentence with errors in dutch, latin, german and english; only in dutch and english the errors are found). Have you checked the language settings? Libreoffice allows you to set the language to something it doesn't have a spell checker for (it even suggests the correct language, like latin in my case).

Furthermore, have you checked you have installed the dictionary files? You need the package hunspell and some language package named hunspell-<language code> or myspell-<language code>. It will fail if you request british english and only have canadian and us english installed.

---

### Post by foldered on 2013-01-21
> **Impavidus said:**
> Have you checked the language settings? Libreoffice allows you to set the language to something it doesn't have a spell checker for (it even suggests the correct language, like latin in my case).

Furthermore, have you checked you have installed the dictionary files? You need the package hunspell and some language package named hunspell-<language code> or myspell-<language code>. It will fail if you request british english and only have canadian and us english installed.
I messed around with the language settings a bit and did manually install a myspell-OED of some sort.  It seems to pick things up now if I run a check, but not as I type.  It isn't imperative that I get it to work as I type, but it would be much more convenient. 
Thanks for responding!

---

