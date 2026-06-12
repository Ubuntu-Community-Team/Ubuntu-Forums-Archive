---
title: "jEdit 5.0pre1 on 12.10 (issues with views and GC)"
date: 2013-08-30
forum: General Help
---

### Post by mlntdrv on 2013-08-30
Hi,

jEdit has some strange issue on my xfce 4.10 - when the garbage collector runs, some of the views disappear from the toolbar where the minimised windows reside. However they're still accessible through ctrl+tab and when brought to focus, their minimise button is gone, while the maximise and close buttons are still there. Any ideas?

Cheers!

---

### Post by dragonfly41 on 2013-08-30
I have jedit 4.4.2 on Ubuntu 12.04.   No experience of 5.3 yet.

You could try running [COLOR="#0000FF"]sudo update-alternatives --config java[/COLOR]

to switch to a different java engine.

[http://www.jedit.org/index.php?page=compatibility]("http://www.jedit.org/index.php?page=compatibility")

Also try the jedit forum to look for any issues with 5.3.

[http://community.jedit.org/]("http://community.jedit.org/")

---

### Post by mlntdrv on 2013-08-30
> [COLOR=#0000FF]sudo update-alternatives --config java[/COLOR]found no alternatives.

Later I tried jEdit 5.1.0, but same stuff happens.

---

