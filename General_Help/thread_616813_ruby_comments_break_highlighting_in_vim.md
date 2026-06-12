---
title: "ruby comments break highlighting in vim"
date: 2007-11-18
forum: General Help
---

### Post by hasimir44 on 2007-11-18
Syntax highlighting works great in vim until I create a comment in a ruby file. To be more accurate, it happens when I delete the auto generated comment on the next line.  Typing the following command turns it on again until the next comment: ```
:syntax on
```

This only happens to ruby files (so far, I tried a perl file and it works fine).  I don't need to (nor care to) actually fix the problem, if someone could tell me how to disable the auto comments, then I'd never notice it again. I can also type the command to set comments to a blank line and it works great:
```
:set comments=

```
but where do I save that command so I don't have to type it every time I open a file? putting it in ~/.vimrc doesn't work, nor does putting it in /etc/vim/vimrc  
I read that vim sources many different conf files and I assume that the comment option is getting overridden somewhere down the line. 

Please help me get back to my studies, this is so annoying. (I've already uninstalled, reinstalled, tried vim.tiny, vim.full, vim.ruby, ...)  Thanks

---

