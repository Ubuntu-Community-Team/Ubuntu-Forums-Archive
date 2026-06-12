---
title: "[SOLVED] VI, editting the way it starts up"
date: 2007-11-25
forum: General Help
---

### Post by teryowen on 2007-11-25
I remember using VI in computer class a while back, and what we did was edit a file which would configure the VI so that when you run it for example you get line numbers.

Anybody know how to do this, or where this file is?

---

### Post by LaRoza on 2007-11-25
```

sudo aptitude install vim-full

```

The file is "vimrc".

---

### Post by ekravche on 2007-11-25
edit your .vimrc file it should be in your home directory. You'll need to start gvim though instead of vi. I prefer to use gvim though.

---

### Post by nick_h on 2007-11-25
You can always turn line numbering on with:
```
:set number
```
and off again with:
```
:set nonumber
```

---

### Post by LaRoza on 2007-11-25
> **nick_h said:**
> You can always turn line numbering on with:
```
:set number
```
and off again with:
```
:set nonumber
```

Adding that at start up will prevent having to type it every time. Also, you can use ":syntax on" for syntax highlighting.

---

### Post by teryowen on 2007-11-25
Hey i installed vim-full but i cant find the vimrc file.

---

### Post by bingoUV on 2007-11-25
It is ~/.vimrc. If it does not exist, no problem. Vim does not mind. You can create it, and vim will consider it the next time you start vim.

---

### Post by teryowen on 2007-11-25
Thanks i just created the .vimrc file and works perfectly.

---

