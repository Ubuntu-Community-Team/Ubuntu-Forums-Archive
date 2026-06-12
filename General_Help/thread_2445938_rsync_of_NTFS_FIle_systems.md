---
title: "rsync of NTFS FIle systems?"
date: 2020-06-22
forum: General Help
---

### Post by rsteinmetz70112 on 2020-06-22
Can rsync be used to faithfully copy from an ntfs file system to another ntfs file system?

While as far as I know there is no windows implementation of rsync, Linux can read an ntfs file system.
I began wondering if rsync can copy for an ntfs files system on either a Windows OS or Linux to an ntfs files system on Linux.

---

### Post by HermanAB on 2020-06-22
Look for Windows Robust Copy: robocopy

[https://docs.microsoft.com/en-us/windows-server/administration/windows-commands/robocopy](https://docs.microsoft.com/en-us/windows-server/administration/windows-commands/robocopy)

---

### Post by Impavidus on 2020-06-23
rsync is just a fancy tool to copy files. It doesn't care about the underlying filesystem. As long as you have read access on the filesystem you want to copy from and write access on the filesystem you want to copy to, I don't see why rsync wouldn't work. The options to preserve ownership and permissions won't work though, as those aren't supported by ntfs.

---

### Post by lvm on 2020-06-23
> **rsteinmetz70112 said:**
> While as far as I know there is no windows implementation of rsync

There is cygwin ([https://cygwin.com/](https://cygwin.com/)) and there is also WSL on windows 10, both provide fairly robust linux environments on windows including rsync. You can even run ubuntu in WSL.

---

### Post by siepo on 2020-06-23
It also depends on the purpose of the copy. For backing up your projects it is probably ok but I would never use it for Windows OS files: I would not trust a Unix tool to preserve all the particulars of an NTFS filesystem.
Plus, windows may store local times while linux normally stores UTC times. If that is a problem then you can give rsync a --modify-window parameter to ignore time differences up to a certain threshold.

---

### Post by sudodus on 2020-06-23
Copying the directory tree and the files with rsync works well also with NTFS.

But I see a possible problem: The ownership and permissions of Microsoft file systems cannot be managed properly by Linux. So there may be problems for you if there are some [system] files, that must have certain ownership and permissions.

This problem with ownership and permissions affects also rsyncing a linux root file system to a backup drive with NTFS. In this case it works to use tar.

The only full backup of Windows in Linux that I rely on is cloning; [Clonezilla](https://clonezilla.org) is a good tool for that purpose. It is smart enough to copy only used blocks (and skip free blocks in the file systems).

---

### Post by rsteinmetz70112 on 2020-06-23
Thanks. 

My thought was to copy data files, mostly documents and no system files, from a Windows server share to a NTFS file system on Linux to maintain an easily accessible up to date copy. As part of our backup strategy we already do this with samba shares on ext4 files systems. Since most of this data is static over time and kept online for use as required rsync will quickly only update those files that are changed. We do not delete files that are removed. I also want to store it outside the Windows environment as I don't consider Windows particularly safe, no matter what you do to secure it. 

Using tar results in large amounts of duplication and is more cumbersome to retrieve,

---

### Post by sudodus on 2020-06-23
It seems to me that rsync will be excellent for this task :-)

Edit: You may need some special options to avoid unnecessary copying or complaints because of trouble with the ownership and permissions, but it should definitely work.

---

### Post by HermanAB on 2020-06-23
BTW, there is a deduplication utility called hardlink, that uses hard links to replace duplicated files.  It works only on Linux file systems, so here is another reason for you to stop using NTFS.

---

### Post by rsteinmetz70112 on 2020-06-25
> **HermanAB said:**
> BTW, there is a deduplication utility called hardlink, that uses hard links to replace duplicated files.  It works only on Linux file systems, so here is another reason for you to stop using NTFS.

The reason to use NTFS is to preserve windows attributes to the extent possible.

---

