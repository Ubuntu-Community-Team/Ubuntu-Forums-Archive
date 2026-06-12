---
title: "I purged the fonts and it has messed-up my GUI fonts"
date: 2019-12-11
forum: General Help
---

### Post by sidewalkcynic on 2019-12-11
So, I was working with fonts in Blender: [http://www.blender.org/](http://www.blender.org/)

I installed an add-on to preview fonts: [https://www.blendernation.com/2017/09/22/add-easy-font-management-font-selector/](https://www.blendernation.com/2017/09/22/add-easy-font-management-font-selector/)

It was still too cluttered with fonts that do not make any sense (they're wierd, or boxes with numbers, or something), and so I purged the fonts using the list that was provided for a similar request from a month ago: [https://unix.stackexchange.com/questions/550889/why-so-many-default-fonts-in-ubuntu/550895](https://unix.stackexchange.com/questions/550889/why-so-many-default-fonts-in-ubuntu/550895)

Somehow my GUI fonts are messed-up - I think it is an aliasing problem. I went to the fonts settings in the Tweeks app, and tried different fonts, but it does not help. Any ideas???

---

### Post by sidewalkcynic on 2019-12-11
So, I just reinstalled the list, and it fixed it, and then it went bad again.

It seems to need the fonts.conf file from this discussion for it to work: [https://askubuntu.com/questions/1030041/full-font-hinting-not-working-in-ubuntu-18-04](https://askubuntu.com/questions/1030041/full-font-hinting-not-working-in-ubuntu-18-04)

---

