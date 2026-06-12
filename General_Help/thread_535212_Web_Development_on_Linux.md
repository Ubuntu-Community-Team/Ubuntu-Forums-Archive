---
title: "Web Development on Linux"
date: 2007-08-26
forum: General Help
---

### Post by nami on 2007-08-26
Dear Ubuntu Experts,

I am trying to get my webpage to work properly on linux operating systems.  I seem to be having a problem.  In my css file, I set the font to arial and the font size to 13px, but the textbox in linux increases size for some reason?

How do I get it the same size.  Please have a look at the attachments to see what I mean.  The search button is just an image, so naturally, it would not increase or decrease in size.

The textbox works perfectly in firefox on windows.

Help

---

### Post by sonofusion82 on 2007-08-26
My guess is that you are using Arial, which is not a common font available in Linux unless the MS TrueType Fonts are installed. Anyway, I am not an expert in web design, it has been years since I last coded HTML by hand, so I might be a bit rusty on this. Anyway, check out this site: [http://www.webspaceworks.com/resources/fonts-web-typography/48/](http://www.webspaceworks.com/resources/fonts-web-typography/48/)

---

### Post by p_quarles on 2007-08-26
Using css to set a single font is a good way of making a page incompatible with lots of browsers. Try using the font-family tag to give the browser some options. For instance:
```
font-family: Arial, Helvetica, sans-serif
```

---

### Post by nami on 2007-08-26
Is there an arial equivalent in linux?  or something similar?  what is the default font in linux?

---

### Post by p_quarles on 2007-08-26
Generic sans-serif is going to be the most cross-browser compatible font.

---

### Post by zach12 on 2007-08-26
just open openoffice and find a something that looks right

---

