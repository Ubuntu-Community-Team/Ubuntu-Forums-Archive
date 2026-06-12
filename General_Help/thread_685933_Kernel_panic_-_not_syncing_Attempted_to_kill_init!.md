---
title: "Kernel panic - not syncing: Attempted to kill init!"
date: 2008-02-02
forum: General Help
---

### Post by grapeape25 on 2008-02-02
I just rebooted my computer after running the "envy" script, and now I can't do anything, I don't know if running the script is the problem though, because I rarely reboot. I booted normally and it just froze on the screen with the loading bar (in the same spot, right at the start). I also tried selecting the recovery mode, which is where it showed this error.

Here is what it says:

> EXT3-fs error (device sda2): ext3_get_inode_loc: unable to read inode block - inode=3457577, block =6914067.
Kernel panic - not syncing: Attempted to kill init!

I don't know what to do, since there is no way (that I can find) where I can access a command line. Is there any way I can recover my data or even fix this?

---

### Post by grapeape25 on 2008-02-02
Anyone? My other computer does not work at all... do I need to reinstall it?

---

### Post by pointone on 2008-02-03
Try booting from the Live CD and run the command:

```
sudo fsck -C /dev/sda2
```

---

