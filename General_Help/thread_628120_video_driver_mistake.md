---
title: "video driver mistake"
date: 2007-11-30
forum: General Help
---

### Post by baldheadedguy on 2007-11-30
ok big problem I was trying to set xubuntu to have smaller icons and and font so that every thing would fit on the screen. I tried a different video driver. that was mistake. now all i get is a black screen and some funky symbols. Am i screwed? and if so how do i reinstall on a duel boot system? HELP. 

dell inspiron 5100 laptop/xp/xubuntu7.10

---

### Post by PmDematagoda on 2007-11-30
Do:-
```

sudo dpkg-reconfigure xserver-xorg
```

And select the driver which was used earlier.

---

### Post by baldheadedguy on 2007-11-30
> **PmDematagoda said:**
> Do:-
```

sudo dpkg-reconfigure xserver-xorg
```

And select the driver which was used earlier.

do i do this i safe mode? sorry 
nooby here.

---

### Post by -grubby on 2007-11-30
> **baldheadedguy said:**
> do i do this i safe mode? sorry 
nooby here.

yes you do it in "recovery mode"

---

