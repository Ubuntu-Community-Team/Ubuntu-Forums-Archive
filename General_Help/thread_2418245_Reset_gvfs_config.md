---
title: "Reset gvfs config?"
date: 2019-05-04
forum: General Help
---

### Post by MrEgg on 2019-05-04
How can I delete / reset a user's gvfs config?

On Ubuntu 18.04, I am facing the infamous gvfs *General input/output error while accessing /var/user/1000/gvfs/...* when opening a .ods over davs. Ubuntu 18.04 was a clean install, but the /home partition is mounted to the system, and that /home comes a long way (with all sorts of config files dating back to 14.04 that have been carried along over time).

If I umount /home and try to open an ods over davs, it works fine.
If I mount /home and try to open the ods over davs, I get the error. So how can I reset my config so it works with my /home settings?

Thanks

---

### Post by dino99 on 2019-05-04
Possible error comes from ./local/share/gvfs-metadata
For doing a test, you can rename it to 'gvfs-metad' for example, to protect the inside files; and create a new empty gvfs-metadata subdir. Then try again that ods file after opening a new session, and see what warning/error popup (if any).

---

### Post by TheFu on 2019-05-04
Create a new userid, test it.  If something works fine in the new userid, but not in an older one, then the problem is in the config files of the older userid.  Use comparison tools to find which files are the same between the 2 users, Unix systems have 50+ tools for this stuff.  You can narrow down more and more of the files, often by looking at the directory structure and where a file is located.  Bet that's what dino99 did.  Often, the files are text, so you can actually compare them using any of the comparison tools - diff, sdiff, meld, tkdiff, whatever.  If they are binary or that crazy gnome-DB stuff, perhaps dumping all the settings to text from both userids, then comparing that output?

Use the /tmp/ directory for any intermediate files. That's what it is for.

Of course, there is another option.  DON'T USE GVFS.  There are always other options and those other options provide more control, and almost always access to options that allow for 30% or more performance improvements.

---

### Post by MrEgg on 2019-05-05
I tried emptying out .local/share/gfvs-metadata completely, I'm still getting the same error.

> Of course, there is another option. DON'T USE GVFS. There are always other options and those other options provide more control, and almost always access to options that allow for 30% or more performance improvements. 
How do I tell Nautilus not to use GVFS when I want to access a remote davs document on the fly (ie. without having to first mount cifs or sshfs through fstab or terminal)?

---

### Post by TheFu on 2019-05-06
> **MrEgg said:**
> I tried emptying out .local/share/gfvs-metadata completely, I'm still getting the same error.


How do I tell Nautilus not to use GVFS when I want to access a remote davs document on the fly (ie. without having to first mount cifs or sshfs through fstab or terminal)?

You cannot.  If you use a GUI, 95% of the time, that will force GVFS to be used, with the terrible performance and poor controls.

---

