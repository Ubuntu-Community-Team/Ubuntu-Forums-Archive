---
title: "Can someone explain symbolic vs hard links to me?"
date: 2006-12-01
forum: General Help
---

### Post by Peepsalot on 2006-12-01
I just don't really get it.

How do you decide when to use one type over the other.

---

### Post by lloyd_b on 2006-12-01
> I just don't really get it.

How do you decide when to use one type over the other.

99+% of the time, you use symlinks (Symbolic Links).

The only reason for using a hard link is if you've got some software that absolutely refuses to work with the symlink.  For instance, FTP servers typically run in a "chroot'ed" environment (a security feature), and as a consequence cannot follow symlinks that point to files outside of the "/home/ftp" directory structure.  In this case, a hard link resolves the issue.

Lloyd B.

---

### Post by dcstar on 2006-12-02
> **Peepsalot said:**
> I just don't really get it.

How do you decide when to use one type over the other.

Here's my understanding:

A Symlink is essentially a pointer to another directory entry (inode), a hard link is a separate directory entry to the same file information (basically with the inode containing the same file data info).

You can delete the original directory entry and any Symlinks pointing to it will be broken (but still exist), when you remove hard links the file remains until all of its hard links are deleted.

Some programs (not many these days, I believe) don't understand Symlinks and can't follow them to the actual inode data, but they work fine with hard links because they are essentially "normal" directory entries.

IIRC Symlinks can cross physical disks and mounted drives, hard links are restricted to a logical partition.

---

### Post by kpatz on 2007-01-31
As an old-school Unix guy (who used *nixes before symlinks were "invented") I still like hard links more than the average guy, and still tend to use them unless there's a situation where a symlink is better (or the only option, such as crossing filesystems/mounts).

Anyway, here's some pros and cons of each type:

**HARD LINK PROS**

1.  More efficient than symlinks - no additional inode needed, and only space for an additional directory entry, plus fewer lookups when referencing them
2.  A hard-linked file can work with any application, while some apps don't like symlinks
3.  Hard linking is more robust - if some of the file's links are moved or deleted, remaining links are still valid

**HARD LINK CONS**

1.  Can't hard link across filesystems
2.  Can't hard link directories (well, there are ways of doing it, but you'll break things by doing so)
3.  It's more difficult to find all the links to a file if you lose track of them (you can do a find by inode # though).

**SYMBOLIC LINK PROS**

1.  Can create links to *anything*, including directories, /dev nodes, objects on other file systems, mounts, etc.
2.  When doing an ls -l, you can see what the link is linked to

**SYMBOLIC LINK CONS**

1.  Delete or move the file, and any symlinks to the file remain but no longer work
2.  When creating symbolic links, you have to be careful to use full paths, as relative path symlinks can break after you "cd" to another directory.
3.  If you have a symlink to a file that's in a directory you don't have read/search access to, you won't be able to access the file.  To demonstrate:```
kpatz@zuul:~$ mkdir -p $HOME/dir1/dir2
kpatz@zuul:~$ echo "Hi, I'm a file" >$HOME/dir1/dir2/file
kpatz@zuul:~$ ln $HOME/dir1/dir2/file hardlinktofile
kpatz@zuul:~$ ln -s $HOME/dir1/dir2/file symlinktofile
kpatz@zuul:~$ ls -l *linktofile
-rw-r--r-- 2 kpatz kpatz 15 2007-01-31 12:46 hardlinktofile
lrwxrwxrwx 1 kpatz kpatz 26 2007-01-31 12:46 symlinktofile -> /home/kpatz/dir1/dir2/file
kpatz@zuul:~$ cat hardlinktofile
Hi, I'm a file
kpatz@zuul:~$ cat symlinktofile
Hi, I'm a file
kpatz@zuul:~$ chmod 000 $HOME/dir1
kpatz@zuul:~$ cat hardlinktofile
Hi, I'm a file
kpatz@zuul:~$ cat symlinktofile
cat: symlinktofile: Permission denied
kpatz@zuul:~$ chmod 755 $HOME/dir1
kpatz@zuul:~$ rm $HOME/dir1/dir2/file
kpatz@zuul:~$ cat hardlinktofile
Hi, I'm a file
kpatz@zuul:~$ cat symlinktofile
cat: symlinktofile: No such file or directory
kpatz@zuul:~$

```Now, here's a mind twister for you.  What happens when you create a hard link on a symbolic link?

---

