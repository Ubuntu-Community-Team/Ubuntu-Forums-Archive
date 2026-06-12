---
title: "Encoding problems"
date: 2005-04-27
forum: General Help
---

### Post by Aurels on 2005-04-27
Hello.

I installed hoary on my laptop and I got some trouble with special charcters like "é" or "è" in files (PHP scripts and MySQL data in particular). I'm belgian but I installed ubuntu in english.
I heard about the recode tool, is it a good solution?
Any ideas for me?
Thanks.

---

### Post by Alexander Kirillov on 2005-04-27
[QUOTE=Aurels]Hello.

I installed hoary on my laptop and I got some trouble with special charcters like "é" or "è" in files (PHP scripts and MySQL data in particular). I'm belgian but I installed ubuntu in english.
I heard about the recode tool, is it a good solution?
Any ideas for me?
Thanks.[/QUOTE]
 What kind of trouble?

By default, hoary uses UTF8 encoding for all files. If you have files which were created elsewhere and use latin-1 encoding, you can recode them to UTF8 (there are also other ways - e.g. , you can explicitly specify to applications the encoding used by files). I found recode to be a reliable solution.

---

### Post by Aurels on 2005-04-28
Kind of problems:

some charcters like é è ... becomes a little triangle with a ? inside.

For some of the PHP files, i could change the encoding to UTF-8 with emacs but how to do that for binary mysql data files?

Thank you for your qick reply.

---

### Post by Alexander Kirillov on 2005-04-28
[QUOTE=Aurels]Kind of problems:

some charcters like é è ... becomes a little triangle with a ? inside.

For some of the PHP files, i could change the encoding to UTF-8 with emacs but how to do that for binary mysql data files?

Thank you for your qick reply.[/QUOTE]
 For text files (including PHP), I'd use recode - this is easier tahn emacs. For mysql, I have no idea. Probably various mysql frontends provide an option of converting from one encoding to another? Or specifying the encoding directly? Just guessing... 

Of course, if everything else fails, you can always switch back to iso8859-1 locale - but in the long term, this is not a good idea.

---

