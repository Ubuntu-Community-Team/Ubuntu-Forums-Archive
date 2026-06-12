---
title: "rsync problem"
date: 2019-02-10
forum: General Help
---

### Post by alansecker on 2019-02-10
Following a rebuild, I ran two scripts, the first to mount remote shares and the second to backup.
Both scripts had been successfully run for several years. But now under 18.04 they stumble.

I had always mounted the shares on my home directory and used "exclude-from" to avoid copying the folder on which the shares were mounted.
Now, this fails to stop recursive copying, ending up with a full drive!   Clearly something is wrong with my  rsync syntax.

As a workaround, I decided to mount the shares under /mnt but that produced error messages like:

Couldn't chdir to /mnt/churchill/public/: No such file or directory - but there is!

The full mount statement ( Note: 192.168.0.66 is 'churchill')

mount -t cifs -o rw,noperm,user=<me>,password=<mypasswd>,domain=ASANDCO,vers=1.0 //192.168.0.66/public/  /mnt/churchill/public 

The original mount point was: /home/me/mnt/churchill/public/

As the script is run from a # prompt I cannot fathom why this should be.

---

### Post by dragonfly41 on 2019-02-10
Try the gui Grsync initially in "dry run" mode (the blue button in top bar). Tick "verbose" in basic options for detailed report.

[COLOR=#b22222]{Later edit][/COLOR] Also understand the implications of [closing slash]("http://qdosmsq.dunbar-it.co.uk/blog/2013/02/rsync-to-slash-or-not-to-slash/"). I think that this might be the cause of your drive filling up.

---

### Post by TheFu on 2019-02-10
And what, exactly, is the rsync command?

---

### Post by dmnur on 2019-02-10
Consider this example:
```
rsync --recursive --exclude /mnt/ ~/ ~/mnt/churchill/public
```
This will sync all contents of your home directory to **~/mnt/churchill/public**, excluding **~/mnt** and its contents (because **--recursive** makes exclusion rules recursive as well).
Exclusion rules are always *relative to the source directory*, so specifying **/mnt/** means "exclude the **mnt** directory that's in the root of the source directory".

This won't work: **--exclude ~/mnt/**
Because this will match the following (assuming your home directory is **/home/you**): **/home/you/home/you/mnt/**

So check if your exclusion rule is correct.

---

### Post by TheFu on 2019-02-11
Writing backups to CIFS storage loses all the permissions.  For HOME backups, this isn't a big deal. For system backups, you'll never be able to restore and get a working system.

As for rsync options, I tend to use **rsync -avz SOURCE TARGET**  You can lookup the options in the manpage.  This is good for network rsync's, but for disk-to-disk rsync's (which includes network mounts since rsync doesn't know about the network), it doesn't use diffs to send only changes. If the files don't match, it will only send the "SOURCE" if it is newer. For local copies, it is probably best to just use the timestamp.  For remote, it is best to use rsync on both sides and not use network storage.  That means either having rsyncd listening or using ssh+rsync, then the diff optimization of rsync will be used.  The rsync manpage is very complete with explanations, but very long.

---

