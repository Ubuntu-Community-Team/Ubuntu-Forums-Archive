---
title: "Problem booting Edgy"
date: 2007-08-03
forum: General Help
---

### Post by garyed on 2007-08-03
I posted this in the Beginners forum but I think this my br a better forum for it since it is quite technical.

My Grub menu comes up & it will let me get into Win XP but it will not let me into Ubuntu.
I get this message:

/bin/sh: can't access tty: job control turned off
(initramfs)
Anyone know what that means & how to fix without a reinstall.

I was running Win98 on one HD & Edgy on the other & dual booting fine.
I reformatted my Windows drive(C) & installed XP.
Then I booted to the Ubuntu 6.10 CD & got to the terminal & did the commands:
sudo grub
find /boot/grub/stage1 " Which returned (hd1,0) "
root (hd1,0)
setup (hd0)
quit

The only thing unusual was the computer locked up shutting down.
I've done this before without a problem but this time it looks like something happened to my Ubuntu startup files.

Any clues?

---

