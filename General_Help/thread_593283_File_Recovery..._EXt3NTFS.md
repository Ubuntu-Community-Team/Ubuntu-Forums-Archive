---
title: "File Recovery... EXt3/NTFS"
date: 2007-10-27
forum: General Help
---

### Post by #Reistlehr- on 2007-10-27
Ok, so i'm hving one of those nights. Get stood up on a date, it's raining, stubbed my finger, my motherboard on one of my servers died, somehow webdav broke my svn, my mythbox won't record anymore... yeah

Ontop of it, i was recovering some files off my servers one HD. The server HD is an NTFS partition. Well i was copying the files from the NTFS partition to the EXT3 partition, and for some reason they copied to ./ Now, those of you know . is current working directory. Well, it make a directory called . for some reason, and then moved the files off NTFS to the ./ directory, not the cwd. 

I am so angry at mysqlf, cause it's almost a 98% garuntee it's a pebkac error. Now, i tried foremost, recover, and debugfs -w, but sicne it made the dir called . and move the files into it, when i try to go into the directory, it just stays in the cwd. So i am so stumped. haha.

Now, i was thnking. if i was moving files from the NTFS drive to the EXT3 drive, shouldn't the files have been treated like they were deleted off the NTFS drive, so it should be possible to recover the files of the NTFS drive?

I'm no stranger to data carving, and data recovery. A lot of the tools i had, don't read journaling file systems like EXT3/Reiser FS/JFS/XFS.. AccessData comes in no handy...

Any insight or pointers or ideas would be greatly appreciated.

The files have an array of extensions from .mda, .mdf, .php, .doc and .ags

---

### Post by Ptero-4 on 2007-10-27
have you tried using the nautilus/thunar show hidden files option and clicking on the . dir and renaming it (you'll see two if the filemanager shows the "." and ".." dirs, just click them one and then the other, the one with a size diferent to it's parent dir is your "backup" dir).

---

