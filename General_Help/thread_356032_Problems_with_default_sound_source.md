---
title: "Problems with default sound source"
date: 2007-02-07
forum: General Help
---

### Post by trenog on 2007-02-07
For some reason my default sound card is being selected as my integrated sound card instead of my Soundblaster Live Value card. Anyone know how I can fix that?

Thanks

---

### Post by sdide on 2007-02-08
Hey,

do:

asoundconf list

to see a list of your cards.

and do:

asoundconf set-default-card <CARD>

where <CARD> is the one you want to be default from the list.

---

### Post by trenog on 2007-02-09
Thanks

---

