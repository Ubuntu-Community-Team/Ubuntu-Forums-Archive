---
title: "tar files in a directory which were updated in last 2 hours"
date: 2008-02-08
forum: General Help
---

### Post by PhatBob55 on 2008-02-08
Hi foks

I am doing some web development (very basic stuff) but I wanted to have a tar command that I can use, or maybe even cron, that will tar any files that have been created or modified in the last x timeframe. i.e. last 2 hours, or, changed today. 

lets say directory is /var/www/test

and I want to wirte the backup to /home/bob/backup.tar

Cheers

---

### Post by drs305 on 2008-02-08
The commands you should check out include "find" and  "xargs".

Look at the man pages for find, especially the tests section. The options you might be interested in include the -mtime, -daystart, -mmin to name a few. The swtiches are where the power is - you can set it for minutes, hours (via minutes), today (-daystart), or days (-mtime). You can play with lots of options/switches to get only the files you are interested in backing up.

A hint when you are looking at a large man page is to run the command below and then read it in a text editor for ease of navigation or search. To me it's easier than trying to find the man page stored on the drive. To do this with the 'find' page, run:
```
man find  > ~/Desktop/find.txt
```

Here are some commands that would save files changed within the past 60 minutes into home/bob/backup.tar. 

The 'find' command you want is:
```
find /var/www/test -type f -mmin -60 
```
which will output the names of the changed files.

The command for finding and making a tar file would be something like this:
```
find /var/www -type f -mmin -60 | xargs tar -rf /home/bob/backup.tar
```

Note the way this command is written it will maintain multiple copies of the same file if the command is run multiple times within the time frame specified (60). It also retains the folder structure of the directories, so when you open the tar you have to drill through subdirectories to find the files you are interested in. I'm not partial to this method but switches added to the tar command can allow you to save these files in a variety of ways.

Suggestions for improvements welcome ;-)

---

