---
title: "Preserve folder structure when using find command"
date: 2016-06-15
forum: General Help
---

### Post by cky on 2016-06-15
Hello, so my question is how to preserve folder path when moving files from one folder to another?

I somehow manage to copy file, but I need to move the files, because then it will take to much time if I always copy files that were already copied.

Command:
```
find /var/spool/asterisk/monitor -name '*-11-*' -print | cpio -pvdumB /tmp/test/
```

So then it has to be in tmp like this:

/tmp/test//var/spool/asterisk/monitor/2016/06...

Thank you for any help.

---

### Post by steeldriver on 2016-06-15
What are you trying to do, exactly? if you want to skip files that are unmodified, then you should probably be using rsync

If you really want to delete the source files after they've been copied, rsync has an option for that as well, I think

---

### Post by ajgreeny on 2016-06-15
The cp command also has a -n option.

From man cp:
```
-n, --no-clobber
              do not overwrite an existing file (overrides a previous -i option)

```

---

### Post by cky on 2016-06-16
Im sorry but none of your methods doesnt do me good, I need to MOVE files because I can't have two of the same files on two locations (space etc.). This command:

```
find /var/spool/asterisk/monitor -name '*-11-*' -print | cpio -pvdumB /tmp/test/
```

does what i am looking for, but instead of COPYING files I need to MOVE files that are found with find command. 

Or if there is a way to add something to remove files that was found at the moment of when the command was runned.

Thanks again.

---

### Post by ajgreeny on 2016-06-16
You mjight be able to do what you want with rsync if you choose the --delete option, though I am still not totally sure what you want.
From man rsync:```

            --del                   an alias for --delete-during
            --delete                delete extraneous files from dest dirs
            --delete-before         receiver deletes before xfer, not during
            --delete-during         receiver deletes during the transfer
            --delete-delay          find deletions during, delete after
            --delete-after          receiver deletes after transfer, not during
            --delete-excluded       also delete excluded files from dest dirs
            --ignore-missing-args   ignore missing source args without error
            --delete-missing-args   delete missing source args from destination
```

---

### Post by steeldriver on 2016-06-16
I guess it depends whether 'copy and delete' will work for you, or you need a true 'move' (source and destination on the same filesystem, just requiring a rename)

If the latter, I don't know any way to do it short of creating the necessary directory structure (e.g. 'mkdir -p') followed by 'mv'

If the former is acceptable, then for example given

```

$ tree dir
dir
&#9500;&#9472;&#9472; subdir1
&#9474;   &#9500;&#9472;&#9472; bar
&#9474;   &#9492;&#9472;&#9472; foo
&#9500;&#9472;&#9472; subdir2
&#9474;   &#9492;&#9472;&#9472; bar
&#9492;&#9472;&#9472; subdir3
    &#9500;&#9472;&#9472; bar
    &#9492;&#9472;&#9472; foo

3 directories, 5 files

```

Then
```

$ rsync -a -m --remove-source-files --include='**/foo' --include='*/' --exclude='*' dir/ newdir/

```

(see, for example, [How to rsync files with matching pattern in path by keeping directory structure intact?]("http://stackoverflow.com/a/28440217/4440445")) results in
```

$ tree newdir
newdir
&#9500;&#9472;&#9472; subdir1
&#9474;   &#9492;&#9472;&#9472; foo
&#9492;&#9472;&#9472; subdir3
    &#9492;&#9472;&#9472; foo

2 directories, 2 files

$ tree dir
dir
&#9500;&#9472;&#9472; subdir1
&#9474;   &#9492;&#9472;&#9472; bar
&#9500;&#9472;&#9472; subdir2
&#9474;   &#9492;&#9472;&#9472; bar
&#9492;&#9472;&#9472; subdir3
    &#9492;&#9472;&#9472; bar

3 directories, 3 files

```

---

### Post by cky on 2016-06-20
> **steeldriver said:**
> I guess it depends whether 'copy and delete' will work for you, or you need a true 'move' (source and destination on the same filesystem, just requiring a rename)

If the latter, I don't know any way to do it short of creating the necessary directory structure (e.g. 'mkdir -p') followed by 'mv'

If the former is acceptable, then for example given

```

$ tree dir
dir
&#9500;&#9472;&#9472; subdir1
&#9474;   &#9500;&#9472;&#9472; bar
&#9474;   &#9492;&#9472;&#9472; foo
&#9500;&#9472;&#9472; subdir2
&#9474;   &#9492;&#9472;&#9472; bar
&#9492;&#9472;&#9472; subdir3
    &#9500;&#9472;&#9472; bar
    &#9492;&#9472;&#9472; foo

3 directories, 5 files

```

Then
```

$ rsync -a -m --remove-source-files --include='**/foo' --include='*/' --exclude='*' dir/ newdir/

```

(see, for example, [How to rsync files with matching pattern in path by keeping directory structure intact?]("http://stackoverflow.com/a/28440217/4440445")) results in
```

$ tree newdir
newdir
&#9500;&#9472;&#9472; subdir1
&#9474;   &#9492;&#9472;&#9472; foo
&#9492;&#9472;&#9472; subdir3
    &#9492;&#9472;&#9472; foo

2 directories, 2 files

$ tree dir
dir
&#9500;&#9472;&#9472; subdir1
&#9474;   &#9492;&#9472;&#9472; bar
&#9500;&#9472;&#9472; subdir2
&#9474;   &#9492;&#9472;&#9472; bar
&#9492;&#9472;&#9472; subdir3
    &#9492;&#9472;&#9472; bar

3 directories, 3 files

```

That's exactly what i was looking for.

Thank you very much.

---

