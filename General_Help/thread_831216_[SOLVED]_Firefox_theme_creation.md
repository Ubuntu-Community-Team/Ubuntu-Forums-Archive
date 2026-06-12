---
title: "[SOLVED] Firefox theme creation"
date: 2008-06-16
forum: General Help
---

### Post by Rabix on 2008-06-16
Hi !

I would like to modify a theme, for firefox3, but my theme won't load.

I tried to :
- take a working theme
- decompress it
- recompresse it (using file roller - I try with both .jar and .zip format)

When I try to load it, it doesn't work. more specifically it does like it was intalling it but the new modify them doesn't show up in the installed list.

That make me suspect a problem with the compression, but is as far as i could go !

Thanks

---

### Post by macaholic on 2008-06-16
The jar files, as I understand it, are not actual jar files, but just zip files, so you should compress the theme in a zip file and rename it to a .jar. Also, I would suggest using the command zip -r to recompress indivudual files into the original theme file first, and see where that takes you.

---

### Post by Rabix on 2008-06-16
Thanks for the amswer. I did try to zip it and rename it afterwards but it does the same thing.

What I am trying to do now is to take an exinstig .jat theme, decompress it and try to recompress it without changing anything. But that doesn't work.

Edit: I think I got it working ;) (with the command line instead of file roller)

Edit2: It does work ;) thx. It seems you can't compress the whole folder.

---

