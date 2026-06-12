---
title: "zsh and bindkey -v"
date: 2006-08-21
forum: General Help
---

### Post by nukethewhales on 2006-08-21
When using zsh, if I set it to be in vi mode with 'bindkey -v', on Ubuntu I run into a really odd behavior.  When I go to the previous command in the history, the cursor is reset to the beginning of the line, instead of the end like it is supposed to be.  I know it's not my keyboard or other zsh settings, I've tried with a blank .zshrc and just run bindkey -v.  It's not the version of zsh I'm using (it works just fine on Slackware and Gentoo with the same version of zsh), or the terminal emulator - it happens bother remotely (SSH) and locally with gnome-terminal and Konsole.  It appears to be Ubuntu specific.

Does anyone know how to fix this, so that the cursor gets reset to the end of the line when going up/down in the command history, instead of the beginning?

---

### Post by sequethin on 2007-11-09
This is a stale question I know but I found out exactly what causes this. I got help from #zsh on freenode (thanks ft and others) while searching high and low because this was annoying me so much! ;) Note that this "bug" exists in gutsy gibbon as well. I'm not sure it can be called a bug really but it feels like a bug when you are used to the cursor being at the end of a line when you "up arrow" through history.

it's this line in /etc/zsh/zshrc 
```

# ncurses fogyatekos
[[ "$terminfo[kcuu1]" == "^[O"* ]] && bindkey -M viins "${terminfo[kcuu1]/O/[}" vi-up-line-or-history

```


if you comment it out your cursor will appear at the end of the line.

since I have a rather specific zshrc that I carry with me to all my shells (hooray for subversion) I really don't need the global rc file at all, and so as ft suggested in #zsh I have

```
setopt noglobalrcs
```

in my .zshenv


Hope this helps someone!

---

