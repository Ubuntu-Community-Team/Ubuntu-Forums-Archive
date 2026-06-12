---
title: "See boot sequence!"
date: 2008-05-02
forum: General Help
---

### Post by vdawg on 2008-05-02
Hi!

I just installed a fresh new Hardy Heron, and so far everything is lookin real good. I was just curious as to how could I get to see the boot sequence (as in all the boot commands) instead of the windows type loading screen.

In fiesty fawn it was automatic, or I used to press 'esc' or something like that.

cheers!

---

### Post by vdawg on 2008-05-03
Bump, this should be a pretty simple thing :p

---

### Post by Zorael on 2008-05-03
Ctrl+Alt+F1 when the usplash starts, alternatively hit F2 in grub and scroll right on the **kernel** line, find and remove **splash**, then hit enter and B to boot. Both are temporary solutions; to make it permanent, you need to edit your **/boot/grub/menu.lst** file.

Make a backup of it, then edit it and find the line starting with '# defoptions'. An example from my menu.lst:
```
## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet **splash** vga=792 resume=/dev/sdb4
```
Your line may vary, of course. Remove 'splash' from the defoptions line, and then enter the following command in a terminal.
```
$ sudo update-grub
```

---

### Post by vdawg on 2008-05-03
Perfect, thank you!

---

