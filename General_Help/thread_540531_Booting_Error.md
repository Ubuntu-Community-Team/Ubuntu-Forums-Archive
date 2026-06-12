---
title: "Booting Error"
date: 2007-09-01
forum: General Help
---

### Post by Knowmee on 2007-09-01
I had to shut down my PC improperly (holding the  button in) because of a hard drive problem, anyway when I booted Ubuntu again, here's whats happened:

(After the loading screen with Ubuntu Icon/Orange loading bar)
File System error.
Checks errors.
Root File System Failed.
Says to do manual check.
Says Apt-Get not installed.
Tells to install manually (apt-get install apt).
Says command not found when typed.

--   I'm F00ked :)   --

Any help appreciated.

---

### Post by merlinus on 2007-09-01
Can you boot into Recovery Mode from the grub menu?

-merlin

---

### Post by Knowmee on 2007-09-01
If I do it just checks the file system like it does with Normal mode, and everything i posted above happens.

---

### Post by merlinus on 2007-09-01
You might try booting from the live cd and running fsck on your ubuntu partition.

If that does not work, I suggest you use a disk recovery tool such as sysrescuecd to save your data, and reinstall.

-merlin

---

### Post by Knowmee on 2007-09-01
Ok, thanks I'll give it a try :).

---

### Post by Knowmee on 2007-09-01
Just on the bootdisk now, looked up fsck on the help, and while I think I have a basic idea of what to do, I'm not entirely sure, and considering it's doing something to my Ubuntu partition I'd rather be certain before doing it.

I assume I need to do this: check a Linux ext2/ext3 file system (which is what the help guide says).

Can anyone help me :confused:

---

### Post by merlinus on 2007-09-01
Yes.

There may be some risk involved, but without fixing the errors that may have been caused by your hard power off, what else are you going to do?

You might try to manually mount the partition so you can backup your data, but ubuntu will refuse to mount partitions that have defects.

-merlin

---

