---
title: "Change Deault OS"
date: 2007-01-29
forum: General Help
---

### Post by baseballmanager on 2007-01-29
I have Ubuntu installed on a partition on my hard drive along with Windows XP.  I want to change the default OS to Windows but I can't.  I looked in the documentation and it told me to do several things but the programs that I needed to use weren't installed and I can't download them.  Can you tell me an alternate way to change the default OS?

---

### Post by scrooge_74 on 2007-01-29
you have to cd into /boot/grub

then sudo nano menu.lst

then you have to change the line which says >
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default         0

you have to change that "default 0"  to the correct line you want to boot first, if XP is listed in the #3 or #4 spot that is the one to put there.

In any case do a backup of the file before any changes

---

### Post by baseballmanager on 2007-01-29
Thanks.  I tried that but I couldn't save the changes.  Is there a way to do that?

---

### Post by scrooge_74 on 2007-01-29
did you type sudo in front of the nano command?

---

### Post by baseballmanager on 2007-01-30
I tried that but it still said that I didn't have the permission to execute that command.

---

### Post by scrooge_74 on 2007-01-30
are you using another user than the one that was use to install the system?  The first user is the one who has sudo rights.  Try booting in recovery mode and you should be able to make the changes and save them.

---

