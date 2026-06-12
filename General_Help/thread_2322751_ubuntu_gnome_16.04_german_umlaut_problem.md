---
title: "ubuntu gnome 16.04 german umlaut problem"
date: 2016-04-30
forum: General Help
---

### Post by ya-paulle on 2016-04-30
in ubuntu gnome 16.04 german umlaute like ü, ä etc aren't properly displayed in the copy paste menues of nautilus and libreoffice.[ATTACH=CONFIG]268731[/ATTACH]

any help?

---

### Post by peter228 on 2016-05-01
So you are using English language as the normal default language for your system?  I looked at your screen capture and got the idea that may be the case.

If that is the case have you also enabled support for the German language?   (System Settings / Language Support / Install Remove Languages)

---

### Post by peter228 on 2016-05-01
Just had another thought ......   I assume that the fonts you have installed will support umlaute and related characters?

---

### Post by ya-paulle on 2016-05-01
> **peter228 said:**
> So you are using English language as the normal default language for your system?  I looked at your screen capture and got the idea that may be the case.

If that is the case have you also enabled support for the German language?   (System Settings / Language Support / Install Remove Languages)

I don't use English as default, and German is installed in system settings.

---

### Post by ya-paulle on 2016-05-01
> **peter228 said:**
> Just had another thought ......   I assume that the fonts you have installed will support umlaute and related characters?

I'm using the fonts Cantarell und ubuntu, both have 'Umlaute'.
[ATTACH=CONFIG]268747[/ATTACH][ATTACH=CONFIG]268748[/ATTACH]

---

### Post by peter228 on 2016-05-02
Saddened to hear that there is no progress.  Please explore further ........ 

In LibreOffice, have you set your language preferences to include German?    (Tools / Options / Language Settings / Languages)

In Ubuntu System Settings, what languages have you selected for text entry?  (System Settings / Text Entry)

---

### Post by QIII on 2016-05-02
Hello!

So you can't paste an Umlaut in menus, but can you in the text of an LO document?

Can you use the character map to place ä, ö or ü in the text of a document?

---

### Post by ya-paulle on 2016-05-02
I got the 'Umlaut'-problem solved. The problem is only with the font Cantarell. I switched to another font and the problem is gone. It seems Cantarell is borked, at least one is using the gnome-staging-ppa too.
Thank you all for help.

---

