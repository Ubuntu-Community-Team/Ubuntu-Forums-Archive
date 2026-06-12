---
title: "What is with Ubuntu vi?"
date: 2007-12-10
forum: General Help
---

### Post by dhinge on 2007-12-10
I hit "i" to insert... I hit Delete on a letter, and it changes it's capitalization... I hit Delete again and it deletes it. I hit the ESC key, "i" again, then an arrow key, and it displays a letter, like "A" or "B" or "C" or "D"... If I hit Delete (which changes caps on a letter), then the arrow keys work the way you'd think. What is with this wonky behaviour?

---

### Post by PmDematagoda on 2007-12-10
If you are talking about the vim text editor, then it is rather different from the earlier vi text editor, you can learn more about using vim from [here.]("http://www.vim.org/htmldoc/help.html")

---

### Post by dhinge on 2007-12-10
No, vim actually works right. I don't know what's up with vi. Thanks for the ad though.

---

### Post by quantumcheese on 2007-12-10
If you're getting ^[[A instead of up arrow press, the problem is probably at the terminal level.  run cat -v and type your arrow keys; if those match what you're seeing in vi, then you'll know that it's not processing the control codes properly.  Not sure what the fix is, but at least it's something to go on.

---

### Post by yanlinlin82 on 2008-06-01
I met the same problem. I removed vim-tiny, and reinstalled vim to resolve it.

---

### Post by pip on 2008-06-04
> **yanlinlin82 said:**
> I met the same problem. I removed vim-tiny, and reinstalled vim to resolve it.

Thanks for that! That did indeed solve it.

---

### Post by ArcaneMagus on 2008-07-19
As the top of vimrc.tiny states:
[INDENT]Vim configuration file, in effect when invoked as "vi". The aim of this configuration file is to provide a Vim environment as compatible with the original vi as possible.[/INDENT]

why in the world ubuntu would choose to do this is beyond me though...

---

