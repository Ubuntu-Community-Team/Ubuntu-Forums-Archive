---
title: "Ubuntu (Linux) Chmod using octal notation"
date: 2013-03-10
forum: General Help
---

### Post by Femi Adegbite on 2013-03-10
I have ran a command using chmod ( change mode) in Ubuntu trying to get the permissions results

when I type " chmod 755 testfile" into gmone terminal 

The results was " total 0". I was expecting to see somethings like this " -rwxr-xr-x 1 femi femi 0 2010-10-09 19:15 testfile".

Can you please explain why and what I need to do to get the permissions ( -rwxr-xr-x) appears

---

### Post by lisati on 2013-03-10
*Thread moved to **General Help**.*
I've moved your question to its own thread, because it doesn't appear to be directly related to the thread in which you originally posted it.

If you want to read up on file permissions, you might find the following interesting:
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by deadflowr on 2013-03-10
Where are you in the directory?
total 0 means you're sitting in an empty directory. Which is why it shows 0, nothing is in it.

You can run:
```
pwd
```

which will tell you where you are currently sitting in terms of directories.

---

### Post by efflandt on 2013-03-11
Your syntax is correct assuming you were in the directory (with typical rwx permission for you or your group) containing **testfile**. If it was not successful or the file did not exist, you should have gotten an error from chmod.

Were you doing this on a Linux or non-Linux file system? You cannot set permissions for individual files or directories on FAT or ntfs file systems (only blanket permissions on all directories and/or files based on mount options)

```
efflandt@XPS8100-1204:~$ ls -l testfile
ls: cannot access testfile: No such file or directory
efflandt@XPS8100-1204:~$ touch testfile && chmod 755 testfile
efflandt@XPS8100-1204:~$ ls -l testfile
-rwxr-xr-x 1 efflandt efflandt 0 Mar 10 23:41 testfile
```

chmod +x testfile would work as well, but since by default files in your home directory are owned by you and your own group, would end up with -rwxrwxr-x

---

