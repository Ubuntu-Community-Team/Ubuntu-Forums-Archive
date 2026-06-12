---
title: "Deja-Dup proben when restoring Backup without .manifest file"
date: 2015-09-23
forum: General Help
---

### Post by mandel2 on 2015-09-23
Hello all,

the following happened when i try to resore a backup from an external usb drive.
I have a backup from a home folder of my old computer that i created with deja dup.
I tested this backup on the very system and it worked fine.

Now i am on a new system and Deja dup doesnt recognize this backup anymore.
After it scans the folder for a while, it comes to the conclusion: No backup found.

I tried this command: 
for t in duplicity-full.20150917T153938Z.*.difftar.gz; do tar xf $t; done 
and successfully unpacked the backup to these 2 folders:
snapshot & multivol_snapshot

snapshot is just the folder structure and weights only 3mb.
multivol_snapshot contains all the files but they are displayed as folders.
So i cant execute them, but when i click them i land in a folder that contains 
files with the name 1, 2, 3, 4, 5, ...etc. with no extension.
Also the 2 folders dont have the same size as the source files, tehy are much smaller than the source.

I realized that there is no .manifest file at the source folder, i must have lost it.
Is there a way to regenerate theis .manifest file?
Or do you know another way to restore the files from this backup?

Any help is very much appreciated.

---

