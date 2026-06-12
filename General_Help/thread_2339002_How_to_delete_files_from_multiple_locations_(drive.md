---
title: "How to delete files from multiple locations (drives) from a certain date?"
date: 2016-10-03
forum: General Help
---

### Post by PrvSAT on 2016-10-03
I have searched for this issue that I have and could not find exactly what I wish to achieve.
I have 8 hard drives with media files in various directories and by mistake Kodi added to these locations lots pf jpg and nfo files. The date is Sept 30 and all files that I wish to delete were created then.
What command should I use to erase files created on Sep 30 on multiple hard drives (connected via USB).

I have found this:
[COLOR=#111111][FONT=Consolas]find . -maxdepth 1 -type f -newermt 2011-08-01 ! -newermt 2011-08-06 -delete
[/FONT][/COLOR]but it is specific for one location and not sure if it is applicable to me. I do not wish to screw something up. Please help.

---

### Post by HermanAB on 2016-10-04
Linux has a single directory tree.

Find '.' means to start from the current directory.  So all you need to do is start it at a suitable point in the tree, so it will recurse everything.  You could start at / for  example.

You should make a backup before you start though.

---

### Post by T2uiYKb7 on 2016-10-04
I thought EXT4 doesn't record the time a file was created/born? I've wanted to do something similar in the past but was told it wasn't possible?

---

### Post by QLee on 2016-10-04
> **andrew.nz said:**
> I thought EXT4 doesn't record the time a file was created/born? I've wanted to do something similar in the past but was told it wasn't possible?

Can you provide any documentation to support your assertion?

---

### Post by T2uiYKb7 on 2016-10-04
As you can see I'm simply saying what I've been told not that it's correct. But now I've looked into I think it is right.

[http://pubs.opengroup.org/onlinepubs/9699919799/basedefs/V1_chap04.html](http://pubs.opengroup.org/onlinepubs/9699919799/basedefs/V1_chap04.html)

[http://unix.stackexchange.com/questions/7562/what-file-systems-on-linux-store-the-creation-time](http://unix.stackexchange.com/questions/7562/what-file-systems-on-linux-store-the-creation-time)

[http://unix.stackexchange.com/questions/91197/how-to-find-creation-date-of-file](http://unix.stackexchange.com/questions/91197/how-to-find-creation-date-of-file)

Under Ubuntu EXT4 uses POSIX for file attributes. Which records:

[B]Last modification
Last access
Last permission change

[/B]Try looking at a files attributes with any file manager and you'll see it lists these but not creation time.

[B]Edit: Try:

[COLOR=#0000ff][I]stat ~/Pictures/YourPhoto.jpeg
[/I][/COLOR]
You'll see it says:

Access: Info
Access: Time
Modify: Time
Chang: Time
Birth: -
[/B]

---

### Post by T2uiYKb7 on 2016-10-04
[IMG]https://s13.postimg.org/p3513stlz/image.png[/IMG]

---

### Post by QLee on 2016-10-04
In the specific situation that the OP detailed, from context I understood, (or thought I did), that all the files in question had *not* been modified and all had the same date. I wouldn't want to suggest anything to the OP that would question HermanAB's solution which I think is correct.

Yes, I do know how to use a File Manager.

We have just clarified everything.

Edit: Sorry for the dup. My fault.

---

### Post by T2uiYKb7 on 2016-10-04
Slightly off topic but it seems bizarre for an OS not to show/record when a file was created. Three things are recorded, things that are potentially changing on a regular basis but not something as simple as birth/creation???

---

