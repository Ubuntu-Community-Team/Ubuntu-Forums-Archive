---
title: "gnome-terminal, vim and cursor keys."
date: 2007-05-16
forum: General Help
---

### Post by the_it on 2007-05-16
It's linux see?  So editing text files is the thing to do.  Many howtos here give 'gksu gedit' or 'sudo gedit' to edit text files, but I'm a vim addict, so there.

I notice that when I'm running vim from a gnome-terminal, pressing the cursor and other keys in edit mode types letters.

up - A\n
down - B\n
left - D\n
right- C\n

home - H\n
end - F\n
del/pageup/down - change case of current letter then \n

Anyways, it's generally annoying since I have to switch from command mode to edit mode to move around.

Vim seems to work alright on a regular tty.

Also I notice that if I press backspace, the cursor moves back, but the graphic of the erased letter doesn't go away (the character IS erased though) (this happens on a regular tty as well)

> markd@trixie:~$ dpkg -l |grep gnome-terminal
ii  gnome-terminal                             2.18.0-0ubuntu1                        The GNOME 2 terminal emulator application
ii  gnome-terminal-data                        2.18.0-0ubuntu1                        Data files for the GNOME terminal emulator
markd@trixie:~$ dpkg -l |grep vim
ii  vim-common                                 7.0-164+1ubuntu7                       Vi IMproved - Common files
ii  vim-tiny                                   7.0-164+1ubuntu7                       Vi IMproved - enhanced vi editor - compact v
markd@trixie:~$ dpkg -l |grep bash
ii  bash                                       3.2-0ubuntu7                           The GNU Bourne Again SHell


any files I can check on this?  I want to be able to use vim normally from a gnome-terminal.

---

### Post by vtel57 on 2007-05-16
Are you absolutely sure you're not running Vi editor? I ask because the navigation keys in Vi are slightly different than Vim. Vim works fine in my Gnome Terminal on all four of my Gnome distros.

See [HERE](http://www.eng.hawaii.edu/Tutor/vi.html#s-mvcur) for Vi navigation commands.

---

### Post by Bolorino on 2007-05-16
It seems (AFAIK) that in edgy command "vi" launches vim, but not in feisty.
Change vi for vim when editing.

---

### Post by qix on 2007-05-16
Go to your home folder and create the ".vimrc" file. This should disable the vi-emulation of vim.

I think.

If it doesn't work, add this line to .vimrc:
set nocompatible

---

### Post by the_it on 2007-05-16
**Bolorino**
> It seems (AFAIK) that in edgy command "vi" launches vim, but not in feisty.
Change vi for vim when editing.

That's strange, both vi and vim's etc/alternatives link to /usr/bin/vim.tiny, and yet, if I type vi I get funky keys in X, whereas if I type vim I get my usualy vim keys.

**qix**
> If it doesn't work, add this line to .vimrc:
set nocompatible

Major win!  vi compatibility somehow gets turned on, but I don't know why it does that for gnome and not for ordinary ttys.

:s

---

### Post by stylishpants on 2007-05-16
/usr/bin/vi is just a symlink to vim, at least by default.

If you start vim as "vi", it runs in a special vi-compatible mode, in which the arrow keys don't work as you expect in insert mode.

You probably want to put this command in your ~/.vimrc file:

```

set nocompatible

```

Try entering this command in command mode first to see if it fixes the problem.

---

