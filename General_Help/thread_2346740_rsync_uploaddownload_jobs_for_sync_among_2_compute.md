---
title: "rsync upload/download jobs for sync among 2 computers and 1 NAS"
date: 2016-12-18
forum: General Help
---

### Post by alain.roger on 2016-12-18
Hi,

i'm coming back to this topic as something is not clear even after few tests i performed.

i have a laptop with a folder called "original" including a test.txt file.

when i run the following command everything is synced/backuped to my NAS folder as planned:
```
rsync -avzP /mnt/TempData/test/original/ /mnt/nas/test/sync/
```

It works greats as it copy the whole /mnt/TempData/test/original/ content to /mnt/nas/test/sync/
and if files content's changed then it is correctly copied to nas folder.

my question is the following one:
if my desktop computer has the same command line but with a different source to the same destination folder, and the content of this source is different.... will it erase the whole content of the NAS destion folder ?

How should i do to make sure that differences of source content from 1 computer does not erase the content or destination NAS folder and if files are the same, that only the latest version is saved (so the newest one overrite the oldest one) ?

in other terms:
if laptop source folder content is:
- /test/original/test.txt (150b)
- /test/original/folder1/file.txt (1k)

first sync with see on NAS destination folder:
- /test/sync/test.txt (150b)
- /test/sync/folder1/file.txt (1k)

Now if desktop computer syn the following content:
- /test/original2/test.txt (200kb)
- /test/originial2/folder2/file-test.doc

i would like to have on my NAS destination folder:
- /test/sync/test.txt (200kb)
- /test/sync/folder1/file.txt (1k)
- /test/sync/folder2/file-test.doc

AFAIK, rsync do a complete backup or differential of content, it does not care about file itself.... the last job overwrite everything on destination

thx

---

### Post by ajgreeny on 2016-12-18
I am not quite sure what you're trying to do, but it looks as if you want to avoid changing files on the destination if the source file happens to be different from that already on the destination, but is an earlier version, which might well be the case if you are using the same physical destination drive, but two or more different sources from other computers.

If you look in **man rsync** you will see that is easy to do by simply using the option -u which should ensure that you always have the most recent file in the destination.
Just make sure the source file timestamps are always correct.
```
       -u, --update
              This forces rsync to skip any files which exist on the destination and have a  modified  time  that  is
              newer  than  the  source  file.   (If an existing destination file has a modification time equal to the
              source file&#8217;s, it will be updated if the sizes are different.)
```
If this is not your problem ask again with more detail of what you want and I'm sure we can try again.

---

### Post by Keith_Helms on 2016-12-18
As long as you don't use the --delete option, rsync will not remove files on the receiving side that are not present on the sending side.  Is that what you were asking?

---

