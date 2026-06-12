---
title: "rsync is only copying directories and not files?!?"
date: 2016-02-07
forum: General Help
---

### Post by M_R on 2016-02-07
I have a bunch of files on an old hard drive that I'm trying to move to my new file server and trying to use rsync to transfer everything. No matter what I try I can only get rsync to copy over the directory structure and no files are transferred. Here's what I'm running:[INDENT]```
# rsync --progress --stats -avhIe ssh user@192.168.1.10:/media/OldHD/ /srv/storage/__sort__/
```
[/INDENT]

I threw the "I" in the options in case it was some weird timestamp thing, but nothing is getting copied.
I run the command as root on the file server and also have access to the source directory as "user".
I'm moving everything into a temporary directory on the file server until I can make sense of everything getting moved over and how/where I want to store them.

Here's the output...

```
[INDENT]user@192.168.1.10's password:
[/INDENT]
[INDENT]receiving incremental file list
Number of files: 19,291 (dir: 19,291)
[/INDENT]
[INDENT]Number of created files: 0
[/INDENT]
[INDENT]Number of deleted files: 0
[/INDENT]
[INDENT]Number of regular files transferred: 0
[/INDENT]
[INDENT]Total file size: 0 bytes
[/INDENT]
[INDENT]Total transferred file size: 0 bytes
[/INDENT]
[INDENT]Literal data: 0 bytes
[/INDENT]
[INDENT]Matched data: 0 bytes
[/INDENT]
[INDENT]File list size: 224.19K
[/INDENT]
[INDENT]File list generation time: 0.001 seconds
[/INDENT]
[INDENT]File list transfer time: 0.000 seconds
[/INDENT]
[INDENT]Total bytes sent: 19.45K
[/INDENT]
[INDENT]Total bytes received: 725.53K
[/INDENT]
[INDENT]sent 19.45K bytes  received 725.53K bytes  165.55K bytes/sec
[/INDENT]
[INDENT]total size is 0  speedup is 0.00 [/INDENT]

```

I can see the complete directory structure in the "__sort__" directory on the file server, but there are no files!

What am I doing wrong???

---

### Post by CaptainMark on 2016-02-08
Are there any symlinks involved, the "-a" flag will imply the "-l" flag therefore not follow symlinks by default unless you override with the "-L" flag

---

### Post by M_R on 2016-02-08
Nope, no symlinks anywhere on the old hard drive.

> **CaptainMark said:**
> Are there any symlinks involved, the "-a" flag will imply the "-l" flag therefore not follow symlinks by default unless you override with the "-L" flag

---

