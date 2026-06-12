---
title: "Error 17 problems but system.virtual disk still works"
date: 2007-07-24
forum: General Help
---

### Post by CSMatt on 2007-07-24
Lately I've been having problems with GRUB giving me Error 17 messages when I try to boot with one of the installed kernels.  I've tried to defragment and uncompress c:\wubi, but this hasn't solved the problem.  The first time this happened I simply uninstalled Wubi and reinstalled it.  However the Error 17 problem happened again shortly after updating.  The odd thing about it is that I can boot the "Ubuntu (Original kernel)" listing without any problems at all, and system.virtual.disk is accessed by the original kernel without error.  In fact, it seems that the Error 17 messages only appear after I edited menu.lst with WordPad.  The first Wubi installation worked fine for weeks until I edited menu.lst with WordPad to add the "irqpoll" option.  It booted successfully one or two times with this modified menu.lst, but afterward GRUB gave Error 17 messages.  It seems like they happen after one edits menu.lst in WordPad, boots Wubi with the edited menu.lst at least once, boots Windows, and then tries to boot one of the Wubi kernels again.  This seems to be how the Error 17 messages appeared the second time, since the second Wubi incarnation was on my computer for only two days and booted about 5 times.

How can I edit menu.lst without causing these Error 17 messages to appear?  I need the "irqpoll" option or else the boot time slows down significantly.  I can't edit it in Ubuntu because update-grub is always run at shutdown. and it appears that using WordPad is causing the Error 17 issues.  Right now I just always run Wubi with the original kernel, but I would really like to use the updated kernel for security and performance reasons.  I've attached a copy of my menu.lst file so that others can see if there's some flaw in the file itself that's causing this.

---

### Post by CSMatt on 2007-07-24
I also found a "menu.lst.save" file in /boot/grub.  Renaming that to "menu.lst" fixes the issue and I am able to boot successfully.  I've posted the new menu.lst, what was previously "menu.lst.save."  Somewhere along the line the system sees the need to change menu.lst, make a backup copy of menu.lst called "menu.lst.save," and it's this changed menu.lst that is causing the Error 17 prompts.  Why is this?  What would name menu.lst "menu.lst.save," and how do I stop it from modifying menu.lst in the first place?

---

### Post by CSMatt on 2007-07-24
I've experimented more with menu.lst, and it seems that any customized kernel entered into menu.lst, even one that was copied and pasted from the automagic kernel list into an area just before or just after the automagic kernel list, almost always fails (with the sole exception of "Ubuntu (original kernel)").  Editing an automagic kernel within GRUB4DOS always works, although it needs to be done during each boot sequence.  The unedited automagic kernels always work.

---

