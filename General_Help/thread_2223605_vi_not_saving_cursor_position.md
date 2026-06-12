---
title: "vi not saving cursor position"
date: 2014-05-12
forum: General Help
---

### Post by IAMTubby on 2014-05-12
Hello,
 Every time I write-quit my file and re-open it, the cursor is placed at the beginning of the file.
I understand that I probably have to change something in the vimrc file. But I get a lot of references to vimrc in my search, and I don't understand what to edit either.
```

$ find ./ -name '*vimrc' 2>/dev/null
./usr/share/vim/vimrc
./etc/vim/vimrc
./media/3310890c-1447-47d0-a4fa-a04b0f2a7e35/etc/vim/vimrc
./media/3310890c-1447-47d0-a4fa-a04b0f2a7e35/usr/share/vim/vimrc

```

Please advise.
Thanks.

---

### Post by TheFu on 2014-05-12
~/.vimrc

---

### Post by IAMTubby on 2014-05-16
> **TheFu said:**
> ~/.vimrc
ThuFu,
Thanks for the reply, but

```
IAMTubby@IAMTubby-Inspiron-1545:~$ ls ~/.vimrc
ls: cannot access /home/IAMTubby/.vimrc: No such file or directory
```



Can you also tell me what I should add to my vimrc to save cursor position ?

---

### Post by HiImTye on 2014-05-16
```
cp /usr/share/vim/vimrc ~/.vimrc
vim ~/.vimrc
```in the augroup section put```
  autocmd BufReadPost *
    \ if line("'\"") > 1 && line("'\"") <= line("$") |
    \   exe "normal! g`\"" |
    \ endif
```
if it isn't there already

---

### Post by IAMTubby on 2014-05-17
> **HiImTye said:**
> ```
cp /usr/share/vim/vimrc ~/.vimrc
vim ~/.vimrc
```in the augroup section put```
  autocmd BufReadPost *
    \ if line("'\"") > 1 && line("'\"") <= line("$") |
    \   exe "normal! g`\"" |
    \ endif
```
if it isn't there already
Thanks HiImTye,
Like you said, the ~/.vimrc had an autocmd section which asked to uncomment if I needed the feature. Uncommented it and got it working.
```
" Uncomment the following to have Vim jump to the last position when" reopening a file
if has("autocmd")
  au BufReadPost * if line("'\"") > 1 && line("'\"") <= line("$") | exe "normal! g'\"" | endif
endif

```

---

