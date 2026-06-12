---
title: "post-removal script error caused by undeletable file"
date: 2005-04-07
forum: General Help
---

### Post by josel on 2005-04-07
The last day or so i have a problem with menu-xdg. I can't upgrade it and removing/installing other packages is not always possible because of conflicts with menu-xdg.
Post-removal fails with not empty dir  '/var/lib/menu-xdg/applications/menu-xdg' (error message in danish)

The culprit is the file "X-Debian-Apps-Net-mozilla_navigator.desktop". I cannot delete this file. Get an error saying the file does not exist.
If I, in mc, choose to edit the file and save the changes then i get to identic files. Size etc are exactly the same and i can delete the one but the other relmains.

Looking at inodes gives me identic inodes for two files :-)

```
root@pollux:/var/lib/menu-xdg/applications/menu-xdg # ls -li
totalt 8
6194 -rw-r--r--  1 root root 3 2005-04-07 13:18 X-Debian-Apps-Net-mozilla_navigator.desktop?
6194 -rw-r--r--  1 root root 3 2005-04-07 13:18 X-Debian-Apps-Net-mozilla_navigator.desktop?
root@pollux:/var/lib/menu-xdg/applications/menu-xdg #
```

If i run "rm -f *" one file remains.

Any ideas on how to force a delete of this file or how to surpass the post-removal script so i at least can update menu-xdg and avoid the file problem?

---

### Post by az on 2005-04-07
The removal scripts are in

/var/lib/dpkg/info

Is this a universe package from Hoary?  If so, maybe you could mention it on freenode
#ubuntu-motu

Maybe it can be fixed before the freeze, if it is not already fixed.....

---

### Post by josel on 2005-04-07
Thanks. 
I did "solve" the problem installing software but editing the relevant script. 
The problem does not seem to be menu-xdg but a filesystem related problem.The identical inodes and that a file that cannot be deleted must be it and reiserfs  3.6 problem i think. Any ideas on how i can force the deletion of that file?
**Debugfs** and **clri** didnt do it - complains about filesystem not open.

---

### Post by maqi on 2005-04-07
To check your file system mount your drive as read only and try:
```
$ reiserfsck --check /dev/hd??
```

This will report without actually trying to fix anything - but won't work on a drive mounted write permissions. See also 'man reiserfsck' and google :)

maqi

---

### Post by josel on 2005-04-07
Did the fsck thing  yesterday and nothing detected. Even google didnt have answers.. but there must be a answer to how to delete inodes directly:-)

---

