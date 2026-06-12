---
title: "Cut-Paste-Skip Files Gone-Problem"
date: 2013-06-11
forum: General Help
---

### Post by DocHotzenplotz on 2013-06-11
Hy,
please give me direction for my problem:

On different computers I want to put all my documents together in one folder. So it could had happen that some folders have the same names but not the same contents.

I started to Cut and Paste one main folder, with subfolders into another drive when the OS said: folder XY already exists - What to do?
In this case I cklicked on SKIP to do it later "by hand".

When I went back to the folder I cut out - the skipped folders from the process above werent there. 

For me thats not logic - when I skip the process, why are they gone? 

Anyway, I would like to find these files, where are they?


Thanks,

from DocHotzenplotz - der mit der Bratwurst

---

### Post by HermanAB on 2013-06-11
If the files were really unlinked, then they have gone to La La Land and it is time to go look for the backups.

If you are lucky, the file browser that you used simply hasn't refreshed its display and they are still there.

---

### Post by DocHotzenplotz on 2013-06-11
That means: If I skip a process of pasting, because the filename already exists in the final folder the skiped file will be deleted? mhh, I am not following this kind of logic...

What is the meaning of a "linked file" ?

I checked the refreshments after reboot,  but there was nothing left. The original folder was empty

---

### Post by HermanAB on 2013-06-11
The Linux file systems typically use a tree structure and deletes a file by unlinking the inode.

So, yeah, I seldom use cut and paste (mv) on files.  Copy and paste (cp) and delete (rm) later, is generally safer.

Also, tar is your friend!  Learn how to use tar and life will be good.  It is generally 'tar -zcvf filename.tgz *' and 'tar -zxvf filename.tgz'.  Always tar a directory and never tar just a bunch of files, is another courtesy rule to remember, since it is really annoying when you untar an archive and it spills ten thousand files all over your home directory.

---

