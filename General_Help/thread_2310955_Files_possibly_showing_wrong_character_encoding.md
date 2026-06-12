---
title: "Files possibly showing wrong character encoding?"
date: 2016-01-23
forum: General Help
---

### Post by lucy5 on 2016-01-23
I have some html files which have been created or edited in Sublime Text. Some files have been saved normally, and some I have saved specifically using UTF-8 encoding. The head has the meta charset=UTF-8 tag in it. Firefox info says all of the files are UTF8. However, if I use file -i in the terminal, every one of them shows as being us-ascii... So which is incorrect? Firefox (and Sublime, I suppose, as it's supposedly specifically saving as UTF-8 in some cases) or the terminal command? Or am I misunderstanding something? I don't really know much about character encoding, only that it's important.

Thank you for any help!

---

### Post by steeldriver on 2016-01-23
AFAIK the `file` command is looking at what bytes are actually there, rather than relying on the header: do the files actually contain any non-ASCII characters? As noted in this wikipedia [Comparison of Unicode encodings]("https://en.wikipedia.org/wiki/Comparison_of_Unicode_encodings")

> A UTF-8 file that contains only ASCII characters is identical to an ASCII file.

---

### Post by lucy5 on 2016-01-23
Well, I looked at this list: [http://terpconnect.umd.edu/~zben/Web/CharSet/htmlchars.html](http://terpconnect.umd.edu/~zben/Web/CharSet/htmlchars.html) which is apparantly non-ascii characters and it includes < and > - which are in use for html tags.

---

