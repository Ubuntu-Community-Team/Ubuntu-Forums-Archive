---
title: "Font issue with PDF viewer"
date: 2012-12-29
forum: General Help
---

### Post by nishant032 on 2012-12-29
After installing the msfont package for use Arial and Times New Roman I started having all sort of problems with fonts in Ubuntu.
Now if I open a pdf file the document viewer shows no text and if I open the pdf from shell I can see a list of errors saying

```
Error: could not create type1 face
some font thing failed
```

Also when working with GIMP I get the same error on the shell and sometimes GIMP closes unexpectedly when I work with text.
Any idea?

---

### Post by dino99 on 2012-12-29
how have you installed these fonts ?

[http://www.howtogeek.com/howto/15495/add-microsoft-core-fonts-to-ubuntu/](http://www.howtogeek.com/howto/15495/add-microsoft-core-fonts-to-ubuntu/)

---

### Post by nishant032 on 2012-12-29
> **dino99 said:**
> how have you installed these fonts ?

[http://www.howtogeek.com/howto/15495/add-microsoft-core-fonts-to-ubuntu/](http://www.howtogeek.com/howto/15495/add-microsoft-core-fonts-to-ubuntu/)

Yes, I followed that instructions. I tried removing the msfonts and reinstalling but still have the same issue.

---

### Post by nishant032 on 2013-01-06
YEP! I did it! The only thing I had to do was to run

    sudo fc-cache -r    

In the shell.

---

