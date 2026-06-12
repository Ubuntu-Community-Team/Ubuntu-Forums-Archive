---
title: "vi command is slow to open files"
date: 2008-03-26
forum: General Help
---

### Post by amitst on 2008-03-26
Hi,

Recently I have noticed that the vi command is opening files after a 2-second delay which is a bit irritating (Ubuntu Gutsy-Gibon). I tried renaming my ~/.exrc file but still the issue remains. So the .exrc doesn't seem to be an issue. Also after opening the file, the editing commands behave normally (no performance issues). Any suggestions?

Thanks,
Amit

---

### Post by scottro on 2008-03-26
You can try checking /var/log/messages to see if there's anything interesting..  Memory or other resources might be an issue too. 

These are all guesses though--the only time I ever ran into anything like that was when a multiboot system wound up removing swap from one of the distros.

---

