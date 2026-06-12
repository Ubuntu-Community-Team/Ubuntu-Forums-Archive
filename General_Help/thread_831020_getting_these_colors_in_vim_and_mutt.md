---
title: "getting these colors in vim and mutt"
date: 2008-06-16
forum: General Help
---

### Post by go_beep_yourself on 2008-06-16
How can I get these colors in Vim and Mutt? They are nice to do programming with.

[IMG]http://img240.imageshack.us/img240/972/colors1av5.png[/IMG]

[IMG]http://img108.imageshack.us/img108/7773/colors2rl1.png[/IMG]

---

### Post by Woei on 2008-06-16
> **go_beep_yourself said:**
> How can I get these colors in Vim and Mutt? They are nice to do programming with.

[IMG]http://img240.imageshack.us/img240/972/colors1av5.png[/IMG]

[IMG]http://img108.imageshack.us/img108/7773/colors2rl1.png[/IMG]

Add something like the following to your [FONT="Courier New"]~/.vimrc[/FONT] file:

```
:color torte
set tabstop=8
set softtabstop=4
set shiftwidth=4
set expandtab
set nu
```

As for mutt, add this to your [FONT="Courier New"]~/.muttrc[/FONT] file:

```
color normal    white black
color attachment brightyellow black
color hdrdefault cyan black
color indicator black cyan
color markers   brightred black
color quoted    green black
color signature cyan black
color status    brightgreen blue
color tilde     blue black
color tree      red black
color header    brightgreen black ^From:
color header    brightcyan black ^To:
color header    brightcyan black ^Reply-To:
color header    brightcyan black ^Cc:
color header    brightblue black ^Subject:
color body      brightred black [\-\.+_a-zA-Z0-9]+@[\-\.a-zA-Z0-9]+
color body      brightblue black (https?|ftp)://[\-\.,/%~_:?&=\#a-zA-Z0-9]+
```

---

### Post by go_beep_yourself on 2008-06-16
Thanks, that was almost it but not quite. I found what I was looking for.

[http://vim.sourceforge.net/scripts/script.php?script_id=2215](http://vim.sourceforge.net/scripts/script.php?script_id=2215)

---

### Post by go_beep_yourself on 2008-06-16
Look similar? Gedit and Gvim

[IMG]http://img113.imageshack.us/img113/1413/coolthemeue3.png[/IMG]

---

