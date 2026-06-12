---
title: "rsync not copying everything"
date: 2021-04-11
forum: General Help
---

### Post by DrScum on 2021-04-11
Ubuntu 18.04 
rsync version 3.1.2 protocol version 31
Problem: when copying files to a samba share in some cases only empty directories are copied. 
I am using the Grsync GUI (V 1.2.6) to set up the session
how do I diagnose and preferentially fix this problem?

---

### Post by HermanAB on 2021-04-11
There are multiple underlying file system issues that can prevent copying.  Rsync can only copy that which it has been granted access to.  Even when running as root, SELinux or AppArmor can still prevent access to some resources.

You can run rsync from the command line with the -vn options to see what it will do, without actually doing it.  See the man page for details.

---

### Post by SeijiSensei on 2021-04-11
Samba shares, like all Windows-based filesystems, are not entirely compatible with *nix file systems. In some cases I've had to ZIP directories on NTFS filesystems and use rsync to transfer the ZIPs. I assume you can copy files to the target location manually from a file manager or the command line so permissions aren't a problem. I suppose the user running rsync may not have permissions to some of the files being transferred as well. Using -vn is very valuable to diagnose these problems.

If you are having permissions issues try running the transfer as root.

---

### Post by rsteinmetz70112 on 2021-04-11
What are the underlying file systems on both ends of the transfer? 

My samba shares are all ext4 (although I've used other file systems in the past) rsync can easily copy everything from one ext4 to another. It can have problems between NTFS and any Linux file system. Also on the Linux filesystem check to see if any acls are set incompatible acls can cause problems..

---

### Post by TheFu on 2021-04-11
> **rsteinmetz70112 said:**
> What are the underlying file systems on both ends of the transfer? 

My samba shares are all ext4 (although I've used other file systems in the past) rsync can easily copy everything from one ext4 to another. It can have problems between NTFS and any Linux file system. Also on the Linux filesystem check to see if any acls are set incompatible acls can cause problems..

More and more lazy installation guides are using ACLs, I've been seeing the last few years.  For people that just want to copy/paste without understanding instructions, it certainly gets them to the working solution, but can break all those other pesky things like ... er ... backups.  Which seems to be fine, since the vast majority of people don't appear to actually do backups, then test them.

If NTFS or FAT-whatever (exFAT, FAT32, etc) are involved, filenames that are completely fine on Unix file systems sometimes don't work at all on NTFS or FAT-whatever.  Every file system has limitations. It is just that the Unix-family file systems have fewer limitations in the name, depth, filesize, and total files allowed, and POSIX permissions/ACL/xattr areas.

In short, stay with Unix/Linux file systems whenever possible.

---

