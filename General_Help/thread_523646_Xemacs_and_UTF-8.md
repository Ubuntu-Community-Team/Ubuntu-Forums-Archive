---
title: "Xemacs and UTF-8"
date: 2007-08-12
forum: General Help
---

### Post by uwevoelker on 2007-08-12
Hello,

my locale is de_DE.UTF-8 and I installed xemacs-nomule.

Xemacs does not respect my locale, it inserts everything in ISO-8859-1 (or -15). How can I change that?

Installing the mule-Version did not help - there was no encoding "UTF-8" or similar. How can I get these encodings?


I'm using the 64bit version of Ubuntu 07.04.


Thank you very much,
good bye, Uwe

---

### Post by alex-v on 2007-08-21
First of all, in order to use Unicode in XEmacs you have to use MULE. So you need to install xemacs-mule.

Then, according to XEmacs FAQ

[http://www.xemacs.org/Documentation/21.5/html/xemacs-faq_2.html#SEC72]("http://www.xemacs.org/Documentation/21.5/html/xemacs-faq_2.html#SEC72")

```
(require 'un-define)
(set-coding-priority-list '(utf-8))
(set-coding-category-system 'utf-8 'utf-8)
```

will enable UTF-8 encoding in XEmacs.

---

### Post by Pierre Imbaud on 2008-01-28
Did you get any answer on this? Not on this forum, I guess.
I have different, but related problems: encoding systems, ubuntu,
xemacs. All this seems to have grown so complicated no one
masters the whole thing.

---

### Post by uwevoelker on 2008-01-28
My solution:
- use xemacs-nomule
- switch to ISO-8859-15 locale

It's not the way I wanted it to be, but it works :D

---

### Post by jobarjo on 2008-03-06
> **alex-v said:**
> First of all, in order to use Unicode in XEmacs you have to use MULE. So you need to install xemacs-mule.

Then, according to XEmacs FAQ

[http://www.xemacs.org/Documentation/21.5/html/xemacs-faq_2.html#SEC72]("http://www.xemacs.org/Documentation/21.5/html/xemacs-faq_2.html#SEC72")

```
(require 'un-define)
(set-coding-priority-list '(utf-8))
(set-coding-category-system 'utf-8 'utf-8)
```

will enable UTF-8 encoding in XEmacs.

This works just fine, thanks a lot!
Installing mule-ucs could help also.

---

