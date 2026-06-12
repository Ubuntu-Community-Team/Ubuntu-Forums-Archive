---
title: "Unable to login after power managment change"
date: 2017-01-27
forum: General Help
---

### Post by jyogyo on 2017-01-27
Running ubuntu 16.10 on lenavo x260.

I am in some trouble here, I have some important work on my machine and was trying to disable the password function on awaking from suspend, or to stop suspending altogether. This is due to some buggy behaviour on awaking which I would like to avoid as I have to give a Live presentation with the machine soon.

After altering some of the power settings, the machine now fails to boot ...

Help would be greatly appreciated.

---

### Post by jyogyo on 2017-01-27
Trying to boot in recovery mode, after I enter the root password, the process also fails.

When trying to boot after attempting recovery mode, by selecting the continue normally option, a line in the terminal is visible when the system stops hangs, the cursor just blinks after this line as it does when attempting a normal start.

[ ok ] Stopped User Manager for UID 1000.
[ ok ] Removed slice User Slice of <username>.

---

### Post by ajgreeny on 2017-01-27
If you boot in recovery mode you do not need a root password so something here is not as it should be.

Have you enabled the root account in your system, which we do not condone?
After getting to recovery mode you must run command ```
mount -o rw,remount /
``` to mount the filesystem as read/write in order for any changes you make to take effect; did you do that?

---

