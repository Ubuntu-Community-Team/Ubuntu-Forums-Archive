---
title: "How do I create information Backups for Kubuntu?"
date: 2007-01-13
forum: General Help
---

### Post by wersdaluv on 2007-01-13
In windows, they have that Windows Live OneCare Data Backup and restore. I'm wondering is there is something like that for Linux.

I'm using Kubuntu Edgy Eft and the case is that, I want to create a new partition. Not being very familiar with doing that and just for a sense of security, I want to backup my files.

The files I want to backup are my Music, my browser settings, me desktop environment settings, may information in KDE's Kontact, etc.

As for the Music, I think I will have to burn them to CDs but for the others, how can I make a backup for them? Is there something like Windows Live OneCare Data Backup and restore?

---

### Post by john_spiral on 2007-01-13
I might be wrong but 'll have a go

get a terminal up:

type:

dd if=/dev/1st_disc_and_partition of=/mnt/some_directory/image.iso

e.g

dd if=/dev/hda1 of=/mnt/backups/image.iso

caio

Johne

---

### Post by peterLinux on 2007-01-13
There are several backup/restore programs
In your case I would not bother to much.
You have to store those files on an other computer or medium anyway.
What does it help to have a backup file on a harddisk that is not accessible?

I would make a tar.bz file(s) and copy that file onto a CD/DVD (s)

Look in the man pages for more info: man tar

Other option is to us K3B and drag everything you want to backup onto a CD/DVD.

2 cents


Peter

---

### Post by wersdaluv on 2007-01-13
> **john_spiral said:**
> I might be wrong but 'll have a go

get a terminal up:

type:

dd if=/dev/1st_disc_and_partition of=/mnt/some_directory/image.iso

e.g

dd if=/dev/hda1 of=/mnt/backups/image.iso

caio

Johne

I tried the code and what happened was this:

```
dd: opening `/dev/1st_disc_and_partition': No such file or directory
allan@AllanCaeg-Laptop:~$
```

How do I edit the code in such a way that will work for me?

What does this code do? Does it make an iso image for all my data?

---

### Post by wersdaluv on 2007-01-13
> **peterLinux said:**
> There are several backup/restore programs
In your case I would not bother to much.
You have to store those files on an other computer or medium anyway.
What does it help to have a backup file on a harddisk that is not accessible?

I would make a tar.bz file(s) and copy that file onto a CD/DVD (s)

Look in the man pages for more info: man tar

Other option is to us K3B and drag everything you want to backup onto a CD/DVD.

2 cents


Peter

I'm sorry but I'm new with this. What do you mean by man pages and man tar?

---

### Post by peterLinux on 2007-01-13
Open up a command line and type

man tar

It is the help file for tar.

That having said if you are that new... welcome to the Linux community
but stay away from the command line and tar stuff solution.

As a Kubuntu user fire up K3B
and burn your important files on CD/DVD.

In one of the previous post I saw
"1st_disc_and_partition"
needed to be replaced by a name for a disk and partition
usually that is hda1 or hda2 or...
That explains your 'error'....

Don't try the dd cmd, use K3B for now.

FYI It took me 1 yr (way back in 1998 to lear Linux
give yourself the time, get familiar with the desktop first
than start experimenting with the command line.

Peter

---

### Post by wersdaluv on 2007-01-13
> **peterLinux said:**
> Open up a command line and type

man tar

It is the help file for tar.

That having said if you are that new... welcome to the Linux community
but stay away from the command line and tar stuff solution.

As a Kubuntu user fire up K3B
and burn your important files on CD/DVD.

In one of the previous post I saw
"1st_disc_and_partition"
needed to be replaced by a name for a disk and partition
usually that is hda1 or hda2 or...
That explains your 'error'....

Don't try the dd cmd, use K3B for now.

FYI It took me 1 yr (way back in 1998 to lear Linux
give yourself the time, get familiar with the desktop first
than start experimenting with the command line.

Peter

Yeah. I guess you're right. I'm just lucky Linux is getting easier nowadays. Thanks!

By the way, do you know how I can backup contacts, appointments, to-dos, basKet notepads, etc. from KDE's Kontact? Those things are the most important information for me but I don't know how to backup them

---

### Post by peterLinux on 2007-01-14
You have to figure out where the information sits on your harddisk, before you can back it up.

Sometimes those things (like bookmarks for webbrowsers)
sit under a hidden directory or file.

Go to a command prompt (terminal) and type ls-la
it shows you all the files in your home directory
including the hidden ones.

If you backup /home/*your login name here*
including the hidden files chances are big you have ALL the information you need

Also realize that you need to know what to do in case the system crashes...
How and what do you restore from the backup...

Peter

---

