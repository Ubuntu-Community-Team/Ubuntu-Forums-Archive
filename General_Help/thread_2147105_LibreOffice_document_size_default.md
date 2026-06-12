---
title: "LibreOffice document size default"
date: 2013-05-20
forum: General Help
---

### Post by newb85 on 2013-05-20
I'm in the U.S., so I'm among the few who use Letter sized paper, rather than A4 normally.  My printer (trusty ol' MFC-3360C) was automatically set up to use Letter paper as a default.  No problem there.  The trouble is, when I create a new document in LibreOffice, it defaults to A4.  Is there an easy way to change this?

---

### Post by Buntu Bunny on 2013-05-21
I don't know if this would make a difference, but out of curiosity, what are your language settings? 

Tools > Options  > Language Settings > Languages > Locale Setting

Are they in Default - English (USA)?

---

### Post by newb85 on 2013-05-21
The UI, Locale setting, and Western default language are all set to "Default - English (USA)".
Also my system-wide regional format is still set to "English (United States)".

Does LibreOffice not use a "Normal.ott" template file?  I would expect my problem to be a simple matter of altering that file.  However, for the life of me, I can't seem to find it.

---

### Post by schragge on 2013-05-21
Can't test it currently, but I'd expect the settings in
```
Format > Page > Page
``` to be remembered between different calls of LibreOffice.

---

### Post by Buntu Bunny on 2013-05-21
> **newb85 said:**
> Does LibreOffice not use a "Normal.ott" template file?  I would expect my problem to be a simple matter of altering that file.  However, for the life of me, I can't seem to find it.

You got me curious so I had a look. I couldn't find it either. 

If Schragge's suggestion doesn't work

> **schragge said:**
> [code]Format > Page > Page[/code.]

you could set up the size you want as a template, right click it in template management, then choose 'set as default template'.

---

### Post by Peter Maunder on 2013-05-21
The default Ubuntu (12.04) system wide papersize is held in the /etc/papersize file. Check that it is set to letter for American letter or A4 for A4.  The file length will be 3 for A4 and 7 for letter.

---

### Post by newb85 on 2013-05-22
@Schragge - Thank you!  That took care of it.

---

