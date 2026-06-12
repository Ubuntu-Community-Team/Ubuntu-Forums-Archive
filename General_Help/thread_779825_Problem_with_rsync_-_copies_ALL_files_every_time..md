---
title: "Problem with rsync - copies ALL files every time."
date: 2008-05-03
forum: General Help
---

### Post by musther on 2008-05-03
Have a little script which is called from a menu item, I use it to back up my home folder to an external USB drive (encrypted with encfs).  

It used to work, but at some point recently (I think it was before I upgraded to 8.04) it started copying all the files rather than just those that had changed, and I don't know why.  What I do know, is that it's a real pain and takes ages.

Here's the script so you can see the rsync command, and anything else that could be having an effect.

```
#!/bin/bash
#
echo "Please ensure that the USB drive is plugged in and mounted as /mdedia/disk, then press enter to continue."
read
clear
echo "Please enter the password for the encrypted filesystem:"
encfs /media/disk/backup /home/backup/bkpmusther
clear
rsync -r -h --progress -A -o -g -t -E -p --delete /home/musther /home/backup/bkpmusther
clear
fusermount -u /home/backup/bkpmusther
exit
```

Thanks

---

### Post by Aearenda on 2008-05-03
I don't know whether this applies here or not, but I ran into a similar problem some time ago, where it was the timestamps that caused the extra copying. The target filesystem didn't preserve the timestamps with as much detail, so it was always 'different'. Just a thought.

---

### Post by qpieus on 2008-05-03
I think Aearenda is on the right track. I had the same problem when rsync-ing to a fat32 drive. rsync copied every file even if it already existed on the destination. There's some issue with file timestamps on fat32 devices, so to rsync it looked like the file on the fat32 device was a different file - that's why rsync copied all the files every time.

I fixed this by putting this switch in my rsync command```
--modify-window=1
```

I don't know anything about encfs, but I maybe the file timestamps are the problem, just like with my fat32 drive (although this doesn't explain why you didn't have this problem before).

---

### Post by musther on 2008-05-03
Indeed, my external drive is ext2, but the encfs could be something to do with it.  It is possible that I changed the script at some point, and that's when I started getting the errors, but I honestly can't remember.

What does the switch:
```
--modify-window=1
```
do?  Couldn't I just remove the -t from my command?

---

### Post by musther on 2008-05-03
Ok, well I learnt what it meant, and I tried it, but it still copied every file....

---

