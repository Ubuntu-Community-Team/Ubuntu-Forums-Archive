---
title: "gaim-libnotify and Pidgin?"
date: 2007-04-15
forum: General Help
---

### Post by Protoss on 2007-04-15
I was wondering if anyone has gotten [gaim-libnotify]("http://gaim-libnotify.sourceforge.net/") working with Pidgin 2.0B7. I've tried to do some little patches to make it use the new gaim-compat.h library, but I know absolutely nothing about C++. Every time I try to make, I get ```
gaim-libnotify.c:556: warning: type defaults to 'int' in declaration of 'PURPLE_INIT_PLUGIN'
gaim-libnotify.c:556: warning: parameter names (without types) in function declaration

``` so I'm thinking in my 'patching', really screwed something up.
If someone could please make it work, that would be great, as I am having a hard time living without this plugin.

---

### Post by ButteBlues on 2007-04-16
Could you show us what is in lines 550 - 560?

---

### Post by huwshimi on 2007-05-05
I have ported it over to Pidgin.

I'm hoping to get my changes merged with the official version (I have not received any response from the developers yet), but until that happens you can help test the new code here: [http://huw.ugbox.net/dev/squawk/]("http://huw.ugbox.net/dev/squawk/")

Cheers.

---

### Post by Laterix on 2007-05-06
> **xi0nblue said:**
> I have ported it over to Pidgin.
Thank you for doing this. I installed it to Feisty and it seems to work well with Pidgin.

---

### Post by Protoss on 2007-05-06
Sweet thanks! I managed to hack my way to making it work with Pidgin, but it was very messy.

---

