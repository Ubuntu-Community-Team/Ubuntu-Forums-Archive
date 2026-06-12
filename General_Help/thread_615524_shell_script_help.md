---
title: "shell script help"
date: 2007-11-17
forum: General Help
---

### Post by matt91 on 2007-11-17
i am trying to make a backup script i can schedule with cron. so far in the script i am trying to make it make a directory for backups to go in for that date however it always adds ?? onto the end of the dir name.

this is the script so far:
> #!/bin/sh
DATE="backup_`date +%Y%m%d`"
cd /backup
mkdir $DATE

which makes the directory backup_20071117??

I assume i am doing this wrong, does anybody know any good tutorials/howtos?

Matt

---

### Post by geirha on 2007-11-17
> **matt91 said:**
> which makes the directory backup_20071117??

I assume i am doing this wrong, does anybody know any good tutorials/howtos?

Matt

You're not doing anything wrong, it really should create /backup/backup_20071117.

What filesystem is /backup on? ext3? fat32?

If you add ```
echo $DATE
``` at the end of the script, does it output with the "??" as well?

---

### Post by matt91 on 2007-11-17
it is ext3, with the echo on this is what happens:
> root@server:/backup# sh ./test.sh
: No such file or directorykup
backup_20071117
root@server:/backup# ls
backup_20071117??  test.sh

if i then run the script again after this i get:
> root@server:/backup# sh ./test.sh
: No such file or directorykup
mkdir: cannot create directory `backup_20071117\r\r': File exists
backup_20071117


---

### Post by geirha on 2007-11-17
> **matt91 said:**
> 
```
mkdir: cannot create directory `backup_20071117\r\r': File exists
```


hm, how did those \r's get in there. Could you post the output of this? ```
cat -v test.sh
```
And please, put the output in code-tags rather than quote-tags.

If it shows some ^M's in there, the following command should remove them.
```
sed -i 's/\r//g' test.sh
```

---

### Post by matt91 on 2007-11-17
Thanks for that, there were ^M's at the end of the lines, works fine now :) I think it was because i was editing from my M$ box.

---

### Post by toupeiro on 2007-11-17
An important thing to note, sed will only remove the characters, but will not affect the encoding of the file, which is what was ultimately changed.  Depending on your situation, this can be a showstopper.  Those ^M's mean something.  They are carriage return remarks.  Every UNIX file you create gets them when you hit enter, the difference is that you don't see them because of the way the file is encoded.  When you sed the file in this manner, you are essentially removing all carriage returns from the file.  This may not affect the script you are writing right now if the shell interpretor will understand EOL (end of line) as a carriage return, (most do) but it is not a good practice when you start to write/modify different kinds of files, or scripts that are interpreted by applications, because applications won't always interpret the same way a shell will.

On older solaris systems, there was a command called dos2unix which would take care of all the encoding changes that Microsoft OSes put UNIX files through to edit them. In addition, this command also takes care of the carriage return characters properly rather than removing them. in Ubuntu, you can get this command by typing:

```
sudo apt-get install tofrodos
```

It appears the application has gone through some renaming, but the packages still makes a symlink in /usr/bin called dos2unix

the format would be:

```
dos2unix <switches> <input file> <output file>
```

by default, you can specify the same filename for input and output if you wish.

In the end, the result is the same, the ^M's are visibly removed from the file, but the format is modified properly with the dos2unix command.  Use whichever you wish, but if you start encountering a problem, keep this command in your arsenal should you experience any weirdness. ;-)

you can also go.  unix2dos :)

---

### Post by matt91 on 2007-11-17
Thanks for that, i will make sure i do that in the future.

Maybe this should be a new thread, but anyway. How could i rotate backups for example so it only kept the last 10 backups.

For example, In the backup directory their will be directories with the format 'backup_yyyymmdd', so it will delete the oldest backups if their are more than 10 according to their date.

---

### Post by toupeiro on 2007-11-17
If you want to continue scripting a solution, all power to you!  I recommend downloading a utility called sbackup.  You will be pleasantly surprised. :)  It has a pretty advanced scheduler for a home backup tool, and its naming structure is date oriented, redirect-able, and logical to follow.  You can also have the tool scp or sftp data to another machine if you would like.  

It also gives you a nice catalog to browse.


I would try something like this:
```
find /path/to/backup/archive -type d -mtime +10 -print -exec rm -rf {} \;
```

as is, this should blow away directories in a given path that are older than ten days.  If you are using tar files.  just change the -type to an f. and change -rf to -f

if you want to try the utility:

```
sudo apt-get install sbackup
```

---

