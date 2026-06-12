---
title: "Copy files to second drive"
date: 2016-08-04
forum: General Help
---

### Post by 4kh3RAm on 2016-08-04
Since I am no longer using sudo, this does not work due to not having permission.

I use it in a script.

```
cp -u -f Ubuntu_Documents.zip /media/andy/MAXTOR_SDB1/Linux_Files
```

---

### Post by &amp;KyT$0P# on 2016-08-04
Assuming this is a backup script, probably you just want to add sudo to the front of that cp line?
Don't see what's wrong with running that specific command as root.

---

### Post by 4kh3RAm on 2016-08-04
Okay.

For some reason, this opens as a superuser and I don't know why ?

```
thunar /home/andy/Scripts/

```
This opens as non-root.

```
thunar /home/andy/Documents/
```

---

### Post by mook765 on 2016-08-04
You need read-permission for the source file _and_ write-permission for the destination to success in this copy operation.
You can ship around this using sudo, like halogen2 suggested, or you check and change the permissions of source and/or destination using chmod.
> 
[http://linuxcommand.org/lc3_lts0090.php](http://linuxcommand.org/lc3_lts0090.php)


---

### Post by 4kh3RAm on 2016-08-04
I tried this while in my backup directory, but root remained the owner.

```
sudo chown andy:andy /home/andy
```

Is chmod 666 what I want ?

I tried chmod 666 *.*, but I guess it does not accept wildcards.

sudo chmod 666 Linux_Files resulted in my not being able to change into that directory.

Running that really messed things up. :-(

---

### Post by Dennis N on 2016-08-04
> sudo chmod 666 Linux_Files resulted in my not being able to change into that directory.

To be able to access files in a directory requires execute permission on the directory - the permissions are normally 755 for directories.

7 = read, write, and execute.
6 = read and write.
5 = read and execute.

---

### Post by &amp;KyT$0P# on 2016-08-04
Running chown or chmod on a backup is dangerous.  You've locked yourself out of all the directories by doing chmod 666.  For directories, you want either 0555 (read-browse for all) or, more likely, 0755 (read-write-browse for owner, read-browse for group & others) or 0750 (same as 0755 but disabling all access for others).  Directories need to be marked executable in order to browse.

That chown command applied to your home directory, not your backup directory, so it presumably had no effect.

Anyway, this should reverse the damage done to the directories on your second drive:
```
sudo find /media/andy/MAXTOR_SDB1 -type d -exec chmod 0750 "{}" \;
```
Of course, replacing 0750 with 0755 if that's preferable to you.
Refer to the man pages of find and chmod for more information about this command.

If it gives errors, you should be able to just run it again (and get different errors) until it doesn't give errors anymore.

Given that the files likely didn't have uniform permissions, I do not know an easy way to reverse the damage done to the files, sorry.  I'd suggest to simply make another backup.

---

### Post by 4kh3RAm on 2016-08-04
thanks a lot. This got the directory to it's previous state.

```
sudo find /media/andy/MAXTOR_SDB1 -type d -exec chmod 0755 "{}" \;
```

---

### Post by &amp;KyT$0P# on 2016-08-04
You're welcome  :KS

---

