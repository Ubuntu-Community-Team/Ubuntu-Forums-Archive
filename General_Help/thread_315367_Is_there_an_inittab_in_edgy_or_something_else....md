---
title: "Is there an inittab in edgy or something else..."
date: 2006-12-09
forum: General Help
---

### Post by encompass on 2006-12-09
[http://ubuntuforums.org/showthread.php?t=89491&highlight=speed+up+ubuntu+feel+it](http://ubuntuforums.org/showthread.php?t=89491&highlight=speed+up+ubuntu+feel+it)
I am trying to edit my inittab to take out my extra tty consoles that I don't use.  with only 200mb ram every drop of ram counts.
But I don't think inittab exists in edgy what is it down and how do I do that same things as in this howto in edgy?
btw with a little searching, it has to do upstart?  Heck, looked for a man page but to no luck.
Moikka.

---

### Post by lloyd_b on 2006-12-09
As I understand it (and there's no guarantee I've got it right), the spawn/respawn of getty's is controlled by the "/etc/event.d/tty..." files.

I think all that's required is to delete the tty... entry from this directory, and then reboot.  Better save a backup copy of it somewhere, though.

Lloyd B.

---

