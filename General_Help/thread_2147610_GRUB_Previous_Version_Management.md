---
title: "GRUB Previous Version Management"
date: 2013-05-22
forum: General Help
---

### Post by iNate71 on 2013-05-22
I recently upgraded my kernel and it caused tons of issues. I didn't know about GRUB's "Previous Versions of Linux" though. I was able to boot into the older version of the kernel. I have no intentions on upgrading the kernel now--however, I can't figure out how to remove the new version of the kernel from GRUB's menu and move the old kernel version back to the standard location in the menu. I've tried GRUB Customizer, but I can't seem to get it to work as it doesn't actually allow me to change anything (tried running as superuser--still nothing). 

Any help would be appreciated!

---

### Post by deadflowr on 2013-05-22
Try this
open up the file /etc/default/grub as root.
Either sudo nano /etc/default/grub.
Or gksudo gedit /etc/default/grub.

And change the line GRUB_DEFAULT=0, to GRUB_DEFAULT=saved.
Then add this line:
```
GRUB_SAVEDEFAULT=true
```

This should allow you to boot into the last booted instance again without having to scroll for it.

---

### Post by ajgreeny on 2013-05-22
Just uninstall the kernel that does not work for you, and you will automatically be back to where you were.

You will then either need to pin your kernel version to the one that works or just manually remove the kernel update from the update manager each time.

To pin an example package version add these lines to  /etc/apt/preferences:
```
Package: linux-image-3.2.0-23-generic
Pin: 3.2.0-23.36     #(number from repos)
Pin-Priority: 1001
```

---

### Post by iNate71 on 2013-05-22
> **deadflowr said:**
> Try this
open up the file /etc/default/grub as root.
Either sudo nano /etc/default/grub.
Or gksudo gedit /etc/default/grub.

And change the line GRUB_DEFAULT=0, to GRUB_DEFAULT=saved.
Then add this line:
```
GRUB_SAVEDEFAULT=true
```

This should allow you to boot into the last booted instance again without having to scroll for it.

Then how will I be able to boot into Windows?
The line (GRUB_DEFAULT="saved") was already there and already like that. I didn't add the other line yet.

> **ajgreeny said:**
> Just uninstall the kernel that does not work for you, and you will automatically be back to where you were.

You will then either need to pin your kernel version to the one that works or just manually remove the kernel update from the update manager each time.

To pin an example package version add these lines to  /etc/apt/preferences:
```
Package: linux-image-3.2.0-23-generic
Pin: 3.2.0-23.36     #(number from repos)
Pin-Priority: 1001
```

I don't know how to uninstall the kernel. I couldn't reinstall the older kernel for whatever reason. Wouldn't it just be easier to edit the GRUB menu?

---

### Post by deadflowr on 2013-05-22
The saved default option only sets the system to load the last session you used. It doesn't prevent you from choosing another session.
However the next session you choose will be the default upon the next boot.
And so forth. Every time you switch a session, the new session is the new default to which the boot will load from.

Unfortunately I don't know how to switch default lines with the previous kernel submenu.
Before, you could do this with GRUB_Default=0,1,2,3,4 depending on the line in grub you wanted to run from.
But with the previous kernel option  I don't know if it'll run from there.

There's always a custom menu option.

---

