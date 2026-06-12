---
title: "Automatic saving vim"
date: 2015-03-06
forum: General Help
---

### Post by CkDGTAT on 2015-03-06
Hi,

How can I configure vim to save the file everytime a character is entered?

Thank you

---

### Post by TheFu on 2015-03-06
You can script almost anything with vim.
I web searched "autosave vim" and found 20 possible answers - depending on the version of vim you have and other options.
* save every 1 sec - caveats
* save every character - caveats
* save all buffers (advanced users often have multiple buffers in use) - caveats

Each seems to have issues, so only you can read the options and decide when any specific issue isn't important for your work style.

Try them and see which works best for your needs. Would be nice if you posted which solution worked besthere.

---

### Post by CkDGTAT on 2015-03-07
```
[FONT=Consolas]set updatetime=1000
[/FONT][FONT=Consolas]autocmd CursorHoldI * silent w[/FONT]
```

---

