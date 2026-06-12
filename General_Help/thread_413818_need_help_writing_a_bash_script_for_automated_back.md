---
title: "need help writing a bash script for automated backup of files.."
date: 2007-04-19
forum: General Help
---

### Post by billdotson on 2007-04-19
ok.. so I have just gotten Windows completely reinstalled and all of my games installed and patchd up.  Last night I make a ntfsclone backup image and am currently burning it to DVDs (I used bzip2 and split to get them to DVD size) 

I do not want my Windows partition mounted all of the time because w/ ntfsclone or dd if I start a restore or a backup while it is mounted it cause cause serious issues.

So what I was planning on doing is writing a bash script that would automatically mount the Windows partition as read-only on bootup (booting into Ubuntu), then use cp to copy all my save games and application data e.g. my firefox bookmarks and extensions or my thunderbird emails.  Then at the end of the script I would have it unmount the Windows partition after it was done.

The problem is that while I know how to mount and umount the Windows partition.. many of the Windows folders like "Documents and Settings" and "Program Files" have spaces in between the words instead of an underscore or a dash like I would use in Linux.  

Here is what I have so far but I am almost certain w/ the spaces in between the words it will not work:

```

#make sure there is a mount point called /media/Windows first!!
sudo mount /dev/hda1 /media/Windows/ -t ntfs -o nls=utf8,umask=0222
cp /media/Windows/Program Files/Activision/Rome - Total War/saves
sudo umount /media/Windows

```

I started writing it and would have added more savegame locations but I quickly realized that Windows named it's system folders names that have spaces in them.. grrrr.

How do I work around this and get it to work??  I *could* just go into it manually and backup my savegames like normal.. but what if I forget and restore before doing so?  That is why I want this script to run on bootup.

---

### Post by kpkeerthi on 2007-04-19
Change 
```

cp /media/Windows/Program Files/Activision/Rome

```
to 
```

cp /media/Windows/Program\ Files/Activision/Rome

```

---

### Post by billdotson on 2007-04-19
so where there are spaces I put a \ after the word and the have the space?

---

### Post by kpkeerthi on 2007-04-19
Yep! :)

---

### Post by x1a4 on 2007-04-19
Hi,

Where in the boot process do you intend to run your script?  If too early, Ubuntu won't recognize escaped spaces.  In which case replace all your spaces with **\040**. 

So this: 

/media/Windows/Program Files/Activision/Rome

becomes this: 

/media/Windows/Program\040Files/Activision/Rome

---

### Post by billdotson on 2007-04-19
I was planning on making the script, making it executable and then putting it my bin (the one I have in my home folder; I have added it to my PATH) and then going to System >  Preferences > Sessions > Startup Programs and then simply adding the name of the script, which is Windowsbackup.

Can I give cp multiple things to copy and send them all to the same folder?  What about copying only new ones or telling it to copy the contents of a folder instead of copying the actual folder?

Thanks.

---

### Post by x1a4 on 2007-04-19
For backup, just add the **-b** option to **cp**.  This will check if the source file is newer than the destination, and if so, copy it, otherwise **cp** will move on to the next file.  

Use wildcards to copy many files.

* = any character, or sequence of characters
? = one character
[Aa] = capital or lowercase **a**
[abc] = lowercase **a**, **b** or **c**

Use options with **cp**

-f = force copy (no prompt to confirm overwrite; good in scripts where you don't want to have user interraction)
-b = backup (don't copy same file twice, only if it's changed)
-R = recursive copy (copy subdirectories and their contents)
-d = don't dereference links
-p = preserve (keep same mode, ownership, file dates (backup)

For example: 

**cp -fbR /media/Windows/Program\040Files/Activision/Rome/* ~/mywinbackup/rome/**

will copy everything (including subdirectories) in */media/Windows/Program\040Files/Activision/Rome/** to *~/mywinbackup/rome/* without asking to overwrite if files with the same name are there.  It will also check files, and if identical files are found it won't bother copying them (backup).  

**man cp** for more options, or look in the Ubuntu Help Centre.  

To get a script to run at a certain time use **cron** or **anacron** (cron replacement) and/or **atd**

But why bother with scripts and anacron?  Unless you're learning scripting and using this as a practical exercise, just use **simplebackup**, which is a script that does file-based backup.  It's in the Universe repository.  

**sudo apt-get simplebackup**

EDIT: make root:root the owner of the script to run it at boot-time.

---

