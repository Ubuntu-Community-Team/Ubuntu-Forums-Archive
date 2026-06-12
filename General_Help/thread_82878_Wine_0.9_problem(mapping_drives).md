---
title: "Wine 0.9 problem(mapping drives)"
date: 2005-10-27
forum: General Help
---

### Post by Rahu on 2005-10-27
I just installed the latest wine, and I'm having some difficulties. The first thing I did ws to run winecfg.
```
jeff@ubuntu:~$ sudo winecfg
Password:
Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
Warning: could not find DOS drive for current working directory '/home/jeff', starting in the Windows directory.

```

The config utility still came up just fine, so i fiured it was no big deal. I then tried to map the drives through the config utility and got this error when i clicked apply.

EDIT: also, when i return to the config program, the list of drives is empty.
```
err:winecfg:apply_drive_changes   unable to define devicename of 'C:', targetpath of '/'
err:winecfg:apply_drive_changes   unable to define devicename of 'D:', targetpath of '/media/cdrom0'
err:winecfg:apply_drive_changes   unable to define devicename of 'E:', targetpath of '/media/cdrom1'
err:winecfg:apply_drive_changes   unable to define devicename of 'F:', targetpath of '/media/floppy0'
err:winecfg:apply_drive_changes   unable to define devicename of 'H:', targetpath of '/home/jeff'
err:winecfg:apply_drive_changes   unable to define devicename of 'C:', targetpath of '/'
err:winecfg:apply_drive_changes   unable to define devicename of 'D:', targetpath of '/media/cdrom0'
err:winecfg:apply_drive_changes   unable to define devicename of 'E:', targetpath of '/media/cdrom1'
err:winecfg:apply_drive_changes   unable to define devicename of 'F:', targetpath of '/media/floppy0'
err:winecfg:apply_drive_changes   unable to define devicename of 'H:', targetpath of '/home/jeff'

```

Anyone know what I'm doing wrong?

---

### Post by Klaue on 2008-01-28
I know that this thread is old, but I had the same problem (wine-0.9.46) and this thread shows up quite high in google

what i did to get it to work again: I renamed ~/.wine to ~/.wine_back and ran winecfg, which created a new .wine-directory. then i added the drives i need and closed winecfg again. then i went to ~/.wine_back/dosdevices and deleted everything (using a root-nautilus) and copied the contents of ~/.wine/dosdevices to this directory. then, still in the root-nautius, i changed the owner/file access permissions of the .reg-files in ~/.wine_back to my user/group (funnily enough, they were root only).
after deleting ~/.wine and renaming ~/.wine_back back to .wine, everything went as it should

---

