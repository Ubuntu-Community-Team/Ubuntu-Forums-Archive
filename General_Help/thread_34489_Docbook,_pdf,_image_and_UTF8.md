---
title: "Docbook, pdf, image and UTF8"
date: 2005-05-15
forum: General Help
---

### Post by nikikko on 2005-05-15
Hello,

I have a big problem with docbook and pdf generation. I have a simple docbook file in UTF8 with images.

**docbook2pdf**
When I use docbook2pdf, the rendered pdf has no image and all my accent disappear for strange letters.

**sgmltools**
When I use sgmltools, I have no accent... just strange letters.

**fop**
I tried fop and it was working, but all the images were too big (it doesn't use the resolution of the images).

I thought that docbook was made for UTF8... do you have any idea ?

---

### Post by cobbaut on 2007-07-27
I also use docbook2pdf, and have the same problem with images.

About accents and strange characters, you'll have to use &#039 for apostrophe, &#096 for accent grave etc

cheers,
paul

---

