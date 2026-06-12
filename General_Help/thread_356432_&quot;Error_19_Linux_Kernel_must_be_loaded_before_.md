---
title: "&quot;Error 19: Linux Kernel must be loaded before initrd&quot;"
date: 2007-02-08
forum: General Help
---

### Post by Phrawm48 on 2007-02-08
Ubuntu 6.06 LTS, 2.6.15-27-386

I shut down my system properly last night and this morning I can't boot normally.

I can boot via recovery mode (I'm typing this from Linux right now, so Linux isn't completely broken), but, IF I select Grub's normal Linux boot option, THEN I receive a message that says, "error 19" followed by the statement:

> Linux Kernel must be loaded before initrd
initrd /initrd.img 2.6.15-27-386

What the heck is going on?  As I said, I can boot via the second "recovery mode" option in Grub, but my normal boot mode peremptorily refuses to work.

More important, how can I fix this?

Cheers & thanks,
Ric
SFO

---

### Post by Phrawm48 on 2007-02-08
Never mind -- I found it.

I was using VIM to edit *menu.lst* (adding a vga= parameter) and managed to reverse the sequence of the *kernel *and *initrd *lines in the default section of the file.  (VIM's tricky that way...)

I put the lines back in the correct order and that fixed it.  And learned a couple of things along the way...

Cheers & thanks,
Riley

---

