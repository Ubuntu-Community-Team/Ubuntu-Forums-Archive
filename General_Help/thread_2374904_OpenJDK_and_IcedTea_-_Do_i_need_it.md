---
title: "OpenJDK and IcedTea - Do i need it?"
date: 2017-10-20
forum: General Help
---

### Post by Ice-Tea on 2017-10-20
Apart from it allowing websites to spam me with adverts is there any particular reason why i would need OpenJDK and IcedTea or can they be safely removed?

Thanks

---

### Post by vasa1 on 2017-10-20
LibreOffice has some features that may depend on OpenJDK. Run *apt show libreoffice* for more.

---

### Post by Impavidus on 2017-10-20
Some optional features in Libreoffice depend on OpenJDK, but most of Libreoffice will work without it. If you can live without those features, you can probably uninstall OpenJDK and IcedTea. I've never had them installed.

Use the package manager to remove them. Have a look at the list of additional packages to be removed (if any), and if that shows something you want to keep, abort.

---

### Post by Ice-Tea on 2017-10-21
I don't use  Libreoffice either so i can remove that along with OpenJDK.

Thanks both for the reply.

---

