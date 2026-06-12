---
title: "Setup of language, currency and units"
date: 2008-06-02
forum: General Help
---

### Post by Euphorion on 2008-06-02
During installation of Ubuntu, I told the system I would like the system to speak English, use a German keyboard layout and have time zone Berlin, and reside in Stuttgart.


 Having told Ubuntu this I would have expected that the default Currency be set to Euro and that the decimal point be a comma and the thousands diver be a decimal point.


 Whilst setting up OpenOffice Writer and Calc I noticed that the English conventions are active. So I thought well simple matter find the application for setting up language and currency settings (dare I say it a la windows, I have for 3 weeks migrated from Vista to Ubuntu) but I can’t find such an application within the desktop. How can I check and correct my settings ?

---

### Post by p_quarles on 2008-06-02
It's not going to be like Windows, because a GNU/Linux system is considerably more multilayered and modular than Windows (which is both a good thing and a bad thing, depending on what you're trying to do).

In any case, the settings you selected during installation are likely to only affect Gnome settings, and OpenOffice.org is not a Gnome application -- the settings are separate. 

You should be able to fix this to be the way you want it by opening up your package management program, searching for the OpenOffice localization package you want, and installing it.

---

### Post by Euphorion on 2008-06-04
Thank you for your reply and the explination as to why. I have set up OpenOffice manually using the settings within OpenOffice. It now works fine.

---

