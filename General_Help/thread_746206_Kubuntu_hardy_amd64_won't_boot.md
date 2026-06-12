---
title: "Kubuntu hardy amd64 won't boot"
date: 2008-04-05
forum: General Help
---

### Post by Dominator86 on 2008-04-05
Hi!

Tried to install the amd64 version of Kubuntu today and at first I was happy because the usplash bug with my graphics card seems now to be fixed.

The installation finished without any error messages so I tried to boot Kubuntu.
After the splash screen the screen went black and I wasn't able to do anything.

So I tried to boot in safe mode.
Everything seems to load fine because of the [ OK ] at the end but after the loading finished (the point where normally the splash screen disappears) I got the following messages:

> EXT3-fs error (device loop0): etx3_find_entry: reading directory #734425 offset 0
stat: cannot stat '/usr/bin/screen': No such file or directory
(bunch of 'No such file or directory' errors here)

followed by a blinking cursor and I wasn't able to do anything again.

I tried it with wubi 455 and 479B. (both with the latest image)

I think I'll stick with the x86 version a little longer ;)



A little 'problem' I also have is that the installer always sets a wrong system time for me.
I live in the CET timezone (UTC+1 standard time / UTC+2 during daylight saving).
But this has most likely nothing to do with wubi.

---

### Post by Dominator86 on 2008-04-08
*bump* :rolleyes:
Sorry for double posting but any ideas?

I'd really like to install the 64bit version of kubuntu because I plan to run a 64bit guest os in virtualbox.

There are only 16 days left to final state and it totally stopped working.
(older versions used to work but with graphics problems)

---

### Post by ago on 2008-04-08
screen should be there it might be that the ISO is in an inconsistent state at the moment. Try with the beta ISO.

---

