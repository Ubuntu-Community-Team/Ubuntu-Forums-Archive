---
title: "Directory not empty error when deleting folder with rm -r and rm -fr"
date: 2015-07-10
forum: General Help
---

### Post by TheWattsMan on 2015-07-10
I've got a folder that will not show any files or subdirectories (though I can get to said directories if I navigate directly to them), and when I attempt to delete it so I can start fresh, I get an error stating that the directory is not empty, whether I use the GUI or command line. Is there any way to force their removal without having to reformat the hard drive?

---

### Post by dino99 on 2015-07-10
is not that folder only used by the system for temporary needs ?; meaning the user/admin cant do tweaks against the system (processes locked by design; linux system security)

---

### Post by papibe on 2015-07-10
Hi TheWattsMan. Welcome to the forum ):P

I would check if there are hidden files.

On the GUI you can press Ctrl+H to show hidden files on Nautilus (file manager).

On the terminal you can list the hidden files with the option -a. For example:
```
ls -a directory
```
Hope it helps. Let us know how it goes.
Regards.

---

### Post by ajgreeny on 2015-07-10
Where is this folder?

You can not rm as user any folders or files in the system that do not belong to you, which usually means everything that is not in your home.

---

### Post by TheWattsMan on 2015-07-11
This is a folder on a ntfs-formatted USB drive mounted with read and write permissons (and I am capable of creating, modifying and deleting other files on the drive), the files are not hidden, and I tried running the command with sudo. Also: had this been a permissions issue, the error message I'd be getting would be "cannot remove {folder}: Permission denied", not "Directory not empty". The folder is a windows steam library, so nothing would be using it either (which, again, would be a different error message, but I'm sure it'll come up at some point).

---

