---
title: "Change default for .doc (winword.exe)"
date: 2008-06-11
forum: General Help
---

### Post by terryeden on 2008-06-11
Hi All,

My parents refuse to learn how to use OpenOffice, so I've stuck Office 2000 on their machine using WINE.

The install works and they can edit docs etc.  However, the .doc filetype is still registered to OpenOffice.  How can I change it so that winword.exe gets run?

In the terminal I can type
```
wine "C:\Program Files\Microsoft Office\WINWORD.exe" /home/foo.doc
```
Which opens "foo.doc" in Word.

When I right click on a .doc and try to change the "Opens With..." to wine and the path to winword it says that it can't add it.

So, simple question.  How do I register wine and winword.exe as the prefered application for .doc files?

T

---

### Post by Tom--d on 2008-06-11
When selecting open with. is wine there?
If yes, select that.

And openoffice is better than office 2000. I suggest to make them use it :p

---

### Post by terryeden on 2008-06-11
That'll teach me to Google harder before I post!
According to [https://help.ubuntu.com/community/Wine#head-c65dfece90dfd8c4cf9ab68a10a7854e7c81bbe2](https://help.ubuntu.com/community/Wine#head-c65dfece90dfd8c4cf9ab68a10a7854e7c81bbe2)
I can create a script.  Is there a graphical way I can do it?

---

