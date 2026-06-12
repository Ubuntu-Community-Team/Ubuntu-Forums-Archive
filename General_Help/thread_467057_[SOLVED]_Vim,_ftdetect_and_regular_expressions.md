---
title: "[SOLVED] Vim, ftdetect and regular expressions"
date: 2007-06-07
forum: General Help
---

### Post by reclusivemonkey on 2007-06-07
I tried to subscribe to the vim mailing list today but I don't seem to be getting a reply, so maybe a vim guru can help me out here!

I use vim for pretty much everything I can, but I've only just recently discovered the more advanced options in vim. I have downloaded two vim syntax files, and saved them to .vim/syntax; namely remind.vim and txt.vim. I believe I should be able to use both of these syntax files automatically, but I am not sure. I only seem to be able to get one to work. In ~/.vim/ftdetect/remind.vim I have the following;

```

au BufNewFile,BufRead ~/gtd/*.txt set filetype=remind

```

This works fine, and doesn't capture anything out of the gtd folder. I have the following in my ~/.vim/ftdetect/txt;

```

au BufNewFile,BufRead [^~/gtd/]*.txt set filetype=txt

```

I've tried every single combination I can think of, but I just don't seem to be able to get the expression right. Should I be able to do this? If so can anyone help me out with the right expression?

---

### Post by reclusivemonkey on 2007-06-07
Bah, I knew I'd get it once I'd posted! The answer was;

```

au BufNewFile,BufRead ~/[^gtd]*.txt set filetype=txt

```

---

