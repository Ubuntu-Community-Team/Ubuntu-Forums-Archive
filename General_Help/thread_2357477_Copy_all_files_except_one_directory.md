---
title: "Copy all files except one directory"
date: 2017-04-02
forum: General Help
---

### Post by raleigh3 on 2017-04-02
I would like to copy all files from /media/sdb1/Linux_Files/ to /media/andy/DATASTICK/.

Except for the Family_Movies directory.

That directory of files also has a Family_Movies directory within it.

I know I need to use cp for that project.

---

### Post by Dennis N on 2017-04-02
Why not copy them all, then just delete the unwanted folder from the target?

Edit:
If you want to use terminal, I suggest rsync since cp has no exclude option that I am aware of. Use this pattern:

**rsync -r --exclude=a1 source-folder destination-folder**

where a1 is the name of the folder you don't want copied.

---

### Post by &amp;KyT$0P# on 2017-04-02
Try this -
```
cp -pvR $(echo /media/sdb1/Linux_Files/* | sed -r -e '/Family_Movies$/d') /media/andy/DATASTICK
```

That assumes you don't need to copy any hidden files (files with names starting with a dot).  If you do, and if none of your filenames contain any 'weird' characters, you might be able to use this instead -
```
cp -pvR $(ls -A /media/sdb1/Linux_Files/* | sed -r -e '/^Family_Movies$/d' | sed -r -e 's#^#/media/sdb1/Linux_Files/#g') /media/andy/DATASTICK
```


To double-check what the commands are doing without actually running them, prepend [FONT=Courier New]echo[/FONT], e.g.
```
echo cp -pvR $(echo /media/sdb1/Linux_Files/* | sed -r -e '/Family_Movies$/d') /media/andy/DATASTICK
```

---

### Post by raleigh3 on 2017-04-02
> **Dennis N said:**
> Why not copy them all, then just delete the unwanted folder from the target?

Edit:
If you want to use terminal, I suggest rsync since cp has no exclude option that I am aware of. Use this pattern:

rsync -r --exclude=a1 source-folder destination-folder

where a1 is the name of the folder you don't want copied.

Thanks.

I used this 

   ```
sudo rsync -av --progress /media/sdb1/Linux_Files/ /media/andy/DATASTICK --exclude 'Family_Movies'

sending incremental file list


 
total size is 4,242,949,535  speedup is 1.00


```
And got one small error.
As far as I can tell, all files got copied.

```
rsync error: some files/attrs were not transferred (see previous errors) (code 23) at main.c(1183) [sender=3.1.1]
```

I prefer not to just copy and delete the dir because I will be doing this frequently.


Thanks halogen2.

Your reply makes me wonder why would be faster.

Rsync or cp ?

---

### Post by &amp;KyT$0P# on 2017-04-02
I would say the [FONT=Courier New]rsync[/FONT] solution is better, if you can use it -
> **raleigh3 said:**
> I know I need to use cp for that project.

---

### Post by raleigh3 on 2017-04-02
Thanks, I will use rsync whenever possible.

---

### Post by vasa1 on 2017-04-02
In case you didn't know, rsync has a *--dry-run* option so that you can see what will happen if you run the same rsync command without *--dry-run*. From *man rsync*,```
        -n, --dry-run               perform a trial run with no changes made
```

---

### Post by raleigh3 on 2017-04-03
Thanks, I will try it out.

---

