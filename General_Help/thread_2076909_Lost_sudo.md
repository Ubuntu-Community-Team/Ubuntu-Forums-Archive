---
title: "Lost sudo"
date: 2012-10-27
forum: General Help
---

### Post by disc0tech on 2012-10-27
Hello,

I misguidedly changed the permissions of /etc/sudoers to 444, instead of 440, so that dropbox could back it up.

Now when I try and use sudo I get:

> sudo: /etc/sudoers is mode 0444, but should be 0440
sudo: no valid sudoers sources found, quitting...
sudo: unable to initialise policy plug-in


To make things worse I am unable to boot into single user mode and correct the problem, as I don't get a GRUB menu at startup.  It seems in /etc/default/grub I have

> GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true


...and I can't edit that file as I cannot sudo...

Any ideas anyone?

---

### Post by The Cog on 2012-10-27
I think that holding the left shift key down during boot will get you a GRUB prompt. I seem to remember that down-arrow does too, but I'm less sure about that.

If you really can't get grub to pop up, boot a live CD and edit from there.

---

### Post by disc0tech on 2012-10-27
> **The Cog said:**
> I think that holding the left shift key down during boot will get you a GRUB prompt. I seem to remember that down-arrow does too, but I'm less sure about that.

If you really can't get grub to pop up, boot a live CD and edit from there.

Left shift did work, thanks

---

