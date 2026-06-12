---
title: "Simple Backup Problem"
date: 2008-06-11
forum: General Help
---

### Post by Person98 on 2008-06-11
Hi I recently used simple backup to change hard drives however it did not seem to take the programs with it however in both synaptic and add/remove it has them listed as installed but when run they say they are not installed any advice? thank you

---

### Post by defishguy on 2008-06-12
Sbackup using the default backup settings doesn't copy programs, it will only copy the contents of your user folder and a few other directories.  You will need to reinstall the programs that you were using.

---

### Post by Person98 on 2008-06-13
yeah i was suspecting as much, however the problem that I having is that they are flagged as installed in synaptic, so i don't know what is there and what isn't, is there a way to clarify the flags so i can know what I have got?

---

### Post by defishguy on 2008-06-14
I do not think there is a way to let apt know a package really isn't installed.

The best work-around I can think of is to open synaptic and there is a button in the lower right that says "Status"  If you click that button some options will appear in the window above.  Highlight "installed".  This will show you every package that apt thinks is installed.  If you select all of them for re-installation then actually re-install them you'll be in a known config.

This will take a long time but will fix the problem.  Hopefully someone that knows more about apt might make a better suggestion.

---

