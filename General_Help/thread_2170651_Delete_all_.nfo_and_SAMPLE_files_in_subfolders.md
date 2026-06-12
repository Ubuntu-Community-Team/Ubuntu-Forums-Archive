---
title: "Delete all .nfo and SAMPLE files in subfolders"
date: 2013-08-27
forum: General Help
---

### Post by ialvik on 2013-08-27
Hi

I have about 600 folders that contains useless files with the word SAMPLE, .SAMPLE and .nfo files
These are on different HDD's but i used union-fs so they are all in one folder and I added the RW, so I can delete files from this folder
Is there any terminal command i can use to delete them all at once?

Thanks for reading my post :)

-Iver

---

### Post by steeldriver on 2013-08-27
You could use 'find' with the -delete action

!! USE WITH CAUTION: IT WILL DO EXACTLY WHAT IT SAYS, NO BACKOUT, NO CONFIRMATION !!

```
find /path/to/dir \( -name '*SAMPLE*' -o -name '*.nfo' \) -type f -delete
```

I recommend you do

```
find /path/to/dir \( -name '*SAMPLE*' -o -name '*.nfo' \) -type f **-print**
```

first and at least glance over the list to make sure it's not going to find/delete anything you don't want it to

---

### Post by ialvik on 2013-08-27
Thanks!! That cleaned up a lot :)

---

