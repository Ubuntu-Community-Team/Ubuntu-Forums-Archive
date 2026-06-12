---
title: "Adobe Reader does not substitute fonts correctly after upgrade"
date: 2008-05-24
forum: General Help
---

### Post by MAA1977 on 2008-05-24
Hello,

after upgrading to Xubuntu 8.04, Adobe Reader substitutes Helvetica with a serif font.

When a font is not embedded in the PDF to be displayed, Adobe Reader should substitute the missing font with a similar one. The font substitution used to work without problems until I upgraded to 8.04.

Under Xubuntu 8.04, Adobe Reader substitutes Helvetica with a serif font. As Helvetica is actually a sans serif font, this behavior is clearly wrong.

I suspect that the problem is somehow related to Xubuntu's font configuration, because the same version of Adobe Reader works correctly under Xubuntu 7.10. I guess that the problem occurs under other Ubuntu derivates as well, but I have not tested it.

Has anybody an idea?

Regards
Alexander

PS: I already installed a couple of font related packages (extra fonts, msttcorefonts, etc.), but the problem still remains.

---

### Post by MAA1977 on 2008-05-24
I fixed the problem on my own:

You have to edit the acroread script:

> sudo vim $(which acroread)

The following two lines should be uncommented (remove the leading #):

> ACRO_ENABLE_FONT_CONFIG=1
export ACRO_ENABLE_FONT_CONFIG

Afterwards, everything works correctly.

However, I wonder why it worked in 7.10 without those changes ...

---

### Post by andlun57 on 2009-02-20
Thanks for the tip. Worked for me as well.

---

### Post by area124 on 2010-07-29
Thanks much as this worked for me as well. I am running Ubuntu 9.10 and Adobe Reader 8.1.3.:popcorn:

---

