---
title: "[SOLVED] consolidate files"
date: 2008-06-16
forum: General Help
---

### Post by c1rcu17 on 2008-06-16
I need a bit of help consolidating some files on my desktop. I have 80 separate files, each one very big, and each one in its own folder. I want to move all the files out of their own folders and into one big community one. Moving each one out of its own folder into one big folder would take forever. I also don't have the hard drive space to copy the files. It needs to be a straight cut & past maneuver. They are all of the same file type and the name differs by having a 0-79 number difference in it

For example, the files are in ~/folder/A1/File0.txt
                              ~/folder/A2/File1.txt
                              ~/folder/A3/File2.txt

I want File 1, 2 and 3 to be in ~/folder, and not in its own folder.

So it should look like,    ~/folder/File0.txt
                           ~/folder/File1.txt
                           ~/folder/File2.txt

I'm sure that a bash or perl script can be used, but I don't really know how. Can the "mv" command be used? Or should I do something else?

---

### Post by sdennie on 2008-06-16
You can use "mv" or, you can just symlink the files.  Something like this will keep the files in their original location while also making them appear in ~/folder:

```

cd ~/folder
ln -s `find . -type f` .

```

You'll likely get some warning with that command but, it should do what you want.

---

