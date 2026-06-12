---
title: "Kernel Panic"
date: 2007-02-11
forum: General Help
---

### Post by RallyMonkey on 2007-02-11
When attempting to start up my computer, it gets to booting the kernel, and then I get this error.

> Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)

And then it just stops on that screen. Does anyone have any ideas as to why this might be?

Thank you.

---

### Post by kidders on 2007-02-11
Hi there and welcome,

It could be a few things, but my interpretation of that error is that the first partition on your primary hard drive (which Ubuntu seems to want to look at) is missing or corrupt. Does that sound possible?

If I saw that message on my own machine, it would make me a little nervous, but it isn't _definitely_ bad:

[LIST=1]
[*]Boot your PC with a Linux boot CD.
[*]Fsck your disk partitions.
[*]Mount them, take a look around, and convince yourself they're okay.
[*]Reinstall your bootloader.
[*]Reboot.
[/LIST]

If you changed something in your BIOS to precipitate the error, you should change it back.

---

