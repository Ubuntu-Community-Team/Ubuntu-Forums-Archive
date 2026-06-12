---
title: "Symbolic links (ln -s) vs mount --bind"
date: 2007-05-18
forum: General Help
---

### Post by dudinatrix on 2007-05-18
We currently have symbolic links to directories, and need to rethink things a little because when trying to lock an FTP user into a chroot jail, the symbolic links don't work since they appear to be "outside" of the jail.

So I found that "mount --bind" basically mounts a directory to another path, and would work in the chroot jail environment. Is there a pro or con when using one over the other? I think "mount --bind" wouldn't have that same symbolic link limitation, but is there a drawback to using it?

---

### Post by lloyd_b on 2007-05-18
> We currently have symbolic links to directories, and need to rethink things a little because when trying to lock an FTP user into a chroot jail, the symbolic links don't work since they appear to be "outside" of the jail.

So I found that "mount --bind" basically mounts a directory to another path, and would work in the chroot jail environment. Is there a pro or con when using one over the other? I think "mount --bind" wouldn't have that same symbolic link limitation, but is there a drawback to using it?

"mount --bind" was created to (among other things) allow the equivalent of a symlink from within  a chroot jail. 

Note that hard links ("ln" without the "-s") option can also cross a chroot boundary, but hard links only work within the same file system, while symlinks and remounts can connect to any file regardless of what file system it's in.

The only real disadvantage of a remount is that it doesn't persist across reboots - you'll have to have a shell script to execute any required "mount --bind" commands after a reboot.  

There's probably some system overhead involved in remounts, but unless you've got a very large number of them this should be trivial.

Lloyd B.

---

### Post by brennydoogles on 2007-05-26
> **lloyd_b said:**
> "mount --bind" was created to (among other things) allow the equivalent of a symlink from within  a chroot jail. 

Note that hard links ("ln" without the "-s") option can also cross a chroot boundary, but hard links only work within the same file system, while symlinks and remounts can connect to any file regardless of what file system it's in.

The only real disadvantage of a remount is that it doesn't persist across reboots - you'll have to have a shell script to execute any required "mount --bind" commands after a reboot.  

There's probably some system overhead involved in remounts, but unless you've got a very large number of them this should be trivial.

Lloyd B.

So if I created a Symbolic link from within my EXT3 Linux filesystem to my windows NTFS File system, would windows recognize it, or is it only that linux can link to other file systems??

---

### Post by lloyd_b on 2007-05-26
> So if I created a Symbolic link from within my EXT3 Linux filesystem to my windows NTFS File system, would windows recognize it, or is it only that linux can link to other file systems??

Just to clarify what a symlink (Symbolic Link) does - it creates a "pointer", that tells the system "when I try to access the symlink, access this other file instead".  So, you can easily create symlinks within an EXT3 file system pointing to files in NTFS, FAT32, or any other type of filesystem that Linux can mount.

There is no "backward link" created, however, so while you have a pointer in the EXT3 filesystem pointing to the file in the NTFS filesystem, the NTFS filesystem is completely unaware that the symlink exists.

Lloyd B.

---

