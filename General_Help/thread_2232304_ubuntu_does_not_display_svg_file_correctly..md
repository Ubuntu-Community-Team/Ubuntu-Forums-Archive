---
title: "ubuntu does not display svg file correctly."
date: 2014-07-01
forum: General Help
---

### Post by monkeybrain20122 on 2014-07-01
Hi,

I have a .svg file created in inkscape in lubuntu (saved as plain svg), it displays properly in lubuntu and xubuntu (first screenshot) but in Ubuntu it appears like the second screenshot.

This is not an inkscape issue because opening the file in firefox, chrome and image viewer show the same distortion and only in Ubuntu (work in Xubuntu, lubuntu and even Windows)

Please advise, thanks.

---

### Post by coffeecat on 2014-07-01
It looks as though you have the font Gentium Book Basic installed in your Lubuntu and Xubuntu installations but not in Ubuntu. Try installing Gentium Book Basic in Ubuntu - it makes a world of difference to your svg!

---

### Post by mcduck on 2014-07-01
I agree with coffeecat, seems to be a missing font.

Unless you convert text into paths, SVG files depend on the fonts installed on the computer when viewing the files. Converting to path makes sure the file will always look the same (so you'll usually want to do it before sending the file to anyone else or publishing it) but at the same time you loose the ability to edit the text. I usually keep the editable text on a hidden layer so I don't have to completely redo it if I need to edit it afterwards.

---

### Post by monkeybrain20122 on 2014-07-01
Thanks guys, installing Gentium Book Basic works. It is installed by default in X/Lubuntu, not sure why not in Ubuntu.

Thanks mcduck for the tip to convert text to path. It is very helpful.

---

