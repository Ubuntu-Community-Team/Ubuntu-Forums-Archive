---
title: "How to make a copied file like it's not being copied?"
date: 2024-08-11
forum: General Help
---

### Post by mangada on 2024-08-11
If the copy action occurred in the disk or two, the file's timestamps should be closer because the speed of disk is very fast, make it looks like a copied file, so you would change the timstamps. And, what other significant signs showing the file is copied?

---

### Post by Autodave on 2024-08-12
Maybe it is just me, but I have no idea what you are asking or trying to do.  Can you explain this in a little more detail please?

---

### Post by TheFu on 2024-08-12
> **mangada said:**
> If the copy action occurred in the disk or two, the file's timestamps should be closer because the speed of disk is very fast, make it looks like a copied file, so you would change the timstamps. And, what other significant signs showing the file is copied?

Use a backup tool, not copy.
Also, the timestamps are file system dependent, so you'll need to be more specific about the file systems used.  Each can be slightly different.

Use the **stat** command to see the details on any file.

---

### Post by mangada on 2024-08-12
I copied a text file from Linux to USB pen drive with exfat format, then try to change it's timetamps by **touch**,  the Access, Modify, Change timestamps will change to what I set. Adding  `-a` will change Access only, adding `-m` will change Modify and Change  time. The Birth time ( all is viewed by **stat** FILE) are the same. But if the file's content is modified by **mousepad,** all the 4 timestamp will be changed. But if by **nano**, birth timestamp unchanged. Is it because the **Mousepad** created a new file and **nano** just adds new to the file?

---

### Post by HermanAB on 2024-08-12
Exfat is a simple Microsoft file system.  It only has create, modify and last access time stamps. Last access time may be disabled and you cannot really set it with a command.

---

### Post by TheFu on 2024-08-12
> **mangada said:**
> I copied a text file from Linux to USB pen drive with exfat format, then try to change it's timetamps by **touch**,  the Access, Modify, Change timestamps will change to what I set. Adding  `-a` will change Access only, adding `-m` will change Modify and Change  time. The Birth time ( all is viewed by **stat** FILE) are the same. But if the file's content is modified by **mousepad,** all the 4 timestamp will be changed. But if by **nano**, birth timestamp unchanged. Is it because the **Mousepad** created a new file and **nano** just adds new to the file?

The only way to know how any specific program actually works is to look at the source code.  Fortunately, you can do that with F/LOSS, so feel free to answer your question by looking at how files are created new and saved in any program you like.

Most Linux file systems set the "birth time" to be the same as the "create time" or the "change time" or just leave it empty completely, IME, but I seldom look all that closely.  My backup tools don't care so I have little reason to care.  

Of course, it is a perfectly valid question, if something you need to accomplish needs these things.  However, if you wanted to accomplish something by using the birth time on a file, I'd warn you that it isn't likely to happen.  File system gurus/devs have know about this for 40+ yrs and deemed it not so important to bother.

So, I looked at an ext4 file and a ZFS file.  I don't have any exFAT here. Just not something I'd use when there's f2fs available for flash drives, but we all have our own needs and limitations to meet.

So, the ext4 file has this:
```
$ stat file.mkv 
  File: file.mkv 
  Size: 3569418044      Blocks: 6971528    IO Block: 4096   regular file
Device: fd05h/64773d    Inode: 75          Links: 1
Access: (0664/-rw-rw-r--)  Uid: ( 1000/      tf)   Gid: ( 1000/      tf)
Access: 2024-08-05 15:43:36.729626424 -0400
Modify: 2024-08-05 19:24:03.186029813 -0400
Change: 2024-08-05 19:24:03.186029813 -0400
 Birth: -
```
The file was created by a video transcoding tool. The file system is mounted with rw,noatime,errors=remount-ro options.
ls -l on that file has **Aug  5 19:24** which is either the modify or change time. I can't tell.

and the ZFS file (completely different file) has this:
```
$ stat file.mkv
  File: file.mkv
  Size: 16              Blocks: 2          IO Block: 512    regular file
Device: 1ch/28d Inode: 1709610     Links: 1
Access: (0664/-rw-rw-r--)  Uid: ( 1000/      tf)   Gid: ( 1000/      tf)
Access: 2024-08-12 10:48:07.305965030 -0400
Modify: 2024-08-12 10:48:07.305965030 -0400
Change: 2024-08-12 10:48:07.305965030 -0400
 Birth: 2024-08-12 10:48:07.305965030 -0400
```
This file was created and modified multiple times using vi.  It wasn't deleted between complete emptying and editing the 5 times that happened.  As you can see, all the times match the last time I ran stat, not the last time the file was actually modified.  Odd.  The ZFS file system is mounted with ZFS defaults, which seem to be rw,relatime,xattr,posixacl. 

Make whatever you like about those times.

Any program used will have different versions, so even the same program can change how they create and update files over time if the program version changes.  When a C open() function call happens, there are different modes that files can be opened.  read-write, read-only, append, and all the permissions on the file would be checked / error, if needed when an unallowed mode was attempted - probably at write time based on the file handle, not the open() call.  You can read more about open() in the manpages.  Use **man -s 2 open** to see the options.  After opened, there are read(), write(), close(), seek() functions.

---

### Post by currentshaft on 2024-08-12
mousepad

---

### Post by ubuuser3482 on 2024-08-13
> **mangada said:**
> I copied a text file from Linux to USB pen drive with exfat format, then try to change it's timetamps by **touch**,  the Access, Modify, Change timestamps will change to what I set. Adding  `-a` will change Access only, adding `-m` will change Modify and Change  time. The Birth time ( all is viewed by **stat** FILE) are the same. But if the file's content is modified by **mousepad,** all the 4 timestamp will be changed. But if by **nano**, birth timestamp unchanged. Is it because the **Mousepad** created a new file and **nano** just adds new to the file?

Maybe -p does what you want?

---

### Post by mangada on 2024-08-22
**cp -p**? That will not keepthe birth time.

---

### Post by mangada on 2024-08-22
I know faking timestamps to avoid others suspecting it's a copied file, what other significant signs showing the file is copied?

---

### Post by currentshaft on 2024-08-22
po

---

