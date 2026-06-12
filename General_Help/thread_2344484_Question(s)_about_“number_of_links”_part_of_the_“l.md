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

### Post by vasa1 on 2016-11-25
Duplicate of [https://ubuntuforums.org/showthread.php?t=2344493](https://ubuntuforums.org/showthread.php?t=2344493)

---

