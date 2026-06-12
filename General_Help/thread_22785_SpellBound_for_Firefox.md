---
title: "SpellBound for Firefox"
date: 2005-03-29
forum: General Help
---

### Post by ola on 2005-03-29
Hi

I have tried to install [SpellBound](http://spellbound.sourceforge.net/) for Firefox through their website but It seems to be impossible..

Is there any proper way to install it?

Regards

Ola

---

### Post by XarayaGeek on 2005-03-29
[QUOTE=ola]Hi

I have tried to install [SpellBound](http://spellbound.sourceforge.net/) for Firefox through their website but It seems to be impossible..

Is there any proper way to install it?
[/QUOTE]

The way I got it to install was to first run firefox from the console as root

sudo firefox

Then I installed the libraries and dictionary from there,

Next run firefox as regular user and just install the Spellbound Extension from here ->  [http://exchangecode.com/spellbound/downloads/spellbound-0.7.3.xpi](http://exchangecode.com/spellbound/downloads/spellbound-0.7.3.xpi)

thats all you need to install as the regular user since it uses the extensions and dictionary from from the earlier install.

---

