---
title: "Enable Unicode Character 'SMASH PRODUCT' (U+2A33) on my system"
date: 2016-11-03
forum: General Help
---

### Post by GwibberFooey on 2016-11-03
How can I enable Unicode Character 'SMASH PRODUCT' (U+2A33) to display on my system. I am running Ubuntu MATE 14.04 AMD64 on a Samsung laptop with a AMD A6 and fglrx drivers. Is there a specific font that I need to install? How would I install that font?

---

### Post by GwibberFooey on 2016-11-05
The problem is resolved with the following command:

```
sudo apt-get install xfonts-mathml ttf-lyx otf-stix
```

---

