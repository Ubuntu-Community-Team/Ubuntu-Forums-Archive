---
title: "Question(s) about “number of links” part of the “ls -l” (without the quotes) command"
date: 2016-11-25
forum: General Help
---

### Post by s3a on 2016-11-25
Hello to everyone that's reading this. :)

For example, what does the number 1 mean exactly in the following line?:
-rw-r--r-- 1 s3a s3a 43891048 Nov  5 01:03 Firefox Setup 45.4.0esr.exe

This ( [http://superuser.com/questions/435919/how-to-interpret-the-number-after-permission-in-ls-l](http://superuser.com/questions/435919/how-to-interpret-the-number-after-permission-in-ls-l) ) link (no pun intended) (among others) basically states that that number represents “the number of links”, but what does that mean exactly?

I've used symlinks / symbollic links in the past, but are hard links the type of links used in data deduplication (for example)?

Furthermore, I'm assuming that all files and directories have at least one link, because if I'm understanding this concept of files and directories being linked to, the links are like pointers (such as in C++), and the files and directories in question need to be found somehow (by the OS), but **what's the logic behind the OS's decision of whether a certain file or directory automatically gets more than one link** (so without manual intervention from the user)? (I hope I'm asking the right question(s), because I'm confused about this topic, but I am still trying to ask a question that's not vague.)

Any input would be greatly appreciated!

P.S.
I hope this post is in the right place, but if it is not and you have the administrative privileges to move it into the right place, please do so.

---

### Post by kpatz on 2016-11-25
The link count is the number of hard links to the file.  Every file has at least one link, the original path/name of the file.  You can use the ln command to create additional links to a file.  Hard links are additional names/paths to the same inode and file contents.

When you "delete" a file (using rm or whatever) you're actually deleting the link.  The file itself doesn't disappear until all links to it are removed.  The link count allows the OS to keep track of the number of links so it knows when to actually delete the file.

Symbolic links don't affect the link count, since they're just files containing a path to another file.  If you delete a file with a symbolic link, the file will disappear and the link will point to a non-existent file.

Directories have link counts as well, but you can't hardlink directories yourself, instead they are created by the kernel as the "." and ".." directories.  The "." directory is a link to itself, and ".." is a link to the parent.  The link count of a directory corresponds to the number of subdirectories in the directory (as each would have a ".." that links back to the parent).

---

### Post by s3a on 2016-12-22
Thanks very much! That was very helpful! (Sorry for the delay.)

---

