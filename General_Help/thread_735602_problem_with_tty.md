---
title: "problem with tty?"
date: 2008-03-25
forum: General Help
---

### Post by tahssarm on 2008-03-25
hey there, i'm new to ubuntu, and no guru at any OS really.

I set up my system to boot both vista and ubuntu 7.10 through wubi, and it worked fine, after i configured the x server as another thread in this forum taught me to do. it worked great, ran way faster than vista has ever done, and i proceeded to install a few things, which may or may not be related to my problem.
i installed a media player that is something like exise or something, i don't remember, and can't check now, b/c i can only boot with vista right now.
i installed VLC player, and flash (not macromedia flash, just the plugin to enable me to play .swf's on firefox).

every time i try to boot up ubuntu, i get the basic stuff, then the ubuntu loading bars, they take forever. then i get a few lines of random whatever (type help for sample commands and such) then this:

 "/bin/sh: can't access tty; job control turned off"
and then immediately below that:
(initramfs)


how do i fix this?

---

### Post by tahssarm on 2008-03-25
bump for great justice.

---

### Post by pointone on 2008-03-25
Right before the BusyBox prompt is started, the boot process should have thrown an error message explaining what went wrong. Please post a few more lines of the output.

---

