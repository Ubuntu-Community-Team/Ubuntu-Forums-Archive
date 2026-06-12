---
title: "Broken Links"
date: 2013-10-28
forum: General Help
---

### Post by mayagrafix on 2013-10-28
On my desktop I have some links which point to PDF files in my documents folder. After moving those files to another folder, the link path has been broken. 

Is there anyway to reestablish the path to the documents new address or should I delete them (the original desktop link icons) and make new ones?

Thanks for ur help.

---

### Post by TheFu on 2013-10-28
The only OS that I know which has maintained references with "symlinks" is OS/2, even if they crossed partition boundaries.  If the directory entries for both location are on the same partition, then you might want to create a "hard-link" instead, but that technique does NOT work across partitions ... and I don't think that either works to non-file system objects ... so remote links don't work ... er ... except over NFS.

The old symlinks (also called "softlinks") are worthless.

For a greater understanding of how this stuff works, the wikipedia article on each topic really is very good - so is the man page for the **ln** command.  **man ln** will access it.

Symlinks and hardlinks are fantastic tools.

---

### Post by mayagrafix on 2013-10-28
Thanks for the references. I'll make new links. However, I also found this bit of info:
> In Mac OS and some Linux distributions, applications or users can also employ aliases, which have the added feature of following the target, even if it is moved to another location on the same volume.

Is Ubuntu one of the Linux distros with the above mentioned "Alias"?

---

### Post by tgalati4 on 2013-10-29
Alias is typically reserved for an environment variable that you define in a resource file using the *set* command:

```
env
```

This will print out environment variables that you have defined.  Aliases are helpful as shortcuts for common commands.  As far as symbolic links (hard or soft) automatically changing?  I'm not aware of it.  I know under older versions of Mac OS X, you will get a pop-up letting you know that the link is broken and the ability to search for a new file or to delete it.  It may have been modified now to do this automatically, but I don't have the lastest version of OS X.  I don't know of any linux desktop enviroment or file manager that automatically fixes broken symlinks.

---

