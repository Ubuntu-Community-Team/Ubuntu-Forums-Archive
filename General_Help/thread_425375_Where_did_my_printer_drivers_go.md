---
title: "Where did my printer drivers go?"
date: 2007-04-27
forum: General Help
---

### Post by Astro96 on 2007-04-27
I recently reformatted my Edgy partition and installed Feisty.

In Edgy it seemed like there were printer drivers for practically everything, but not so in Feisty.  I'm trying to use a Ricoh Aficio 3228 (and a few similar to it).  The drivers were all there in Edgy, but not so in Feisty!

Where did they go?  More importantly, how can I get them back?

Thanks,
Andy

---

### Post by Astro96 on 2007-04-29
I figured it out -- I needed to install the openprinting-ppds-extra package:

```
sudo apt-get install openprinting-ppds-extra
```

---

### Post by organica on 2007-04-30
> **Astro96 said:**
> I figured it out -- I needed to install the openprinting-ppds-extra package:

```
sudo apt-get install openprinting-ppds-extra
```

Thanks!  Mine were missing too..

---

