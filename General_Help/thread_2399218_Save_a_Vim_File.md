---
title: "Save a Vim File"
date: 2018-08-22
forum: General Help
---

### Post by shane_faulkinbury2 on 2018-08-22
I'm using VIM for the first time and I added this line to the bottom and I'm asking how do i save the file and exit?  I've searched at least  four of the top links using Duckduckgo and  nothing works!

```
export PATH="/usr/local/ssl/bin:${PATH}"
```

---

### Post by &amp;KyT$0P# on 2018-08-22
[noparse]:w to save, :q to quit

Or you could use :x to save and quit in one step[/noparse]

---

### Post by QIII on 2018-08-22
Hello!

Esc to exit the edit mode and then

```
:wq
```

(A mnemonic for that might be "**w**rite and **q**uit"

[This]("https://www.vim.org/docs.php") is a good place to look as you learn vim.  vim is not the sort of thing you learn overnight.  It takes a lot of practice and you need to build some muscle memory for things to just "click".

Edit:  There are a number of interactive tutorials out there, like [this.]("https://www.openvim.com/")  Trying to memorize stuff from a "cheat sheet" is frustrating.  Learn by doing it.  Over and over.

---

### Post by shane_faulkinbury2 on 2018-08-23
I read to do that, but do I put in the colon or not.  I put it in and it just moved to the cursor to the next line and didn't quit.

---

### Post by QIII on 2018-08-23
Did you press the "Esc" button first to get out of edit mode?

---

### Post by shane_faulkinbury2 on 2018-08-23
No I didn't, but will now!  Thanks

---

