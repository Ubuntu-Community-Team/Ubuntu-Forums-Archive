---
title: "Vim/GVim printing"
date: 2013-09-12
forum: General Help
---

### Post by HiImTye on 2013-09-12
I figured I'd share what I did to get vim (and by extension, gvim) to print. Vim uses *lpr* by default to print (which isn't installed, and incidentally, after installing it when I tried using it to print it failed silently), so I told it to use *lp* instead (which actually works in the terminal). I added the following to the end of my *~/.vimrc*:
```
set printoptions+=header:0

set printexpr=PrintFile(v:fname_in)
function! PrintFile(fname)
  call system("lp " . a:fname)
  call delete(a:fname)
  return v:shell_error
endfunc
```
note: the extra space is required after *lp*, as it separates the command from the input to the command (vim simply sends a shell command, instead of handling printing on it's own, which is fine so long as it uses the right command).

following this you don't even need to specify a printer (*set pdev=*), as *lp* handles all of it for you (so long as *cups* is properly configured).

---

