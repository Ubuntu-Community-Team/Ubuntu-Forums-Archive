---
title: "making custom backup script - how to exclude a file?"
date: 2006-10-30
forum: General Help
---

### Post by sup on 2006-10-30
Hello, I would like to back-up my home directory (I do not need to back-up my system, that I can reinstall in less than an hour and with a list of installed packages, with back-uped home I can have fully-operational system fro mscratch in less than three hours). However, I do not need to backup a folder $HOME/music, since everything stored in there is already on my portable hardisk mp3 player. 

I am struglling with it a little - how can I exclude a file from being copied?

My idea was something very simple, i.e.
```
#!/bin/bash
cp -pr $HOME /path/to/external/harddrive/backup
```
 but how do I exclude the files?

I tried sbackup as graphical tool, but it runs only as a root and it is not very convenient since I want to backup diles that are solely in my ownership.

---

### Post by Jussi Kukkonen on 2006-10-30
Use a real backup system -- it'll pay off. I suggest setting up rsync, it's easy and matches the requirements you mentioned.

EDIT:whoops, for some reason I imagined you were copying to another machine. Sorry, rsync might not be applicable. The general advice stands -- there are quite a lot of little details that can go wrong in backing up if you do-it-yourself.

---

### Post by sup on 2006-10-30
well, and is there a simple gui tool that will allow me to do what I want? I do not need that fault-proof solution, I od not mind using a month old back-up most of the time, I save real important stuff twice nevertheless...

---

### Post by Jussi Kukkonen on 2006-10-30
Now that I think of it rsync is usable (even the man pages say * You can also use rsync  in  local-only  mode,  where  both  the source  and  destination  don’t have a ‘:’ in the name. In this case it behaves like an improved copy command.*). It's not a GUI though
* You can exclude files like *tar* does (using a command line flag) or using CVS ignore.  
* Copies links,devices, permissions
* root not required

Then again tar probably fits that description too :)

---

### Post by dannyboy79 on 2006-10-30
i use sbackup 1.0, so what if it runs as root? I use it to back up to a local folder which has a smb share mounted to it. sbackup is so easy to configure. The next thing I am trying to get to work is to be able to backup to a ftp server using sbackup but i haven't been able to get to work even though when I test it using [ftp://username:password@ftpserver/share](ftp://username:password@ftpserver/share) it gives me a green light meaning the connection os good but when I run it it doesn't do anything? Anyway, could you explain why sbackup running as root is bad?

---

### Post by podunk on 2006-10-30
If it's only a few directories I'd just use Nautilus to drag and drop onto the external drive.

---

### Post by garretwp on 2006-10-30
I have made a perl script to my needs that backs up my home directory. I have restored from it many of times in the past. I.e. doing a clean install of Ubuntu on every release. I use the tar command to tar up the whole folder and I have it setup to do a full backup once a week. Then the rest of the days of that week, I have it do a partial backup. Here is what the tar command would look like and to exclude a file or files.

tar -cvzf --exclude-from="file name" homebackup.tar.gz "home directory"

c = create v = verbose z = gzip f = file

With the --exclude-from=  put in the path to a text file with the list of all the files you want to exclude. i.e. /home/username/music
This will exclude the folder music from being tar'ed up.

- Garrett

---

### Post by dannyboy79 on 2006-10-31
how "EXACTLY" should the folder's being written within this file? can you please post some examples. unless of course you're already saying that i could just simply make a blank file named whatever and then inside the file would be:

/home/username/music


and that's all your saying?

---

### Post by garretwp on 2006-10-31
I have a file called exclude.lst. With in that file I have a list of all the folders and files I do not want to. for example:

/home/garrett/storage
/home/garrett/drive-backup
/home/garrett/.Trash

storage and drive-backup are hard drives mounted in my home directory. I do not want them to be backed up as it will create a large file and they are already backed up on seperate drives. When you use the --exclude-from= option, you put in the path to where that exclude file is located.

--exclude-from=/storage/backups/exclude.lst

- Garrett

---

### Post by dannyboy79 on 2006-11-01
> **garretwp said:**
> I have a file called exclude.lst. With in that file I have a list of all the folders and files I do not want to. for example:

/home/garrett/storage
/home/garrett/drive-backup
/home/garrett/.Trash

storage and drive-backup are hard drives mounted in my home directory. I do not want them to be backed up as it will create a large file and they are already backed up on seperate drives. When you use the --exclude-from= option, you put in the path to where that exclude file is located.

--exclude-from=/storage/backups/exclude.lst

- Garrett

how do you get the .lst on the end of a file? if I were to just do gedit exclude would that be ok? i don't understand file extensions in linux just yet? for example, I use a username.map file within my smb.conf to map network usernames to my server usernames but to edit it I simply use gedit so what's the whole point of having the .map on the end? or in this case the .lst? also, like the sources.list, i noticed your file extension only is .lst were as sources file is .list. what's this all about? Can you answer these questions for me?

---

### Post by garretwp on 2006-11-01
You do not have to have any extension at the end. It just makes it easier for you to know that it is a list. You can name the file anything you want. An easy way of making a file would be to use the touch command. i.e. touch exclude.lst Then open it up in gedit and edit away.

- Garrett

---

### Post by sup on 2006-11-01
> **dannyboy79 said:**
>  Anyway, could you explain why sbackup running as root is bad?
Because it then creates file that is owned by root, it is inconvinient to move it around etc.
> If it's only a few directories I'd just use Nautilus to drag and drop onto the external drive.
It's my entire /home directory, so it is not just a few directories, and I want it to be automatic so that I do not have to think about it.

Thanks others for suggesting tar, it seems to work fine and I have already back-uped my files. 

However, If I wanted to run the script about once a week and would like to keep at most two simultaneous back-ups, is there an easy way to got it working considering I want to back-up on an external hard drive that is not always plugged in?

I intended to use anacron for it, but I struggle with coping with possibility of unpluged harddrive when the back-up should take place...:-/

---

### Post by mistab1034 on 2006-11-01
> **dannyboy79 said:**
> i don't understand file extensions in linux just yet? 

File extensions don't matter as much in Linux as they do in Windows. Most applications use meta data in the file to select the propper application to open it with and ignore file extension. So a file you create in Gedit could have any file extension and still be able to be edited in Gedit. For example you can make a file called 'mytext.mp3' and Linux would still know it's a text file.
```
user@ubuntu: gedit mytext.mp3 &
user@ubuntu: file mytext.mp3
mytext.mp3: ASCII text
```

---

### Post by dannyboy79 on 2006-11-03
> **sup said:**
> Because it then creates file that is owned by root, it is inconvinient to move it around etc.

so then you chown it, no big deal!

---

### Post by sup on 2006-11-03
> **dannyboy79 said:**
> so then you chown it, no big deal!
Yeah, I might just do it - the other thing was that sBackup for some reason filled my root partition to the last byte, but I might give it one more try since I do not know enough about bash and else to make a script that would do just what I want...

---

### Post by sup on 2006-11-03
edit:duplicate

---

### Post by dannyboy79 on 2006-11-03
> **sup said:**
> Yeah, I might just do it - the other thing was that sBackup for some reason filled my root partition to the last byte, but I might give it one more try since I do not know enough about bash and else to make a script that would do just what I want...

well that's probably because the default save location is /var/backup which is obviously the same parition as your root and entire system unless of course you mounted that to a different parition but most likely not. what i do, is backup my laptop to a folder that has a smb share mounted to it.

---

### Post by sup on 2006-11-03
no, I choose my external USB drive as save location - and it was /tmp that was filled.

---

### Post by sup on 2006-11-05
So I am using Sbackup right now and it seems to work. I have to objections though - it uses compression by default and it runs as root. Both were adressed to the developer and he seems willing to do something aboutit, maybe.

But anyway, it works nicely, and that full temp was due to Krusader, it created huge file when I tried to browse the backup without uncompressing it.

---

