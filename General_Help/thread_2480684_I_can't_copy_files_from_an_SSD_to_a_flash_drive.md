---
title: "I can't copy files from an SSD to a flash drive"
date: 2022-11-06
forum: General Help
---

### Post by pizzawithdirt on 2022-11-06
Hey, the problem is when I try to copy it  the error [HTML]"Could not write to /run/media/pizzawithdirt/usb-drive/x64/F6flpy-x64 ( Intel® VMD)\."[/HTML] How can I fix this problem? The USB drive uses the NTFS file system and the GPT partition table if that’s necessary. Thanks.

---

### Post by TheFu on 2022-11-07
Likely a mount options problem which leads to a permissions issue.
a) what are the permissions on the target directory?
b) what are the options used to mount the target file system?

Typically, if you mount using the GUI, root:root will be the owner and no other users can write to that file system.  Through mount options, we can specify a different owner for all files and directories, which will allow creating files (i.e. copying onto) the storage.

In short, don't use the GUI to click-to-mount non-native file systems like FAT32, exFAT, or NTFS.  This issue has existed for many years. There are many threads in these forums with exact commands to mount NTFS storage.


Of course, those are just my initial guesses.  If the program used to copy the data is a snap package, then it could be that access to the target location is not allowed by the snap confinement settings.  You can see which programs are installed as snap packages using 'snap list'.  For some reason, I thought xubuntu wasn't using snap packages very much, but many things have changed the last few years.  

Without knowing the specific release and DE being used, these are all guesses.  always, always, always, include at least that minimal information in posts. You'll get better answers.  'inxi -bz |head -2' can provide that basic information.

---

