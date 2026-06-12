---
title: "In need of backup advice."
date: 2008-04-23
forum: General Help
---

### Post by Serguei_89 on 2008-04-23
Hi,

There are hundreds and hundreds of blogposts and articles about backing up ubuntu. But from what I found most of these ways either don't work(unreliable) or too complicated or are not what I'm looking for

For context:
Gui programs like Sbackup or Timevault simply didn't work for me. Sbackup backed up the files, but when trying to restore, it didn't. Timevault sat in the tray without doing anything.

I used rsync once to backup my files, but when executing the command again, it started copying all the files over again. I thought it was supposed to do incremental backups.

In either case, I need help for the following situations:

1) File-based backup using rsync. I backup to an external harddrive which is not always connected to my laptop. I have no trouble running it manually once a week or so, but I need help getting the command right.
How do I make it backup just the changes? I'm backing up around 60GB of data, so I don't want it to take 3 hours copying every file over again? Also, I don't want it to ask me anything, no prompts. And it should backup every file, skip nothing. How do I setup the command to do this?

2) Image-based backups. It would be nice to have a full Ghost-like image of an entire hard-drive in case of completely disastrous situations. I tried Part-image, but it only does partitions. What program is able to backup entire hard-drive image to a set of DVDs or to external on the ghost-like level of reliability?

I appreciate any advice from you.

Serguei.

---

### Post by Interstellar Overdrive on 2008-04-23
I also played with a number of backup options, and ended up using rsync.

To perform an incremental backup (only files that have changed) I use these arguments:

```
rsync -avzt /home/ClientUser /backup/destination
```

(Files will end up in /back/destination/ClientUser)

The options mean:

-a, --archive 
        Like -r, but reproduce nearly all characteristics of the files and directories being transferred, such as modification times, symbolic links, ownership, and permissions.

-v, --verbose 
        Display the names of files transferred and statistics related to the transfer.

-z (synonym for --compress) 
        Use compression during transmission.

-t, --times 
        Set the timestamps of the destination file to match those of the source file, instead of using the time of transfer (that is, reflecting the existence of a new file on the destination host).

EDIT:
I forgot to say that this is only incremental if you backup to the same location each time. If you backup to a different folder then everything will get copied over

---

### Post by Vadi on 2008-04-23
See if this program ([click]("apt:sbackup")) does it for you. After installing it can be found in system - administration.

---

### Post by upthelum on 2008-04-24
Use tar. Works fine for me. Type man tar for help files.

---

### Post by Serguei_89 on 2008-04-24
I've used the command 
rsync -avzt /home/ClientUser /backup/destination

and right after it finished, I ran it again. It's still taking over an hour to complete. Is this just the time it takes to compare the files and see if there are changes to write? I have around 70GB of data to backup.

Also, it keeps popping messages like:
rsync: chgrp "/media/NEW VOLUME_/File-based Backups/Videos/Movies/TMNT.avi" failed: Operation not permitted (1)

What does that mean? I'm running the command as sudo.

Plus my external hard-drive for some reason is mounted with 'root' as the group and maybe that's the problem. 
I tried running "sudo chgrp myusername /media/external/, but it said operation not permitted. How can I fix that?

---

### Post by rbmorse on 2008-04-24
Take a look at grsync.  It's a GUI front-end for rsync. Easy to use and meets most of your requirements.  You end up with a complete backup of the original fileset...after the first execution, rsync will only copy changes so it's very fast.  

It's not really an incremental backup per se. You can't go back and pull an intermediate version of a file. What's on the backup store will be identical to what was on the source partition at the time rsync was run.

---

### Post by Ziggy72 on 2008-04-25
I like sbackup - simple to setup and use.

---

### Post by natrixgli on 2008-04-25
I use sbackup and timevault on my laptop with good results. I did have to play around with timevault a bit, and I still can't get the nautilus properties dialogue to show anything meaningful, but selecting the snapshot browser from the tray icon works swell.

At work I use Bacula, with Webmin to manage it. It seems complicated, but it's really not that much. The only thing I don't like is having a separate GUI to manage it, and restore files.

I use rsync, then archive to tape with Bacula.

-n8

---

### Post by Interstellar Overdrive on 2008-04-25
> **Serguei_89 said:**
> I've used the command 
rsync -avzt /home/ClientUser /backup/destination

and right after it finished, I ran it again. It's still taking over an hour to complete. Is this just the time it takes to compare the files and see if there are changes to write? I have around 70GB of data to backup.


I'd try backing up a test directory with a smaller amount of data to another directory in the same partition. That way you can test to see if the command options you're using are the problem, or if it's something to do with the external drive.

I use that command (without the -v option) in a cron which copies my home dir to a remote server It's definitely not copying everything over every time, and so far it's worked like clockwork. Obviously I don't know very much about all this, just reporting what's worked for me.

This link [[Click Here]]("http://commandline.org.uk/linux/backup-to-external-drive-2008-02-15-22-50.html") is what I used when setting up my backup process, it might be useful to you.

---

### Post by Serguei_89 on 2008-04-25
Could it be the problem with external hard-drive?

Ubuntu properties says it's filesystem is "msdos", I remember formatting it in windows.

I think the underlying problem is the "chgrp operation not permitted" messages rsync keeps shooting at me. Even when I try manually as sudo, I cannot change the group permissions on the external harddrive. What's weird is that for some files it pops this up and for some it doesn't. 

Any idea?

---

