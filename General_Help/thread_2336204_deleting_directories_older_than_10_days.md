---
title: "deleting directories older than 10 days"
date: 2016-09-05
forum: General Help
---

### Post by Old Jimma on 2016-09-05
Hi Community: :P

I back up my entire home directory every week to a very large hard disk. :neutral:

Letting "joe" be the name of my home directory, when I do the backup, I name the directory "joe - 16-09-05" to denote that the directory on my very large hard disk was the one backed up on September 5, 2016.

That very large hard disk probably can store only 3 copies of the home directory "joe" backed up on 3 weeks. :guitar:

Before copying my home directory to the very large hard disk, I want to delete the oldest copy of the home directory on that hard disk.

Will the following command do this? :-k

> 
find /path/to/home/dir/* -type d -ctime +18 -exec rm -rf {} \;

 :)
I realize that I could do all of this by hand, but I want to know if that command will work as I want it to if I put it in a shell script and run the script in a cron  job. :)

Thanks,
Old Jimma from the Old Country

---

### Post by coldraven on 2016-09-05
I don't know the answer to your question but I think you need to research "rsync". AFAIK this will avoid duplicates.

---

### Post by Habitual on 2016-09-06
[Simple, Secure Backups for Linux with rsync]("http://rsync.net/resources/howto/rsync.html")

---

### Post by sudodus on 2016-09-06
1. Please use CODE tags instead of QUOTE tags for command lines. It makes it easier to read.

2. No, I'm afraid your command line will remove old sub-directories in the file trees, that you want to keep. Instead, I suggest that you remove the old backup [file tree] manually, to have full control until you develop and test another command line. List the directory, where you store the backups, and removed the oldest one when your sure there is a newer version.

3. I think the following command line is safer to list the directories (but not subdirectories below that level)

```
for i in *;do if test -d "$i";then echo "$i";fi;done
```

4. I use rsync, which is a very good tool. It works incrementally as *coldraven* wrote. When you want a fresh start (and get rid of files files in the backup, that you deleted from the source and you no longer want), just back up to a new directory. I often use

```
sudo rsync -Havn /path-to-source/ /path-to-target  # dry run
sudo rsync -Hav /path-to-source/ /path-to-target  # real copying
```

Notice the slash after 'path-to-source'. It is important. See ```
man rsync
```

```
       A trailing slash on the source changes this behavior to avoid creating an  addi&#8208;
       tional  directory  level at the destination.  You can think of a trailing / on a
       source as meaning "copy the contents of this directory" as opposed to "copy  the
       directory by name", but in both cases the attributes of the containing directory
       are transferred to the containing directory on the destination.  In other words,
       each of the following commands copies the files in the same way, including their
       setting of the attributes of /dest/foo:

              rsync -av /src/foo /dest
              rsync -av /src/foo/ /dest/foo
```

You can 'dry run' rsync backwards and get a list of files in the backup, that you have deleted in the source.

```
sudo rsync -Havn /path-to-target/ /path-to-source
```

It is very important to get everything correct. So test with small directory trees, make shellscript files, edit them until you are happy, and then start using them to backup your home directory.

---

