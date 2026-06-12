---
title: "[SOLVED] how do i use the cp (copy) command to copy directories WITHOUT the top level"
date: 2008-04-11
forum: General Help
---

### Post by bluepowder7 on 2008-04-11
here's something i run into, and don't know how to manipulate to work how i'd want.

let's say i have a folder called topfolder, and inside of that i have a bunch of other folders (middlefolder1 to middlefolder9) and a bunch of files (middlefile1 to middlefile9).  now, if i want to copy all those middlefolders and middlefiles over to some other spot (like a backup hard drive), i normally write:

```

cp -R /media/topfolder /media/backuplocation

```

however, that copies the topfolder as well, so it results in me having this useless layer on the backup location (/media/backuplocation/topfolder).

what command do i need to write to skip that topfolder layer and start copying from the middle... layer, so that it ends up in /media/backuplocatio/middlefolder1 and /media/backuplocatio/middlefolder2 and so no?

i tried doing

```

cp -R /media/topfolder/ /media/backuplocation

```

with the extra slash after topfolder, but that doesn't work.  since i have a LOT of middlefolders, i'd rather not have to do them one by one by one...

---

### Post by sillyxone on 2008-04-11
how about
```
cp -R /media/topfolder/* /media/backuplocation
```


just curious, don't you want to use rsync for backup? it's faster than cp with its incremental/differential backup. First copy is as slow as cp, but subsequent runs will be much faster, especially if you have only small changes.

---

### Post by bluepowder7 on 2008-04-11
thanks!  that works exactly like i want it to.

it's not for regularly recurring backups, but rather to copy folders from a rescued hard drive so that i can sort out the files i need to keep.  i find myself moving and reorganizing things fairly regularly, either on the desktop pc or on the server, so it's nice to know how to make the command do what i want it to do.

for example, when a buddy gives me a giant portable hard drive full of video clips or scanned photographs, i hook it up via USB directly to my server and then want to copy them over, and for that i use the terminal - but i don't want an extra layer of folders making life difficult.

---

