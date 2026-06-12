---
title: "VIM - need configure .vimrc to filter/map out (nop?) a key on my keyboard (F1)"
date: 2020-08-07
forum: General Help
---

### Post by wb0gaz on 2020-08-07
I am running VIM (Vi IMproved) version 8.0.1453 on lubuntu 18.04.

I need to filter out (make inactive) the F1 key on my keyboard. As Lubuntu has no obvious (at least to me) method of manipulating keyboard codes, I am trying to solve this with VIM, which is where the problem is acute.

VIM unhelpfully brings up a help menu which is problematic when I unintentionally hit the F1 key (which happens frequently as it is next to Esc).

I verified that VIM does indeed read in .vimrc (I tried putting a test message there and it was flagged on start-up.)

My goal is to map F1 to nop, however, the following instruction in .vimrc is ignored:

map <F1> <nop>

I think the problem is that F1 is not on my keyboard what VIM defines as F1 in the map command.

When I hit F1 key the following byte codes are emitted: 27 79 80, which corresponds to esc OP.

What do I use in the first argument to map to get it to recognize this 3 character sequence?

Thank you.

---

### Post by wb0gaz on 2020-08-08
Should this question be posted to a different part of the forum?

Thank you for any help!

---

### Post by &amp;KyT$0P# on 2020-08-08
Did you try [this]("https://vim.fandom.com/wiki/Disable_F1_built-in_help_key#Comments")? -
```
nmap <F1> <nop>
```
Works for me in Vim and GVim on 18.04.

---

### Post by norobro on 2020-08-08
On my 20.04 box (VIM 8.1.2269) "map" and "nmap" only disable the F1 key in normal mode. For insert mode I use "imap".
```
nmap <F1> <nop>
imap <F1> <nop>
```

FWIW my keycode is the same:```
# showkey -a

Press any keys - Ctrl-D will terminate this program


^[OP      27 0033 0x1b
      79 0117 0x4f
      80 0120 0x50
```

---

### Post by wb0gaz on 2020-08-08
Thanks!!!

The culprit turns out to be "vim-tiny" which Lubuntu decided to install in lieu of vim. I didn't realize this until I started trying to replicate the steps provided here as suggestions.

I did this to fix the problem:

sudo apt remove vim-tiny
sudo apt install vim

and now .vimrc is behaving as norobo and halogen2 recommended.

Also, showkey did result in the same codes norobo notes above.

vim-tiny's initial help display is formatted enough like vim that I didn't read the text (on the same screen) closely enough to see that it was a different program.

I've been using vi since about 1992 on unix machines, so I really didn't want to migrate to a different editor type.

THANK YOU FOR ALL OF YOUR HELP!!!!!!!

Dave

---

