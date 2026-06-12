---
title: "vim shift-o lag"
date: 2008-03-13
forum: General Help
---

### Post by peterff on 2008-03-13
Hi,

I'm having a problem with vim which does not occur in gvim and which is present when running vim in both rxvt-unicode and gnome-terminal. If, within a second of switching from insert mode to command mode, I press shift-o to open a new line above the current one, I see an O inserted into the text for a second before it opens the line and puts me in insert mode. I've tried running vim without my .vimrc and .viminfo.

I realize this is a long shot, but I appreciate any thoughts.

---

### Post by peterff on 2008-03-13
Well, on the off chance that anyone else has this problem, here's an explanation: [http://tech.groups.yahoo.com/group/vim/message/88306](http://tech.groups.yahoo.com/group/vim/message/88306)

Apparently Esc-Shift-o is the beginning of another command, so vim waits to see if you're going to continue the sequence or not. I haven't found a solution, however.

---

