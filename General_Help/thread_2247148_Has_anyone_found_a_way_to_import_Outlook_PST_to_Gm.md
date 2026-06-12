---
title: "Has anyone found a way to import Outlook PST to Gmail on Ubuntu desktop?"
date: 2014-10-06
forum: General Help
---

### Post by carmen2012 on 2014-10-06
My Windows PC failed some time back but I had a copy of a PST file of my Outlook email.

Does anyone know of a way to import this Outlook PST file to Gmail on an Ubuntu desktop?

Thank you

---

### Post by T.J. on 2014-10-06
[https://tools.google.com/dlpage/outlookmigration](https://tools.google.com/dlpage/outlookmigration) Assuming of course you have a Windows machine to use for a few minutes.  Probably the fastest way.

---

### Post by carmen2012 on 2014-10-06
> **T.J. said:**
> [https://tools.google.com/dlpage/outlookmigration](https://tools.google.com/dlpage/outlookmigration) Assuming of course you have a Windows machine to use for a few minutes.  Probably the fastest way.

I did load this on a spare Windows machine, but it didn't work for me.  When I did a bit digging, this isn't a public tool available for the masses but rather, it is a tool that has been released for enterprise customers who pay a monthly fee ( [http://www.google.com/enterprise/apps/business/pricing.html](http://www.google.com/enterprise/apps/business/pricing.html) )

Is there any other way to import a PST file into GMAIL?

---

### Post by amanchesterman on 2014-10-06
A quick search on Google indicates that there is a linux utility **readpst **which can convert .pst files to the more common .mbox format. You can then import the mail into Evolution or Thunderbird. I don't know what you mean by 'gmail on Ubuntu desktop' -- do you mean you are using the Gmail web interface in your web browser?

---

### Post by tgalati4 on 2014-10-06
There is also *pst-utils*.  Haven't used it.

```
apt-cache search pst
```

---

