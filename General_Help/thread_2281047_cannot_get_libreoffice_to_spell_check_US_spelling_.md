---
title: "cannot get libreoffice to spell check US spelling variants -'mom', 'color' etc."
date: 2015-06-04
forum: General Help
---

### Post by jim50 on 2015-06-04
Hi all,

So this has driven me mad for a while, but now my kids are using libreoffice, it could become a deal breaker.

I've set every option I can find in libre office to english UK, and I know it is half working: 'recognize' 'analyze' all come up as spelled incorrectly, however words like 'mom' and 'color' still get through the spell-checker.

I have gone to tools and options and language settings and set all the feilds to english UK
i have gone to tools and options and writing aids and set the language in the spellcker to UK and restarted the computer
I have gone to /etc/defaults/locale and made sure en_GB is defaul
I have gone to /var/lib/locales/supported.d/ and commented out every non en_GB entry in both documents

any ideas?

---

### Post by mc4man on 2015-06-04
It definitely works as you want here by simply switching 3 options as in scr. 1, then re-opening Lo. Maybe try setting those 3 options to another english, close, re-open & set back to uk, ect.

Or - is it possible because some work, some don't that someone either set the non working to ignore or added them. Don't know how to ck. that, maybe try a guest session.

Edit: ck for a custom dict. as in Lo help, scr.3
> Tools - Options - Language Settings - Writing Aids.
Select the user-defined dictionary that you want to edit in the User-defined list, and then click Edit.
Select the word that you want to delete in the Word list, and then click Delete.

---

