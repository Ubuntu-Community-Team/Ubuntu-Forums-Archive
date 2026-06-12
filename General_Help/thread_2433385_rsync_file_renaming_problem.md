---
title: "rsync file renaming problem"
date: 2019-12-18
forum: General Help
---

### Post by eMshsWE on 2019-12-18
Hi, I am trying to make rsync Linux command work after file renaming has  been done. To show this, I created a directory with a single file 'a'  and ran an rsync command

[ATTACH=CONFIG]284632[/ATTACH]

Then I ran an "rsync" command as follows :-
```

ramasea1 ~ $ rsync -auzv ~/Documents/RsyncDemo/source/ ~/Documents/RsyncDemo/dest/
sending incremental file list
./
a

sent 591 bytes  received 38 bytes  1,258.00 bytes/sec
total size is 679  speedup is 1.08


```

So now in my dest folder I have the file "a".

Now I went back to my "source" folder and renamed the file "a" to "a_new"

and then ran the rsync command as follows
```

ramasea1 ~ $ rsync -auzv ~/Documents/RsyncDemo/source/ ~/Documents/RsyncDemo/dest/
sending incremental file list
./
a_new

sent 595 bytes  received 38 bytes  1,266.00 bytes/sec
total size is 679  speedup is 1.07

```

Now in my "dest" folder, I have both the old "a" file as well as the renamed "a_new" file. 

[ATTACH=CONFIG]284631[/ATTACH]


While ideally, I would have preferred only the new "a_new" file to be there

Could someone please help me out?

Regards,
Ajayram

---

### Post by tea for one on 2019-12-18
You will need the flag/option which deletes files on destination.```
--delete
```

Sometimes it is easier to use **grsync**, which is a GUI wrapper for **rsync**

---

### Post by TheFu on 2019-12-18
By default, rsync is additive. It only adds new files or updates files.
As tea for one said, there is a --delete option if you want a mirror of the 2 directories.  There are multiple variants of that to control whether the files not to be retained are deleted before or after the rest of the rsync operations in that directory are handled.  If you don't have enough room in the target area, --delete-before is the option.  If you do have plenty of space in the target, --delete-after would be safer.

The rsync manpage is a freakin' work of art. Highly, highly recommended.

```
$ man rsync 
...
            --del                   an alias for --delete-during
            --delete                delete extraneous files from dest dirs
            --delete-before         receiver deletes before xfer, not during
            --delete-during         receiver deletes during the transfer
            --delete-delay          find deletions during, delete after
            --delete-after          receiver deletes after transfer, not during
            --delete-excluded       also delete excluded files from dest dirs
...
```

---

### Post by HermanAB on 2019-12-18
There is also a max delete option to protect against catastrophic accidental deletes of your backups.

---

### Post by eMshsWE on 2019-12-21
Hi 
I tried with --delete but then it threw this error
```
 rsync --delete source/ ./dest/
rsync: --delete does not work without --recursive (-r) or --dirs (-d).
rsync error: syntax or usage error (code 1) at main.c(1585) [client=3.1.2]

```

So then I added this option also. Generally I use rsync with these options -a (for archive mode), -u (for update mode, skip files that are newer on the receiver), -z (compress files during the transfer) and -v (verbose) . I have not used -r option earlier.
Then I tried rsync -auzvr --delete and It seems to work fine.
```
ramasea1 RsyncDemo $ rsync -auzvr --delete source/ ./dest/
sending incremental file list
deleting a
./

sent 86 bytes  received 20 bytes  212.00 bytes/sec
total size is 679  speedup is 6.41

```

Will this also work if I shift the contents of a subdirectory under source to a new directory under source. ie Folders "A" and "B" were cut and pasted into a new folder "C" .So initially source directory had only folders "A" and "B"., now it has only folder "C" under which there are folders "A" and "B". Will rsync -auzvr --detele work in this case as well?

---

### Post by TheFu on 2019-12-21
> **eMshsWE said:**
> 
Will this also work if I shift the contents of a subdirectory under source to a new directory under source. ie Folders "A" and "B" were cut and pasted into a new folder "C" .So initially source directory had only folders "A" and "B"., now it has only folder "C" under which there are folders "A" and "B". Will rsync -auzvr _--detele_ work in this case as well?

Test it, but I doubt it will work since --delete is spelled that way, not the way you've done it above.
There is a **--dry-run** option for rsync.  Add that and see what happens.  There's always the manpage - which you should read on the -a option.  Using "-a" adds a few other options that don't need to be added.

I tend to use **rsync -avz SOURCE/  TARGET/** and only change from that for specific needs.

---

### Post by eMshsWE on 2019-12-21
My bad in the typo I meant rsync -auzvr _--delete _  only . Ok sure, I will check the man pages. Can I mark this thread as solved then?

---

### Post by cpt-ankitsharma on 2019-12-21
[https://lincolnloop.com/blog/detecting-file-moves-renames-rsync/](https://lincolnloop.com/blog/detecting-file-moves-renames-rsync/)

Nice explanation on handling rsync with renamed file structures.

---

