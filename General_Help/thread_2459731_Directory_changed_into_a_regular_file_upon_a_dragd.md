---
title: "Directory changed into a regular file upon a drag/drop, now how do I change it back?"
date: 2021-03-24
forum: General Help
---

### Post by cparke on 2021-03-24
I'm on Ubuntu 16.04LTS, and I've never seen anything like this before!  

Somehow, simply dragging and dropping a directory in the Ubuntu File Manager messed up and dropped the directory flag off the file!  So now the contents of my directory are inaccessible.  

Forgetting for a moment how this is never supposed to happen, and not sure why it happened, how do I fix this?  (this is EXT4 file system)   I'm afraid to for e2fsck and get these lost chains removed or disorganized (there's a lot of files in here)

I can't find any way using 'chmod' to turn on a mode flag to mark the file as a directory.   But there has to be a way to transform it back.

Ideas?


$ stat CS_DVD
  File: 'CS_DVD'
  Size: 38246         Blocks: 80         IO Block: 4096   regular file
Device: 807h/2055d    Inode: 3801317     Links: 1
Access: (0664/-rw-rw-r--)  Uid: ( 1000/   chris)   Gid: ( 1000/   chris)
Access: 2021-03-24 14:54:10.639129021 -0400
Modify: 2017-12-01 00:30:20.146519924 -0500
Change: 2021-03-24 15:05:06.307454085 -0400
 Birth: -

---

### Post by ajgreeny on 2021-03-24
I wonder if you have a sticky keyboard key meaning that instead of moving the folder you have created a soft link or something similar.

I don't use Ubunyt with nautilus as file manager so I'm not sure if you can create a soft link that way but you can do so in some file managers.  However if it is a soft link it should still open as if it were the original folder so I'm probably wrong.

What does command ***file filename*** tell you?

---

### Post by cparke on 2021-03-24
It is not a soft-link, I would know that using the shell and 'ls -l'.

[B]$ ls -l CS_DVD 
-rw-rw-r-- 1 chris chris 38246 Dec  1  2017 CS_DVD
[/B]
You're right though, 'nautilus' is the file manager and it does have a way to make a link.  I never even realized that was possible.  

Like I said at the beginning, this could even be a bug in the new kernel version that Ubuntu recently prepared for the 16.04 LTS, so we shouldn't necessarily blame the file manager.

To respond to your inquiry, here is the output:

[B]$ file CS_DVD 
CS_DVD: XML 1.0 document, ASCII text, with very long lines
[/B]
Looking at the contents, it seems the directory may have been instantaneously converted into a Brasero project (XML syntax) and replaced with that as a file.  How that could happen is quite bizarre!

The lost directory is also not in my trash.  So where could the directory (and its contents) have gone?

---

### Post by ajgreeny on 2021-03-25
This is certainly taking the adage that "everything in Linux is a file" to a rather extreme extent, isn't it, and I'm afraid my Linux mojo is not sufficient to work out what on earth may have happened here.

Do you have backups, with that folder still available, that you could restore to the site where things went pear-shaped and try again?
Other than that I have not a clue where to go; sorry!

---

### Post by HermanAB on 2021-03-25
I think you already know the answer to the problem of where the files went...

If you don't have backups, then you probably need photorec or similar to recover some of them.

---

### Post by cparke on 2021-03-25
In fact, I made a backup of everything that was in the subdirectory just before I did this move operation.

Looking back at that backup, I see what actually happened, and you're right, nothing funky actually happened (thankfully):
[LIST]
[*]This file was always there.  It is something I must have made in Brasero several years ago to make a DVD containing the missing directory. 
[*]The directory had a slightly different name:** CS_DVD 2017-1** 
[/LIST]
What happened was this: When you drag in nautilus and hover over a subdirectory, if you don't release the right mouse button quick enough, the context automatically switches to that directory.  In this subdirectory, there are additional subdirectories.  I released the mouse at the same time this context switch occurred, and at the time of release, my mouse was now over a subdirectory in the subdirectory.  Going through those, I found my missing directory and moved it up one level where it was supposed to be.

Case closed, thank you so much for you help!


P.S.: I am now curious what the raw contents of a directory inode actually look like.  Is there any way to view it in a hex editor?

---

