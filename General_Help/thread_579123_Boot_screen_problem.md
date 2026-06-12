---
title: "Boot screen problem"
date: 2007-10-18
forum: General Help
---

### Post by logreeval on 2007-10-18
When  one of my boxes boots, it is just blank, no boot screen.

It doesnt shutdown with a screen either.

Running gutsy...anyone know how to fix this?

---

### Post by logreeval on 2007-10-18
Anyone?

---

### Post by logreeval on 2007-10-22
bump

---

### Post by dayvy on 2007-10-22
[http://ubuntuforums.org/showthread.php?t=581075&highlight=usplash.con](http://ubuntuforums.org/showthread.php?t=581075&highlight=usplash.con)

---

### Post by logreeval on 2007-10-25
That didn't work for me :-\

When I shut down I get the words like Nework connectioin............Closed

And all the other stuff like that...

---

### Post by mahousaru on 2007-10-25
Can you try editing the boot options by changing splash into nosplash=y and add a vga=771

U can edit the boot options by pressing ESC right when you switch it on.  Press e to edit, cursor down to the line that starts with kernel, press e again.  Make the changes and press enter to save them for just this boot.

The vga=771 should force it into a more friendly 800x600 mode.

---

### Post by logreeval on 2007-11-01
still no splash screen :(

---

### Post by logreeval on 2007-11-08
bump

---

