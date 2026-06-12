---
title: "Terminal unusable; how to fix?"
date: 2012-11-02
forum: General Help
---

### Post by JKyleOKC on 2012-11-02
Somehow, as I attempted to copy a file from /root into my $HOME area via a root-enabled file manager, I managed to bork all of my terminal emulator programs. I'm using 12.04.1 which was just updated a couple of hours ago, and all was working properly until things went sour.

Now, attempting to launch any terminal emulator causes the terminal window to appear for a fraction of a second, then go away exactly as if Ctrl-D had been pressed or "exit" executed automatically. The same thing happens if I use Super-T, the Applications menu, or double-click on the emulator icon in /usr/bin. It makes no difference whether I try xterm, the xfce4 emulator, rxvt, or any other -- all fail in exactly the same way.

Almost everything else seems to be working properly. I suspected I might have accidentally changed ownership of a hidden file in $HOME, but have not found such to be the case. Only .bash_history and .bash_aliases are not owned by me (the aliases file was the one I was copying and history was copied by accident; I deleted history, though, and it made no difference).

However, re-booting into recovery mode shows another inconsistency: if I attempt to boot into the root mode, nothing at all happens. If I try to log in to TTY1 or TTY6, again nothing: I enter my name and password when prompted, and it immediately returns to the login prompt. This may or may not be connected, but it makes troubleshooting and attempts at correction a bit more difficult...

Any ideas?

---

### Post by pqwoerituytrueiwoq on 2012-11-02
boot to recovery mode and drop to root console
```
chown -r jkyleokc:jkyleokc /home/jkyleokc/*
```
a live cd will work if you create a user of the same name on the live cd

---

### Post by JKyleOKC on 2012-11-02
Thanks for quick response! However, dropping to root console wasn't working either.

However, persistence paid off and I found the cause, finally, by commenting out each of the "alias" lines until I found the one from which I had omitted the quote marks! Without them, when .bashrc tried to define the alias, it got executed instead, and its final five characters were ";exit" which did of course shut down the terminal -- and since I had copied it from /root it was also bad there, which made the drop to root unusable. Naturally, it was the latest one I had created...

It's now working right again, and I've learned about one more one-in-a-million situation and what to look for to fix it!

---

