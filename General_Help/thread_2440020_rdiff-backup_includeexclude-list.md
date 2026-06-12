---
title: "rdiff-backup include/exclude-list"
date: 2020-04-04
forum: General Help
---

### Post by Quarkrad on 2020-04-04
I keep reading about the rdiff-backup option **--exclude-filelist exclude-list** where this exclude-list contains files or folders you want to exclude. But I cannot find out where this file is located.  If I wanted to copy my /home folder using rdiff-backup but wanted to exclude the Downloads directory, using the filelist method, do I just create a simple text file (called exclude-list) containing ~/Downloads? And more importantly, where would I save this file?

---

### Post by Quarkrad on 2020-04-04
Apologies - the only place I hadn't tried locating the file was my home folder.  Just did this and it worked.

---

### Post by kevdog on 2020-04-05
The file could be anywhere actually -- just give the full path to the file --- /home/john/dir1/dir2/excludes.txt  (just an example).

---

### Post by Quarkrad on 2020-04-05
Afraid I still don't quite get this.  If we take **rdiff-backup /media/username/dir1 /media/username/backup** and then decide to have an exclusion list we could have **rdiff-backup --exclude-filelist exclude-list /media/username/dir1 /media/username/backup** - this is sort of what I have done and it works by putting exclude-list in /username.  But where in **rdiff-backup --exclude-filelist exclude-list /media/username/dir1 /media/username/backup** does it know that exclude-list is in /username?  I assumed it works that way as default. When you say exclude-list could be anywhere how does the rdiff-backup ....... command know where to look for the exclude list?  Obviously this applies to a include list.  I've gone through the man pages and not found the answer - perhaps I've missed it.

---

### Post by TheFu on 2020-04-05
```
rdiff-backup --exclude-filelist "./exclude-list" 
```

is the example name.  In scripts, never assume a PWD.  Always fully specify exact locations for files. Scripts need to work from any directory, regardless of the PWD.

```
rdiff-backup --exclude-filelist "/home/thefu/bin/backups-not-to-be-included" 
```
Or better:
```
rdiff-backup --exclude-filelist "/root/bin/backups-not-to-be-included" 
```

Because backups really need to be run by root, not some other userid.

```
cd /tmp
~thefu/bin/backup-script

```
Should work.

```
cd /etc
~thefu/bin/backup-script

```Should work too.

But I'd never trust 
```
cd /etc
~/bin/backup-script
```
Because HOME may not be set, so that command could be looking for /bin/backup-script, not the intended /home/thefu/bin/backup-script.

Das ist klar?

Don't use relative paths for **any** files or programs inside a script.  If you plan to automate a script, say through a crontab, then definitely NEVER trust the PATH or PWD.

I tend to work the other way. Rather than exclude specific things, I include the stuff needed and exclude EVERYTHING else.  My backups don't want everything, just the stuff I need to recreate the system.

---

### Post by Quarkrad on 2020-04-06
I'm currently stuck using a include-list. I am practicing with the command  **rdiff-backup --include /home/dad/Documents --include /home/dad/Desktop --exclude "/home/dad/**" /home/dad/ /destination directory **  ...this works, its puts the Documents and Desktop folders, AND all their respective contents, in the  destination directory (local - different HD).  However, when I use the command **rdiff-backup --include-filelist include-list --exclude "/home/dad/**" /home/dad/ /destination directory**   the Documents and Desktop folders are copied to the destination directory but only the folders themselves, not their contents.  My include-list looks like:

/home/dad/Desktop
/home/dad/Documents

I have tried various options like:

/home/dad/Desktop/**
/home/dad/Documents/**

and

/home/dad/Desktop/*.*
/home/dad/Documents/*.*

but whatever changes I make only the top level folders are copied - not their contents.  Any advice most appreciated - so far I have found very little net-help re the configuration of the include/exclude-list file(s).

---

### Post by TheFu on 2020-04-06
The order of options matter, just like with rsync.
Also, to ensure the shell doesn't expand the regex patterns, use ', not " for quoting.  So, ```
--exclude '**'
```, not ```
--exclude "**"
```

[http://rdiff-backup.nongnu.org/examples.html](http://rdiff-backup.nongnu.org/examples.html)
> Multiple include and exclude options take precedence in the order they are given. 

The manpage has this:
```

       For instance,

              rdiff-backup --include /usr --exclude /usr /usr /backup

       is exactly the same as

              rdiff-backup /usr /backup

       because  the  include  and  exclude  directives  match exactly the same
       files, and the --include comes first, giving it **precedence**.  Similarly,

              rdiff-backup  --include /usr/local/bin --exclude /usr/local /usr
              /backup

       would backup the /usr/local/bin directory (and its contents),  but  not
       /usr/local/doc.
```

---

