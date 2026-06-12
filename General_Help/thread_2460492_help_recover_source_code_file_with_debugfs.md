---
title: "help recover source code file with debugfs"
date: 2021-04-11
forum: General Help
---

### Post by lewsutt on 2021-04-11
I accidentally removed a near final draft of source code instead of copying it into a
new version. Help please. I can't really follow the directions for data recovery given
here: [https://unix.stackexchange.com/questions/80270/unix-linux-undelete-recover-deleted-files](https://unix.stackexchange.com/questions/80270/unix-linux-undelete-recover-deleted-files)

Can someone please talk me through this. I don't want to do too much until I unmount
the block the file was on or safely isolate the block somehow. Or understand what is 
going on there.

1186006 -rw-rw-r-- 1 lew42 lew42 15 Apr 11 19:32 data.txt

That is the inode of a test file that I just saved.
Thanks in advance.
-Lew

---

### Post by ActionParsnip on 2021-04-11
Why not use your backups? If you aren't using backups then why aren't you using backups?
If you code a lot, shy aren't you using git to maintain versioning? You can just pull the newest version from your own branches. 
Is your code not valuable to you? What if the IDE on the drive you have the data on goes bang? Where is your data?

---

### Post by lewsutt on 2021-04-11
Thank you for the life lessons. I am learning the craft atm. The lesson I just learned is to use 
history commands rather than arrow key to scroll history to execute quick commands in bash.
 Because sometimes you go on autopilot and press the wrong thing. I should have been working
in a git init directory, but I wasn't. But hey, this gives us all a chance to brush up on file
recovery! Speaking of, just looking for help figuring out which block to recover, and how.

---

### Post by lewsutt on 2021-04-12
I got kind of confused on the device path needed in debugfs. Fwiw, I am
using Ubuntu 20.04 on a virtualbox machine, which is stored on a different
drive from my main system boot drive. *Main OS is Windows 10. For now.

---

