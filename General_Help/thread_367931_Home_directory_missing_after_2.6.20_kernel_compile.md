---
title: "Home directory missing after 2.6.20 kernel compile"
date: 2007-02-22
forum: General Help
---

### Post by kdawg on 2007-02-22
I recently compiled the 2.6.20 kernel from the source at kernel.org.  I followed all the tutorials I found on the forums and it worked fine.  I installed the kernel image and headers and rebooted and it boots fine.  When it gets to my Gnome login screen, Itype in my username and password and I get the following error, which I have seen a few other places in the forums:

```
"Your home directory is listed as: '/home/kevin' but it does not appear to exist. Do you want to login with the /(root) directory as your home directory?
It is unlikely anything will work unless you use a failsafe session."
```

Selecting yes gives this error:

```
"User's $HOME/.dmrc file is being ignored. This prevents the default session and language from being saved. File shoud be owened by user and have 644 permissions. User's $HOME directory must be owened by user and not writable by other users."
```

Then it halts and gives an error saying that the session lasted less then 10 seconds and quits back to the login screen.

If I select Failsafe gnome or failsafe terminal session, it does the same exact thing.

When I reboot and use my existing kernel, 2.6.15-28, everything is perfectly fine and there are no errors.

I do have my home directory on a seperate hard disk, hdb1, and the root directory is on hda1 with swap on hda5.  All using Ext3 and I have Ext3 selected from the make menuconfig when I compiled the kernel.

Help!!  Thanks!!

---

### Post by kdawg on 2007-02-23
Update:  I recompiled and patched it with the 2.6.20-1 patch and used make xconfig instead of menuconfig, and it works great now.  There must have been some setting in the filesystems section that I didnt have checked...... strange.  Any comments?

Now the only problem I have is that I never compiled vesa drivers with it, so I have no pretty splash screen when I boot or shutdown... oh well, guess I'll reconfigure and recompile again!!

---

