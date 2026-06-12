---
title: "Libreoffice insisting on replacing &quot;to&quot; with &quot;HP&quot;"
date: 2013-04-16
forum: General Help
---

### Post by welshmike on 2013-04-16
Running 12.04 when I'm using LibreOffice Writer 3.5.7.2 to type a document and enter the word to , it immediatey gets replaced by the word HP .
Everything else I type seems to be OK.
What is going wrong?

---

### Post by llamabr on 2013-04-16
That's annoying.  You could turn off auto correct:

[https://help.libreoffice.org/Writer/Turning_Off_AutoCorrect](https://help.libreoffice.org/Writer/Turning_Off_AutoCorrect)

Otherwise, this is a libreoffice question, not an ubuntu one, so if no one else can help here, you might try taking this question to their forum.

---

### Post by r.stiltskin on 2013-04-16
Sorry if this suggestion is too obvious, but have you looked at your autocorrect "replace" rules?  Click on Tools->AutoCorrect Options and under the Replace tab you'll find a list of Replace/With pairs.  Look for
```
to      HP
```
and if you find an entry like that, select and delete it.

---

### Post by welshmike on 2013-04-17
> **r.stiltskin said:**
> Sorry if this suggestion is too obvious, but have you looked at your autocorrect "replace" rules?  Click on Tools->AutoCorrect Options and under the Replace tab you'll find a list of Replace/With pairs.  Look for
```
to      HP
```
and if you find an entry like that, select and delete it.
Thank you. I did find that and have now deleted that replacement. How it got there I do not know.

---

### Post by welshmike on 2013-04-17
> **llamabr said:**
> That's annoying.  You could turn off auto correct:

[https://help.libreoffice.org/Writer/Turning_Off_AutoCorrect](https://help.libreoffice.org/Writer/Turning_Off_AutoCorrect)

Otherwise, this is a libreoffice question, not an ubuntu one, so if no one else can help here, you might try taking this question to their forum.
My apologies for posting on a wrong forum. However the solution kindly has been provided in this forum by r.stiltskin.

---

