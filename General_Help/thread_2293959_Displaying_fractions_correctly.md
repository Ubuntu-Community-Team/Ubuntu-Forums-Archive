---
title: "Displaying fractions correctly"
date: 2015-09-08
forum: General Help
---

### Post by arthur26 on 2015-09-08
Is there a way to auto format all fractions to a single spaced character in the way that 1/2 and 1/4 are system wide (I am using cinnamon if that makes a difference)

---

### Post by efflandt on 2015-09-08
Programs that are not plain text (like word processors) may automatically convert 1/4 to ¼, 1/2 to ½, and 3/4 to ¾, but that is because there are single character codes for those fractions. To somewhat simulate that for other fractions you would need something that could put together a superscript, slash, and subscript with dynamic character spacing (kerning?).

---

### Post by gleedadswell on 2015-09-09
Perhaps LaTeX does approximately what you need?  It wouldn't be "system wide" but LaTeX has been integrated into lots of things.  What applications do you need this in?  If it is in LibreOffice then there is an extension called TexMaths which lets you use LaTeX within LibreOffice.

---

### Post by arthur26 on 2015-09-09
Thanks everyone libreoffice was my main concern.

---

### Post by gleedadswell on 2015-09-10
Just one further comment.  What TexMath will produce in your libreoffice documents will not be single spaced characters like you initially wanted.  It produces the LaTeX output as little graphics files (.png or .svg format?) which you can then resize if you wish.

---

