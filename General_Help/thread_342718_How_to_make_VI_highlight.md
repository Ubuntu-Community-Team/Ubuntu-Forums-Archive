---
title: "How to make VI highlight?"
date: 2007-01-20
forum: General Help
---

### Post by mrwooster on 2007-01-20
Hi,

When I used the knoppix live cd, vi had highlighting for PHP, it does not seem to do it on ubuntu, is there any way to change this?

Thanks

Guy

---

### Post by dexter on 2007-01-20
Edit the config file in /etc/vim/vimrc, uncomment the line
```

syntax on

```
and you will have syntax highlighting in vim.

---

### Post by hellraiser_rob on 2007-02-08
hi,

i'm trying to get the syntax highlighting working also, when i uncomment this line is throws this error when i try and run vim

Error detected while processing /usr/share/vim/vimrc:
line   20:
E319: Sorry, the command is not available in this version: syntax on
Press ENTER or type command to continue


Any ideas?

Cheers
Rob

---

### Post by meng on 2007-02-08
Are you really still using Breezy?
I know that in more recent versions, you can install vim-full
sudo apt-get install vim-full

I wonder if that will fix the problem for you.

---

