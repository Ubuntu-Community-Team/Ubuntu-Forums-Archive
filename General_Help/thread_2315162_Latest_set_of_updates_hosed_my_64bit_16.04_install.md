---
title: "Latest set of updates hosed my 64bit 16.04 install (VMware Fusion / OS X 10.11.5)"
date: 2016-02-26
forum: General Help
---

### Post by crjackson on 2016-02-26
So the updates completed as usual but not it won't load the Ubuntu Desktop or terminal for that matter.

I get the splash screen, then all the text of items that are loading, it completes without errors and goes to a black screen instead of a desktop.

Anyway to fix this without reinstalling?

---

### Post by crjackson on 2016-02-29
No one?

---

### Post by crjackson on 2016-04-26
BUMP

How do I open a vmwharevm file (Ubuntu Install) that won't boot after an upgrade? I just need to grab my T-Bird emails.

---

### Post by crjackson on 2016-05-18
Bump

---

### Post by crjackson on 2016-05-21
Bump

---

### Post by crjackson on 2016-05-31
Bump

---

### Post by The Cog on 2016-05-31
I think I remember that holding down one of the shift keys as grub is loading will make it offer a grub boot menu. Try pressing E (for edit) and editing the boot command, adding the word **single** at the end. This should then boot straight into a root console.

Alternatively, these two links describe getting into recovery mode:
[https://wiki.ubuntu.com/RecoveryMode](https://wiki.ubuntu.com/RecoveryMode)
[http://askubuntu.com/questions/172319/how-can-i-start-in-safe-mode](http://askubuntu.com/questions/172319/how-can-i-start-in-safe-mode)

Hope they help. I see you have been extremely patient.

P.S. failing that, you should be able to get at the files using the live CD, to copy them off for backup.

---

### Post by crjackson on 2016-05-31
Thanks for the reply, I'll try this right now...

---

### Post by crjackson on 2016-05-31
> **The Cog said:**
> I think I remember that holding down one of the shift keys as grub is loading will make it offer a grub boot menu. Try pressing E (for edit) and editing the boot command, adding the word **single** at the end. This should then boot straight into a root console.

Alternatively, these two links describe getting into recovery mode:
[https://wiki.ubuntu.com/RecoveryMode](https://wiki.ubuntu.com/RecoveryMode)
[http://askubuntu.com/questions/172319/how-can-i-start-in-safe-mode](http://askubuntu.com/questions/172319/how-can-i-start-in-safe-mode)

Hope they help. I see you have been extremely patient.

P.S. failing that, you should be able to get at the files using the live CD, to copy them off for backup.

Thanks for the help, I now have full access to my install. I just had to boot into an older kernel and run some updates. It reboot perfectly...:D

---

