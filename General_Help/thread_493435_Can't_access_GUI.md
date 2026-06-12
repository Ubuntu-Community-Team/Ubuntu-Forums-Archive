---
title: "Can't access GUI"
date: 2007-07-05
forum: General Help
---

### Post by LossForWords on 2007-07-05
Ok, here's my problem: every time I turn on my computer, Ubuntu boots as normal - until it comes to the point where it would normally display the GUI. Instead, I am greeted by the text interface and this:

> kinit: name_to_dev_t(/dev/disk/by-uuid/c2ba81c7-7b01-448a-aad5-3b246fa04210
kinit: trying to resume from /dev/disk/by-uuid/c2ba81c7-7b01-448a-aad5-3b246fa04210


I have absolutely no idea what to do. Can anyone here help me fix whatever might be causing this?

---

### Post by DagMan on 2007-07-06
I don't know however I would try first, at the grub screen, hitting e, then selecting the kernel line and hitting e again.  Then type noresume at the end of it, hit enter, type b to boot the system with that paramater, and if it works we can go from there, if not then hopefully someone else knows.
Editing the grub menu this way will not permanently change the file and will only apply to that one boot so it's safe to do.

---

### Post by iver2435 on 2007-07-07
I had this exact same problem and it was right after a fresh install of Ubuntu.....

Following DagMan's instructions solved my issue 100%  Thanks a lot!

---

