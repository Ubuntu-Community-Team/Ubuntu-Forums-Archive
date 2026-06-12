---
title: "OpenOffice, NFS, and files missing..."
date: 2005-04-18
forum: General Help
---

### Post by code on 2005-04-18
Hi,

I have a couple machines with Hoary installed (both i386 and amd64,) and user home directories are served via NFS from SGI Irix. Quite reliably, some directories with spaces (but not all!) will not show up in OpenOffice's File Open/Save dialogs.

For example, the directory "My Documents" is visible in nautilus (File Manager,) and from other apps using the gnome file dialogs, permissions look correct, etc., but the directory won't show in OO.

This problem also apparently occurs on Fedora Core 2 (in a couple other apps, also,) but not Fedora Core 3. When the directory is hosted from another Linux machine, the problem does not occur. Running strace, OO will lstat() everything when bringing up the dialog, except for the directories that don't appear. I can't find any bug reports on this one, anyone else see this and/or have a solution?

---

### Post by diebels on 2005-04-18
Does fedora core 3 use the same file dialogs?
What charset is the SGI Irix machine using on filenames?

---

