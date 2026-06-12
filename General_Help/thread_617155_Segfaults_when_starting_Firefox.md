---
title: "Segfaults when starting Firefox"
date: 2007-11-19
forum: General Help
---

### Post by Bob Todd on 2007-11-19
Since upgrading to Gutsy, I've found that clicking the panel icons for Firefox often won't start it - it appears in the taskbar briefly, then vanishes. If I keep clicking it it eventually works, but it's really annoying. 
I tried opening it from the Terminal, and the same thing happens, with the terminal saying 'segmentation fault, core dumped'. 

Why is this happening and how can I stop it?

---

### Post by Thyme on 2007-11-19
Hi Bod Todd,

Try and see if all the required runtime dependencies are installed:

ldd /usr/bin/firefox-bin           ( my firefox-bin is found in /usr/lib64/mozilla-firefox/ )

You should  see memory address to the right of the arrow for each library.

---

### Post by Bob Todd on 2007-11-19
Thanks - I did that and two of them, libmozjs.so and libxpcom.so, say 'not found'. How can I install them?

---

### Post by Thyme on 2007-11-19
I think those are both native mozilla libraries, meaning its just your installation of firefox that is a bit wierd.

I would just try reinstalling mozilla and firefox in order to reinstall the missing libraries. Even doing a quick search for mozilla with apt can give you an idea on what to reinstall.

---

### Post by Bob Todd on 2007-11-20
Can you (or anyone else) give me more info? I can't uninstall Firefox from add/remove programs because other applications depend on it, and I really don't want to touch the synaptic package manager unless I know what I'm doing.

---

