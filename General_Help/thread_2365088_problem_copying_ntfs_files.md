---
title: "problem copying ntfs files"
date: 2017-07-02
forum: General Help
---

### Post by cmcanulty on 2017-07-02
I have a external hard drive that has 2 partitions, one is ext4 and one is ntfs. Every time I backup my xubuntu 16.04 laptop I back up my home to both in case I ever need to use it with windows. When I connect the external hard drive to a windows 10 pro system it sees all the ntfs files but when I try to copy the Documents  to the windows computer is says there are no files to copy. Yet I can open them and read them on the windows machine. The windows properties said read only and I change that including sub folders and files but it won't keep the changes and immediately sets it to read only. I have the same username on both computers. Thank you

---

### Post by yancek on 2017-07-02
Are you referring to the folders/files you copied to the ntfs partition on your external drive from the Xubuntu computer and then attached to the windows 10 computer and tried to access them?  Obviously, you would not be able to access the ext4 filesystem from windows, that's default by design of microsoft.

Are you trying to copy from the ntfs partition on the external when booted to windows 10?  How?

Did you change the read-only option in windows?  A default windows system doesn't understand Linux filesystem permissions/ownership so that wouldn't help.

---

### Post by efflandt on 2017-07-02
NTFS does not have and is unaware of *nix like file permissions. When Linux mounts an ntfs (or fat) partition, permissions of directories and files are based on mount options, not original Linux file permissions of files copied to it. If you want to back up something to an ntfs partition and preserve Linux permissions, you would need to do it as a **tar** file (which can also use various methods of compression to reduce file size) to preserve directory and file permissions. For example files or directory structure in a tar file that uses gzip compression would typically end with .tar.gz or that uses bzip would be .tar.bz.  In a terminal see: man tar

I don't know if there is a gui that could make that easier to create than in a terminal, maybe **archiver** which can view things in zip and other archived files.

---

### Post by cmcanulty on 2017-07-02
No I am only trying to copy files from the ntfs partition of the ext hard drive to my windows 10 documents. Windows won't copy the files but lets me open them. As i said I try to change them to not read only in windows but it won't really change them

---

