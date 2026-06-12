---
title: "A4 as default paper size for ps2pdf"
date: 2008-01-03
forum: General Help
---

### Post by engine on 2008-01-03
Well, as a good European I've already set my default paper size to A4. Alas, this doesn't seem to be having any effect on ps2pdf, which is resolutely sticking to US Letter.

It's been a long time since I had to struggle with this, and I haven't managed to find out how. Hints and tips appreciated!

tia

---

### Post by mali2297 on 2008-01-03
Try this
```

ps2pdf -sPAPERSIZE=a4 yourfile.ps

```
(From the man page of gs.)

---

### Post by engine on 2008-01-06
Thanks for the "one-off" tip.

I've also checked and found the full answer: despite the fact I specified a European location, language and keyboard while installing 7.10, /etc/papersize was still blandly set to "letter". Not good <g>

---

### Post by mali2297 on 2008-01-06
> **engine said:**
> Thanks for the "one-off" tip.

I've also checked and found the full answer: despite the fact I specified a European location, language and keyboard while installing 7.10, /etc/papersize was still blandly set to "letter". Not good <g>

Interesting. I've got the word a4 in /etc/papersize by default (Ubuntu 7.04, Swedish locale).

Check
```

locale

```
I have the variable LC_PAPER="sv_SE.UTF-8" listed.

Did you solve the problem by editing the file /etc/papersize?

---

