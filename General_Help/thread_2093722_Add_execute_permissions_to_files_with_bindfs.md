---
title: "Add execute permissions to files with bindfs"
date: 2012-12-11
forum: General Help
---

### Post by ksemb on 2012-12-11
Dear all,

I would like to use bindfs to remount a directory with execute permissions added to all files.

For this I use
```
sudo bindfs -f -p a+x ~/src /mnt
```However,  execute flags are only added to files which already  have at least one execute flag (user, group or other) already set. Files  which have no execute flag in the original directory still have no  execute flag in the /mnt directory.

Can somebody please tell me what I am doing wrong?

Cheers,
Klaus

---

### Post by TheFu on 2012-12-11
I had to look up bindfs - interesting. I can definitely see a use. Thanks.

Reading the man page, this jumped out:
<quote> A chown/chgrp call will only succeed if the user  has        enough  mirrored permissions to chmod the mirrored file AND the mounter        has enough permissions to chmod the real file.</quote>

Also, if your userid is not the owner for /mnt, then I doubt that mounting ~/src onto /mnt will work.  Is it possible those arguments are backwards from what you intend?  It seems that the original file system is mounted with the non-FUSE driver on ~/src/ . Is that really where it is already mounted?

If these ideas don't help solve the issue, perhaps if we knew the actual file system type (ext2, 3, 4, btrfs, ntfs, vfat, .... ) that is the source and the top level permissions where it is already mounted, then we'd have a better chance suggesting a solution?

---

### Post by ksemb on 2012-12-12
Hi TheFu,

Thank you for your suggestions.

> A chown/chgrp call will only succeed ...I would like create a view onto the original files where they all have execute permissions, I do not want to chmod or chown the files after the mount. And as I mount as root (see the sudo), there should be no problem with privileges.

> Also, if your userid is not the owner for /mnt, then I doubt that mounting ~/src onto /mnt will workMounting  works fine as except that execute flags are not added if the file does not have at least one execute flag already set...

> If these ideas don't help solve the issue, perhaps if we knew the actual file system typeI tried ntfs and ext3 as source file systems, and the behaviour was exactly the same there. My target file system (/mnt) ist ext3.

The issue is still not solved, so it would help me to hear further suggestions ....

Cheers,
Klaus

---

### Post by TheFu on 2012-12-12
I'm stumped.  

You've probably already seen this article: [http://www.redbottledesign.com/mirroring-files-different-places-links-bind-mounts-and-bindfs-0](http://www.redbottledesign.com/mirroring-files-different-places-links-bind-mounts-and-bindfs-0) 

Have you tried using the longer option names?
Have you tried contacting the tool author?
Perhaps someone else can help?

---

### Post by Morbius1 on 2012-12-12
bindfs has some rules and syntax that can be perplexing at times. As you have found out an a+x is always interpreted as an a+X ( big X ) so all directories are set as executable but only files that were executable to begin with are set to executable. 

But it's not a persistant rule. For example if I create a bindfs to one of my own directories with another option:
```
sudo bindfs -o perms=a+x,create-with-perms=a+x /home/tester1/Test /home/tester1/Test
```And then add a file:
```
touch /home/tester1/Test/test5.txt
```It ends up with these permissions:
> ls -al /home/tester1/Test/test5.txt
-rwxrwxr-x 1 tester1 tester1 0 Dec 12 09:53 /home/tester1/Test/test5.txt
That fixes it for any new files added but doesn't do much with any of the old files.

The grand master of bindfs in this forum is sisco311 ( [http://ubuntuforums.org/showthread.php?t=1460472](http://ubuntuforums.org/showthread.php?t=1460472) ). Maybe he will come along to offer his insight.

---

### Post by LewisTM on 2012-12-12
For what it's worth, you don't seem to be doing anything wrong.
The same kind of command
```
sudo bindfs -f -p a+x ~/Documents /mnt
```
makes all my documents executable in /mnt.

---

### Post by Morbius1 on 2012-12-12
> sudo bindfs -f -p a+x ~/Documents /mnt/Test2
ls -al /mnt/Test2
-rw-rw-r-- 1 tester1 tester1     78 Feb 10  2012 AutoGoogle.txt
-rw-rw-r-- 1 tester1 tester1    417 Feb 10  2012 Enable-Usershares.txt
-rw-rw-r-- 1 tester1 tester1   2489 Aug 21 14:49 test.abw
It doesn't for me.

---

### Post by ksemb on 2012-12-13
Hello,

I contacted the Author of bindfs and he told me that the bug is already fixed in a newer version.

> Hi,

You are probably using bindfs 1.9, which comes with Ubuntu 12.04. This  is a bug that was fixed in bindfs 1.10 where --realistic-permissions was  made an option instead of the default behavior.

You can compile a newer version from source [1] or see if the .deb from Ubuntu 12.10 happens to work [2].

[1] [http://code.google.com/p/bindfs/downloads/list](http://code.google.com/p/bindfs/downloads/list)
[2] [http://packages.ubuntu.com/search?suite=quantal&searchon=names&keywords=bindfs](http://packages.ubuntu.com/search?suite=quantal&searchon=names&keywords=bindfs)


Best regards,
Martin Pärtel
From his suggestions I chose the second one with the Ubuntu repository and everything works now.

Cheers,
Klaus

---

### Post by Morbius1 on 2012-12-13
@ksemb, thank you very much for posting that information. I use bindfs all the time ( 12.04 and earlier ) and would never had known of these changes if not for your post.

@LewisTM, can you confirm that you are experiencing your results from a 12.10 box so that I don't lose sleep over this :)

---

### Post by LewisTM on 2012-12-13
I confirm, you can sleep now :)

---

