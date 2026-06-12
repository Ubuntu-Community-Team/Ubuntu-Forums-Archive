---
title: "Hard link VS Symbolic + Basic terminal questions"
date: 2013-03-18
forum: General Help
---

### Post by GameX2 on 2013-03-18
Hi,


I'm reading a PDF about bash commands; I've read about the difference between hard links and symbolic links.  I do believe symbolic links are a much better version of hard link, and they probably work the same way as Shortcuts on Windows and Aliases on OS X.
But no matter how much time I read the paragraph explaining the hard links, I don't get what they are used for.  Could you please explain?

A basic question as well:
What's the difference between the which command and the whereis command ?

Thank you!

---

### Post by slickymaster on 2013-03-18
A hard link is a directory entry (filename) that points to the file itself. The operating system keeps track of how many hard links point to a file, so when the last hard link to a file is removed, the file is deleted. A symbolic link is a special file that only contains a filename. The file that a symbolic link refers to may not necessarily exist at any given time.

**whereis** will show you the location of the binary, the source, and the man pages for the command, whereas **which** will only show you the location of the binary for the command.

---

### Post by GameX2 on 2013-03-18
> **slickymaster said:**
> A hard link is a directory entry (filename) that points to the file itself. The operating system keeps track of how many hard links point to a file, so when the last hard link to a file is removed, the file is deleted. A symbolic link is a special file that only contains a filename. The file that a symbolic link refers to may not necessarily exist at any given time.

Ok, that's a little complicated, but I get the general idea.  I still wonder what is the actual use of these hard links - when will I need to create a hard link ?

> **slickymaster said:**
> **whereis** will show you the location of the binary, the source, and the man pages for the command, whereas **which** will only show you the location of the binary for the command.

Thank you, very helpful. :)

---

### Post by slickymaster on 2013-03-18
> **GameX2 said:**
> Ok, that's a little complicated, but I get the general idea.  I still wonder what is the actual use of these hard links - when will I need to create a hard link ?

Hard links are useful when the original file is getting moved around. For example, moving a file from **/bin** to **/usr/bin** or to **/usr/local/bin**. Any symlink to the file in **/bin** would be broken by this, but a hardlink, being a link directly to the inode for the file, wouldn't care.
Also, hard links may take less disk space as they only take up a directory entry, whereas a symlink needs its own inode to store the name it points to.

---

### Post by sudodus on 2013-03-18
I like hard links. They survive the case when the original 'file' alias the original 'hard link' is deleted. But hard links work only for files on the same partition. You must use symbolic links for directories and to link between different partitions.

---

### Post by schragge on 2013-03-18
Well, *theoretically* you could use hard links for directories on the same partition. In fact, once upon a time they were used all over the place: each directory contained entries . and .. which were just hard links to the directory itself and its parent, respectively. On modern Linux systems these  usually don't exist as physical directory entries, but are faked by the VFS layer in the kernel. The POSIX standard doesn't explicitly forbid hard links to directories. However, as a matter of fact, you're not permitted to create them on most operating systems even as root.

---

### Post by GameX2 on 2013-03-18
> They survive the case when the original 'file' alias the original 'hard link' is deleted.


Are they comparable to copies of the original file?  Excuse my ignorance!

I've also noticed that when I've tried to create a symbolic link on a USB drive, I got a error message saying "This file system does not support symbolic links".  Is it because it's a FAT32 drive?  Do this work on NTFS ?

Thank you!

---

### Post by slickymaster on 2013-03-18
> **GameX2 said:**
> I've also noticed that when I've tried to create a symbolic link on a USB drive, I got a error message saying "This file system does not support symbolic links". Is it because it's a FAT32 drive?
Yes.
FAT32 doesn't supports concepts like owner, permissions and symbolic links, so you won't be able to use utilities like chmod, and Windows "shortcuts" are not the same as UNIX symlinks.

---

### Post by sudodus on 2013-03-18
> **GameX2 said:**
> Are they comparable to copies of the original file?  Excuse my ignorance!

I've also noticed that when I've tried to create a symbolic link on a USB drive, I got a error message saying "This file system does not support symbolic links".  Is it because it's a FAT32 drive?  Do this work on NTFS ?

Thank you!
It is *not* copies of the original file. The hard links are pointers to the data on the hard disk surface. In linux there can be more than one pointer (they have equal status or importance, they are all pointing directly to the data). A symbolic link points to such a pointer, not directly to the data. Some of the linux methods to manage files, permissions etc work, some don't work with FAT32 and NTFS. I don't remember if symbolic links work with NTFS. Maybe they work, but they are different from Windows short-cut (same idea though). You can test it yourself :-)

---

### Post by GameX2 on 2013-03-18
Ok, thanks for all your replies.  I've did some tests, using this:

```
ln ~/test_file.pdf hard_link
```

I can see the link is created proprely, althought I can't actually see that it's an hard link  and not a copy.  I mean, I would easilly mistake a hard link for a copy.  I've noticed deleting the hard link or the copy does not "break" each other.  I've also checked the file size of the original (5MB for example) and the hard link (5MB as well).  Selecting them both in Nautilus will display that 2 objects are selected, with a total of 10MB.

> It is *not* copies of the original file. The hard links are pointers to the data on the hard disk surface.
> a hardlink, being a link directly to the inode for the file

There are not copies, but pointers/links, right?  "Pointers" look like my definition of a symbolic link, a shortcut.  Do they actually take disk space if they are pointers (Compared to symbolic links, which are basically shortcuts, and so only a few KBs)?
From what I see, I get your point, but I would need just another explanation - I actually believe that hard link are in that case more useful than symbolic links (If they do not take disk space.  That would be weird), event thought I've read that symbolic links are a newer, more advanced version of hard links.

> They survive the case when the original 'file' alias the original 'hard link' is deleted.

So they can act as a backup, but are actually.. *not* copies? :confused:
^^"

> Some of the linux methods to manage files, permissions etc work, some  don't work with FAT32 and NTFS. I don't remember if symbolic links work  with NTFS.
After testing, I can confirm that symbolic links work on NTFS as well.  But a hard link located on a NTFS external driver, pointing to /home/gamex oddly display an error message "Permission denied".


Thanks for all your replies! :)

---

### Post by bab1 on 2013-03-18
> **GameX2 said:**
> Ok, thanks for all your replies.  I've did some tests, using this:

```
ln ~/test_file.pdf hard_link
```

I can see the link is created proprely, althought I can't actually see that it's an hard link  and not a copy.  I mean, I would easilly mistake a hard link for a copy.  I've noticed deleting the hard link or the copy does not "break" each other.  I've also checked the file size of the original (5MB for example) and the hard link (5MB as well).  Selecting them both in Nautilus will display that 2 objects are selected, with a total of 10MB.

It might help if you rethought a little of this.  A link is a mapping between the *inode *and the entry in the directory.  In other words the original link and any subsequent hard links are nothing more than a mapping between the inode and the file name.  The *inode * is the actually pointer to the block data on the hard disk.  It would look something like this
```

data<---->Inode (200)|<---->Link
                     |<----->Hard Link

```
Looking at this in the terminal.  I created a file named [COLOR="#0000FF"]test[/COLOR].  The inode is  12061747.  I create a hard link to this named [COLOR="#0000FF"]testlink[/COLOR].  The inode number is the same.  It looks like this (the inode number is on the far right.```
ls -li 
total 0
12061747 -rw-rw-r-- 2 bruce users 0 Feb 18 23:40 test
12061747 -rw-rw-r-- 2 bruce users 0 Feb 18 23:40 testlink

``` 
If I make a sym-link to the original test file it will look like this 
```

12060025 lrwxrwxrwx 1 bruce bruce 4 Mar 18 20:36 symtest -> test
12061747 -rw-rw-r-- 2 bruce users 0 Feb 18 23:40 test
12061747 -rw-rw-r-- 2 bruce users 0 Feb 18 23:40 testlink

```
There is no doubt that the sym-link is at the top.  It shows that it points at the link named test.

What ever you want to use these links, hard links or sym-links for is up to you, but you should have a solid grasp of what they are.
> 


There are not copies, but pointers/links, right?  "Pointers" look like my definition of a symbolic link, a shortcut.  Do they actually take disk space if they are pointers (Compared to symbolic links, which are basically shortcuts, and so only a few KBs)?
From what I see, I get your point, but I would need just another explanation - I actually believe that hard link are in that case more useful than symbolic links (If they do not take disk space.  That would be weird), event thought I've read that symbolic links are a newer, more advanced version of hard links.

Neither hard links nor sym-links use much space at all.  More importantly, you should know the pro and con of both types.  I use hard links for backups (to make multiple references to the same inode (that points to the data) and sym-links when I want to multiple pointers to the same file name.
> 
So they can act as a backup, but are actually.. *not* copies? :confused:
^^"
 
The real difference is that with hard links the data is not considered deleted until the last link to the inode is unlinked.  In fact that is really what happens when you delete a file.  You unlink the file name from the inode and remove it (the inode).
> 

After testing, I can confirm that symbolic links work on NTFS as well.  But a hard link located on a NTFS external driver, pointing to /home/gamex oddly display an error message "Permission denied".

Since a sym-link is a pointer to a file name you can create sym-links.  NTFS has no inode system you can really make hard links.

---

### Post by sudodus on 2013-03-19
> **bab1 said:**
> It might help if you rethought a little of this.  A link is a mapping between the *inode *and the entry in the directory.  In other words the original link and any subsequent hard links are nothing more than a mapping between the inode and the file name.  The *inode * is the actually pointer to the block data on the hard disk.  It would look something like this
```

data<---->Inode (200)|<---->Link
                     |<----->Hard Link

```
Looking at this in the terminal.  I created a file named [COLOR=#0000FF]test[/COLOR].  The inode is  12061747.  I create a hard link to this named [COLOR=#0000FF]testlink[/COLOR].  The inode number is the same.  It looks like this (the inode number is on the far right.```
ls -li 
total 0
12061747 -rw-rw-r-- 2 bruce users 0 Feb 18 23:40 test
12061747 -rw-rw-r-- 2 bruce users 0 Feb 18 23:40 testlink

``` 
If I make a sym-link to the original test file it will look like this 
```

12060025 lrwxrwxrwx 1 bruce bruce 4 Mar 18 20:36 symtest -> test
12061747 -rw-rw-r-- 2 bruce users 0 Feb 18 23:40 test
12061747 -rw-rw-r-- 2 bruce users 0 Feb 18 23:40 testlink

```
There is no doubt that the sym-link is at the top.  It shows that it points at the link named test.
...
Good explanation :KS

---

### Post by schragge on 2013-03-19
What might be helpful in order to grasp how hard links work, is understanding that both *test* and *testlink* in the example above are in fact hard links. When you create a file, it gets a name and an entry in some directory. This entry is the first hard link to that file's inode. You can create additional hard links with the *ln* command. Notice the number after permission string in the output of *ls -l*. It's the number of hard links pointing to file's inode. All hard links are created equal. After both *test* and *testlink* are created, there's no way anymore for the system to discern which of the two is the primary and which is the secondary pointer to the inode. The notion of *primariness* is not applicable to hard links. You may just as well say that *testlink* is the main name of the file, and *test* is an additional link to it, it simply doesn't matter. Just think of hard links as aliases, additional names of the same file. A file on Unix/Linux may have several names, or points of access.

---

### Post by matt_symes on 2013-03-19
Hi

```

data<---->Inode (200)|<---->Link 
                     |<----->Hard Link
```

This may be better thought of as
```

data<---->Inode (200)|<----> **Hard **Link (Original Hard link to the file)
                     |<----->Hard Link (Second Hard link to the file) 
```

Just a thought.

Kind regards

---

### Post by GameX2 on 2013-03-19
Thank you, I understand the comcept more clearly;
What I find the most confusing with hard links, is that they don't take any space, but a file manager still display that they take up space.  What I should understand, is that the data is deleted when the original (Which cannot be distinguised from the link) and all the hard-links are deleted.

That's a interesting possibility.  Just out of curiosity, does such a thing exist on Windows / OS X (Just curiosity, I find Linux way much better than Windows, but that's a opinion anyways.  No bashing, OS are tools.) ?

Thank you very much.

---

### Post by slickymaster on 2013-03-19
> **bab1 said:**
> It might help if you rethought a little of this.  A link is a mapping between the *inode *and the entry in the directory.  In other words the original link and any subsequent hard links are nothing more than a mapping between the inode and the file name.  The *inode * is the actually pointer to the block data on the hard disk.  It would look something like this
```

data<---->Inode (200)|<---->Link
                     |<----->Hard Link

```
Looking at this in the terminal.  I created a file named [COLOR=#0000FF]test[/COLOR].  The inode is  12061747.  I create a hard link to this named [COLOR=#0000FF]testlink[/COLOR].  The inode number is the same.  It looks like this (the inode number is on the far right.```
ls -li 
total 0
12061747 -rw-rw-r-- 2 bruce users 0 Feb 18 23:40 test
12061747 -rw-rw-r-- 2 bruce users 0 Feb 18 23:40 testlink

``` 
If I make a sym-link to the original test file it will look like this 
```

12060025 lrwxrwxrwx 1 bruce bruce 4 Mar 18 20:36 symtest -> test
12061747 -rw-rw-r-- 2 bruce users 0 Feb 18 23:40 test
12061747 -rw-rw-r-- 2 bruce users 0 Feb 18 23:40 testlink

```
There is no doubt that the sym-link is at the top.  It shows that it points at the link named test.

What ever you want to use these links, hard links or sym-links for is up to you, but you should have a solid grasp of what they are.
Neither hard links nor sym-links use much space at all.  More importantly, you should know the pro and con of both types.  I use hard links for backups (to make multiple references to the same inode (that points to the data) and sym-links when I want to multiple pointers to the same file name.
 
The real difference is that with hard links the data is not considered deleted until the last link to the inode is unlinked.  In fact that is really what happens when you delete a file.  You unlink the file name from the inode and remove it (the inode).

Since a sym-link is a pointer to a file name you can create sym-links.  NTFS has no inode system you can really make hard links.

Congratulations. It's really a superb explanation.

---

### Post by slickymaster on 2013-03-19
> **GameX2 said:**
> Thank you, I understand the comcept more clearly;
What I find the most confusing with hard links, is that they don't take any space, but a file manager still display that they take up space.  What I should understand, is that the data is deleted when the original (Which cannot be distinguised from the link) and all the hard-links are deleted.

That's a interesting possibility.  Just out of curiosity, does such a thing exist on Windows / OS X (Just curiosity, I find Linux way much better than Windows, but that's a opinion anyways.  No bashing, OS are tools.) ?

Thank you very much.

Yes. Hard links are supported by POSIX-compliant and partially POSIX-compliant operating systems, such as GNU/Linux, Android, Apple's Mac OS X, Windows NT4 and later Windows NT operating systems.
Support also depends on the type of file system being used. For instance, the NTFS file system supports hard links, while FAT does not.

[Hard Links and Junctions (Windows)]("http://msdn.microsoft.com/en-us/library/windows/desktop/aa365006(v=vs.85).aspx")
[Alias (Mac OS and OS X)]("http://en.wikipedia.org/wiki/Alias_(Mac_OS)")

---

### Post by sudodus on 2013-03-19
> **GameX2 said:**
> Thank you, I understand the comcept more clearly;
What I find the most confusing with hard links, is that they don't take any space, but a file manager still display that they take up space.  What I should understand, is that the data is deleted when the original (Which cannot be distinguised from the link) and all the hard-links are deleted.

That's a interesting possibility.  Just out of curiosity, does such a thing exist on Windows / OS X (Just curiosity, I find Linux way much better than Windows, but that's a opinion anyways.  No bashing, OS are tools.) ?

Thank you very much.
If you use du to check the amount of disk used, you will see that it makes no difference when you add hard links.

***cd*** to a test directory with a reasonably big file
```
du 
```
 Make a new hard link to that reasonably big file
```
du 
```
 
If I remember correctly there are no hard links in Windows. I don't know about OS X, but its underlying unix-based system should be able to use hard links.

---

### Post by matt_symes on 2013-03-19
Hi

> What I find the most confusing with hard links, is that they don't take  any space, but a file manager still display that they take up space.

I'm not sure if i understand you correctly here but..

The hard link itself takes up minimal space but the file manager is reporting the size of the file the link points to.

Kind regards

---

