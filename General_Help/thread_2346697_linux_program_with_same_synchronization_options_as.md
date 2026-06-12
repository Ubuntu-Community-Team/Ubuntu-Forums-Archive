---
title: "linux program with same synchronization options as windows toysync?"
date: 2016-12-17
forum: General Help
---

### Post by ubto66 on 2016-12-17
[https://youtu.be/s1xd8bEtMI0?t=113](https://youtu.be/s1xd8bEtMI0?t=113)
Is there a linux program with a gui that provides the same options as windows synctoy?
Thank you.

---

### Post by TheFu on 2016-12-17
The Unix file system is more complex. If you just want a simple recursive copy, use either **cp -r** or **rsync**.
There is grsync, but I've never used it.

I always found synctoy to be lacking in options. rsync has many, many, many, capabilities. You can copy newer and keep any files that already exist. Or you can copy newer and delete any that do not exist in the source.  Plus, rsync works over ssh remotely, by default. That means pushing (or pulling) data between systems is secure. Good enough for internet use - actually, much more secure than using HTTPS.

[http://www.techrepublic.com/blog/linux-and-open-source/how-to-become-an-rsync-power-user-with-grsync/](http://www.techrepublic.com/blog/linux-and-open-source/how-to-become-an-rsync-power-user-with-grsync/) if you **need** a GUI. GUIs get in the way for automation, however.  I like to sync certain files like my password manager DB daily to about 6 locations.  My system-of-record system pushes out the newest version at 1am.  I don't want to be up for that or have to do anything to make it happen.  It is nice that my phone, tablet, and both laptops get the current DB automatically. And I didn't have to trust some 3rd party.

In general, **rsync -avz source target** is the way.  This can be on the same machine between different directories or around the world assuming ssh connectivity is already setup.

---

### Post by ubto66 on 2016-12-18
Thank you for the answers. I disagree they are duplicates. One is about grsync. The other is asking for other programs.
[http://www.techrepublic.com/blog/linux-and-open-source/how-to-become-an-rsync-power-user-with-grsync/](http://www.techrepublic.com/blog/linux-and-open-source/how-to-become-an-rsync-power-user-with-grsync/)
Where in the link does it say how to get the subfolders synchronized?

---

### Post by TheFu on 2016-12-18
If it isn't in that link, it is an oversight. Sorry. Think rsync only does recursive (update: that is incorrect, it will also NOT do recursive), unless the pattern doesn't match the subdirs. But you are correct, the link does not clearly say recursive, though if read through pre-knowing glasses (that we all wish we had), it does imply this, from a certain perspective.  Not useful to you, which I completely understand.

> backing up local or remote directory trees
in the 1st paragraph. Not as clear as I'd like. Easily missed or skipped. I would have missed this too had I not known.

BTW, some of those options like preserving owner/group and permissions won't work if you aren't the owner or root or a member of the group.

**rsync -avz** are the options I use for a quick *mirror-everything* rsync.    I always use a directory for the "source/", so it and all subdirs are synced (not deleting files on the target which don't exist on the source. Test it on a trivial directory system. That will teach more than we can possibly explain here.  Plus there are lots and lots of rsync how-tos.

There are always these pages which there is almost certainly a copy on your Linux system:
* [https://linux.die.net/man/1/grsync](https://linux.die.net/man/1/grsync)
* [https://linux.die.net/man/1/rsync](https://linux.die.net/man/1/rsync)

There is a -r or **--recursive** option for rsync. Can't remember using it in the last 16+ yrs. That's because -a equals -rlptgoD on the options, which includes -r according to the manpage. It is good to check the manpage. I usually learn something new reviewing the manpage for rsync. Other great manpages are ssh, bash, interfaces, fstab, and mount. ;)

---

### Post by tk83 on 2016-12-18
If you want a nice GUI sync program that's designed to do proper 2-way synchronisation use Unison. When you run it it'll show you a list of differences between the 2 folders (which can be on different computers) and allow you to choose whether to skip certain files or to override its guess of which file should be synced over which. 

It's in the Ubuntu repositories - just install package unison-gtk.

---

### Post by ubto66 on 2016-12-19
Thank you.
The key point is the 'merge' synchronization. What I want from merge is Synchronize: New and updated files are copied both ways. Renames and deletes in one folder is repeated on the other. Such that the latest version of a file or its deletion gets synchronized onto the other folder. 
Is there a rsync command that will do that? 
If so, can the rsync command get added into a grsync session? 
I think the 'default' session in grsync is an echo synchronization. Echo: New and updated files are copied left to right. Renames and deletes on the left are repeated on the right.

I have tested unison-gtk. 
I think the 'left to right' and 'right to left' buttons are echo synchronizations. Echo: New and updated files are copied left to right. Renames and deletes on the left are repeated on the right. Allthough I do not know if renamings are being synchronized?
What does the merge button do? I cannot find an answer in the manual, [https://www.cis.upenn.edu/%7Ebcpierce/unison/download/releases/stable/unison-manual.html](https://www.cis.upenn.edu/%7Ebcpierce/unison/download/releases/stable/unison-manual.html). Is merge Synchronize: New and updated files are copied both ways. Renames and deletes in one folder is repeated on the other?

---

### Post by Habitual on 2016-12-20
[http://rsync.net/resources/howto/rsync.html](http://rsync.net/resources/howto/rsync.html)

---

### Post by tk83 on 2017-01-15
> **ubto66 said:**
> Thank you.
I have tested unison-gtk. 
I think the 'left to right' and 'right to left' buttons are echo synchronizations. Echo: New and updated files are copied left to right. Renames and deletes on the left are repeated on the right. Allthough I do not know if renamings are being synchronized?
What does the merge button do? I cannot find an answer in the manual, [https://www.cis.upenn.edu/%7Ebcpierce/unison/download/releases/stable/unison-manual.html](https://www.cis.upenn.edu/%7Ebcpierce/unison/download/releases/stable/unison-manual.html). Is merge Synchronize: New and updated files are copied both ways. Renames and deletes in one folder is repeated on the other?

To Unison a file rename will look like a file deletion (the original filename) and a new file (the file under the new name). It has no problem synchronising this. The only catch with Unison is that you should scroll down and check over which way it wants to sync something - sometimes its logic is not perfect and it'll try to sync one or the other file the wrong way. 

Overall though it's very usable, I use it to sync my home directory around between 3 machines.

Another option, if you want something that just runs in the background, is syncthing. As far as I know rsync can only really sync one way at a time, so is no good if you for example work on some files in your home directory on one machine, and some other files on another machine and want to sync them together.

---

