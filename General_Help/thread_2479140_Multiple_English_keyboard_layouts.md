---
title: "Multiple English keyboard layouts"
date: 2022-09-15
forum: General Help
---

### Post by cmalfet on 2022-09-15
Hi all,

I have a weird problem. In the settings I have only English (US) keyboard layout, however, in reality there are both UK and US layouts and I can switch between them. This is super annoying, because I randomly get £ instead of #, or " instead of @. Could please anyone suggest how to solve it and how to remove the "invisible" UK layout from the system?? Thank you!

Alexander

---

### Post by ne29914 on 2022-09-15
Which language setting do you have? Not all language/keyboard combinations are allowed/supported, and this sounds like an issue in that direction.
You'll find the allowed combinations in:
```
/usr/share/i18n/SUPPORTED
```
Example: en_US would be English locale, US keyboard.

---

### Post by cmalfet on 2022-09-16
I just want to have en_US and ru_RU. Only these two are listed in the Settings-Keyboard-Input Sources, but for some reasons I have 3 en_US, en_UK and ru_RU. My question is how to get rid of en_UK layout, when it's not even listed in the Settings-Keyboard section in the first place.

---

