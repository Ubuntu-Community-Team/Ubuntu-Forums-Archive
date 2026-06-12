---
title: "How to use 'mv' using rsync to backup"
date: 2007-01-22
forum: General Help
---

### Post by Underpants on 2007-01-22
I've been reading: 
```
http://www.mikerubel.org/computers/rsync_snapshots/
```

I might be making a noob mistake somewhere with the "mv" command.

I'm just playing around right now with some directories. 

I have "source" "dest-a" and "dest-b"

I do an rsync from source to "dest-a" 

then I do # mv dest-a dest-b

and it moves not the contents of -a, but the whole dest-a folder into dest-b, so i end up with something like this

--- before mv ----

```


/dest-a/file1.txt
/dest-a/file2.txt

/dest-b/


```

--- after mv ---

```
/dest-b/dest-a/file1.txt
     /file2.txt
```




I'm sure that will make sense to someone. :rolleyes: 

Anyway, don't I want to just move the files, not the entire directories?

---

### Post by Dubbayoo on 2007-01-22
you need to use a trailing / with rsync. check the man page; it's very good.

---

### Post by Underpants on 2007-01-22
> **Dubbayoo said:**
> you need to use a trailing / with rsync. check the man page; it's very good.

My question isn't really pertaining to rsync, it's about 'mv'

---

### Post by po0f on 2007-01-22
Underpants,

You're telling `mv` to move the directory, not the contents.  The following will do what you want it to:
```
[FONT="Courier New"]$ mv dest-a/* dest-b[/FONT]
```

---

### Post by Underpants on 2007-01-22
Taken From ```
http://www.oreilly.com/pub/h/42#code
```

```
# step 2: shift the middle snapshots(s) back by one, if they exist
if [ -d $SNAPSHOT_Rw/home/hourly.2 ] ; then \
$MV $SNAPSHOT_Rw/home/hourly.2 $SNAPSHOT_Rw/home/hourly.3 ; \
fi;
```

Wouldn't this move the hourly.2 folder into the hourly.3 folder? vs. moving all of the contents?

---

### Post by Underpants on 2007-01-22
Also, mv dest-a/* doesn't move .hidden files.

---

### Post by po0f on 2007-01-22
Underpants,

The snip you posted moves the folder and contents, not just the contents.

To move hidden files as well:
```
[FONT="Courier New"]$ mv dest-a/.* dest-b[/FONT]
```

From the script you linked to, the "hourly.3" directory should be deleted before the `mv hourly.2 hourly.3` takes place.  For some reason it's not, and the "hourly.2" directory is just being put inside the "hourly.3" folder.  You didn't change the script at all did you?  The script linked to is fine; there is problem with its execution on your end though.

---

### Post by Underpants on 2007-01-23
I'm not actually using that script. Just testing other things out with smaller file trees so testing wont' take as long. I'll just edit the damn thing to fit my needs and learn it that way.

---

