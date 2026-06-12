---
title: "xterm automatically disowns programs that are run in the background"
date: 2014-01-23
forum: General Help
---

### Post by thimble on 2014-01-23
Hi,

Whenever I start a program in the background in xterm, for example,

$ emacs &

I can close the xterm window and have the program, emacs in this case, still running.

I recently tried gnome-terminal, and the behavior is different: once the gnome-terminal closes, emacs will also close.

I read about how the gnome-terminal behavior is expected: when gnome-terminal closes, it sends a SIGHUP to the background process to kill it. However, I can't figure out why this doesn't happen with xterm. It's almost like xterm automatically runs a "disown" right after executing something in the background.

I am using stock Ubuntu 13.10, with stock bash, stock xterm, and stock gnome-terminal. I've been using Ubuntu for quite a few years now, and xterm has always had this behavior.

Any ideas why xterm automatically disowns child (background) processes so that they remain running after closing the xterm?

Thanks for your help.

---

### Post by tgalati4 on 2014-01-23
*xterm* has been around a long, long time.  I used it in the early 80's on Unix workstations.  It's default behavior was for the shell to spin off child processes automatically.  If the network went down (which it did in the early days of the internet), you could log back in, start your xterm and have your jobs still running and waiting for you.  In gnome-terminal, shell processes are children of the parent and will get terminated when the terminal is closed.  I'm not sure why it was programmed this way, perhaps for better security.

*xterm* uses /bin/sh instead of *bash* as the default shell, so that may be the difference.

---

### Post by thimble on 2014-01-24
Hmm. I wish gnome-terminal could spin off child processes automatically like xterm. I don't really see any benefit in not doing so.

Thanks for the info.

---

### Post by Impavidus on 2014-01-24
If you don't close the terminal by clicking the little button in the top bar, but by closing the shell (giving the **exit** command), background processes will continue running. At least, that's what happens with an xfce-terminal and a bash shell. I don't know the internal details.

---

### Post by thimble on 2014-01-24
Your tip also works with gnome-terminal. Thanks so much for your input.

---

