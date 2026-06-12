---
title: "Consolidating and Organizing Backups"
date: 2006-10-31
forum: General Help
---

### Post by moon2js on 2006-10-31
I have various backups of files across two machines, all of which have slightly different directory trees yet much of it contains the same files. (Different backups from different points in time mostly.)

Can anyone point me in the direction of some Ubuntu/Linux tools that I can use to go through these files and consolidate them without losing anything?

For example, I might have three archives, and maybe two of them have pictures from my vacation in Canada but one might have a few more or less and another might have pics from Alaska too AND each might have them in different(ly named) directories.

Is there any automated way to do this (rsync?) because going through these manually could take weeks. Can anyone point me to such a guide/howto or suggest some search terms so I can google?

---

### Post by Roobert on 2006-10-31
Sounds like you need version control. Have you looked at subversion?

[http://subversion.tigris.org/]("http://subversion.tigris.org/")

But I'm not sure how effective it would be reconciling files with *different* names.

---

### Post by matthewstory on 2006-10-31
Um . . . without a naming convention for this stuff version control won't help, and version control also won't help with the initial consolidation.  It'll only help to manage your files after you consolidate them, but that would be a good idea for you after you consolidate.  If you have naming conventions for your files, you could possible set up an NFS or SAMBA server temporarily to get all the files on the visable on the same machine, and then write a bash or perl script to systematically go through and compare and organize files into folders based on the names of those files.

If you're looking to mesh your stuff together, rsync also isn't the right solution, as rsync is designed for backing up the contents of one directory to another one.

I don't know if you're looking for something much simpler, but i do have a script that goes through a given directory and tars up all the subdirectories of that directory.  If you want that script it's yours, but it doesn't really sound like what you're looking for.

If you do have a naming convention i'm sure the lovely people on this forum would be more than happy to help you write a script using reg exs to organize your files accordingly.

---

### Post by moon2js on 2006-11-02
Well, actually, I was thinking along these lines: I'd be happy if I could just delete redundant files. For example, I might have five copies of the exact same PicXYZ.jpg across three archives, in different directories. Is there a way to write a script that will go through the various archives and delete all redundant copies (as long as they are exactly the same, same byte size, etc.).

It wouldn't so bad to manually consolidate, move, merge as long as I don't have to look at each file, comparing modification dates and byte sizes to see if two files are exactly the same and it's safe to delete one.

---

