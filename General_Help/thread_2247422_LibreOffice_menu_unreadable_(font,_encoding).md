---
title: "LibreOffice menu unreadable (font, encoding?)"
date: 2014-10-07
forum: General Help
---

### Post by David_Bragason on 2014-10-07
I'm running an up to date Kubuntu 14.04 system. After a recent update my LibreOffice has become unusable, as the menus are unreadable (rectangles instead of characters, as seen from the attached screen shot). LibreOffice worked fine before. I have tried to purge LibreOffice and reinstalling it with no change. I have also tried upgrading LibreOffice to a 4.3 version from launchpad.net. The locale settings seem ok (I use en_US.UTF-8).

No other program on my system shows this behavior. I would appreciate any tips on how to fix this. Thank you.

Greetings,
David

---

### Post by SeijiSensei on 2014-10-07
Take a look in System Settings > Application Appearance > GTK and see what themes and fonts you are using for GTK applications like LibreOffice.

Also, see if **libreoffice-kde** is installed. If it is, try removing it and see if that helps.  That package enables LO to use KDE dialogs and such, but it's had some problems in the past.

---

### Post by David_Bragason on 2014-10-08
Thank you very much, making any change in the GTK settings (theme, font) fixes the problem.

---

