---
title: "Someone explain hard links to me"
date: 2017-08-30
forum: General Help
---

### Post by user_of_gnomes on 2017-08-30
I am trying to wrap my head around symbolic and hard links. Under Windows, it's quite simple: you just create a shortcut and that's it. You remove the original fine and the shortcut stops working, simple enough. I suppose this is a soft-link.
Perhaps there are hard-links under Windows as well, I wouldn't know.

Are there any practical examples for when you would use a hard link under Linux? Maybe I'll better understand the concept if I could relate it to every-day use. 
Reading all the theory hasn't helped. I kind of understand what a hard-link is but not why you'd ever want to use one and now I'm wondering if I am missing out on something useful.

---

### Post by 1clue on 2017-08-30
A symbolic link is a file which references another file, approximately the same way that a Windows shortcut does.

A hard link is different.

On any filesystem, there is the file data space, where all the content goes, and then there's a bit of space somewhere else on the drive which tells the operating system where the file is. It includes the name, the blocks on the disk used, that sort of thing.

A hard link is a second 'header' pointing at the same exact data.  Once a hard link is created, you could delete the original file and the data would still be on the second file. There's really no difference between a hard link and the original file header from when you created the file.

---

### Post by wyliecoyoteuk on 2017-09-04
Effectively they are just alternative names for the physical location of the data stored on the disk, which is why they cannot be used across filesystems or for directories.
E.g. you create a file called Fred, and you make hard links to it called Mary and Albert.
The rm command does not remove data, it just reduces the hard link count for that data by one.
If you remove Fred and Albert, Mary remains. if you then remove Mary, the data is still there until it is overwritten, but there is no way to access it.
Symbolic links are equivalent to windows shortcuts, and can be used across filesystems, but if you remove the file, they stop working.

---

### Post by user_of_gnomes on 2017-09-04
Thanks, good explanations! It makes sense to me now.

In essence, when you create a new file a hard link is made. You could then proceed to create a second (and so on) and safely delete the first hard link, not losing access to the data because the operating system will still know where it is. Hence the name hard link,I suppose.

---

