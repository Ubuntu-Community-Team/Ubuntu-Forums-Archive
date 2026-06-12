---
title: "Fonts I purchased at linotype.com and installed using gnome-font-viewer won't show up"
date: 2014-06-18
forum: General Help
---

### Post by desmonddevlin on 2014-06-18
I have tried to install the Berling Roman, Quill and Big Caslon fonts that I purchased from linotype.com and installed them using terminal commands, yet they won't show up either on LibreOffice or GIMP.

Is this an attempt by the Copywrongers to stop special fonts that aren't free to access being used on Linux? Or is there a way round it?

---

### Post by tgalati4 on 2014-06-19
Open a terminal and examine your list of fonts.  You don't need to post them.

```
fc-list
```

Perhaps you need to add them to the font cache:  [https://help.ubuntu.com/community/Fonts](https://help.ubuntu.com/community/Fonts)

---

### Post by grahammechanical on 2014-06-19
> **desmonddevlin said:**
> I have tried to install the Berling Roman, Quill and Big Caslon fonts that I purchased from linotype.com and installed them using terminal commands, yet they won't show up either on LibreOffice or GIMP.

Is this an attempt by the Copywrongers to stop special fonts that aren't free to access being used on Linux? Or is there a way round it?

It is most likely the exact opposite as these fonts are in the OpenType format which standard was designed by Adobe and Microsoft. 

[http://www.linuxlibertine.org/index.php?id=87&L=1](http://www.linuxlibertine.org/index.php?id=87&L=1)

[http://ask.libreoffice.org/en/question/9797/support-for-opentype-advance-features-please/](http://ask.libreoffice.org/en/question/9797/support-for-opentype-advance-features-please/)

[https://en.wikipedia.org/wiki/OpenType#OpenType_support](https://en.wikipedia.org/wiki/OpenType#OpenType_support)

I note that the supplier of the fonts that you have purchased does not provide instructions for installing under Linux.

Regards.

---

