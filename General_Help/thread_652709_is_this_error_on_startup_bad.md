---
title: "is this error on startup bad?"
date: 2007-12-29
forum: General Help
---

### Post by kaston on 2007-12-29
i am running gutsy on a toshiba satellite A100 VA9 and every time i start ubuntu the following error message flashes on my screen (i retrieved it from the system log):

Dec 29 01:47:30 kaston-laptop kernel: [   17.414123] PCI: Failed to allocate mem resource #6:20000@e0000000 for 0000:01:00.0

is this something i should be worried about?  whenever my computer goes into suspend, sleep, or hibernate, i just get a blank screen and have to do a hard restart by holding down the power button.  could this error have something to do with it?

---

### Post by scxtt on 2007-12-29
try running a memtest - see if you get any errors ...

---

### Post by kaston on 2007-12-29
how do i run a memtest?  sorry i'm a relative noob

---

### Post by taurus on 2007-12-29
There should be an option from GRUB menu to test your memory.  Usually, the first option is to boot Ubuntu, the second is to boot into recovery mode, and the third option is that memtest thing.  If you don't see GRUB menu when you first turn on your computer, press Esc to bring up the menu.

---

### Post by yobser on 2007-12-29
Why does kaston need to check memory? I've got the same error
PCI: failed to allocate mem resource #6:20000@e0000000 for 0000:01:00.0

0000:01:00.0 is video adapter. I've got an answer on launchpad forum that it is not reason for loosing any functionality. But I afraid it is reason why I have no success with compiz.

---

### Post by scxtt on 2007-12-29
good point ... i didn't see the (obvious) PCI reference or think about / ask what "0000:01:00.0" might have been ... :oops:

---

