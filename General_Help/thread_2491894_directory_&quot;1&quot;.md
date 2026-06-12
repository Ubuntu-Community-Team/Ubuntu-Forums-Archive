---
title: "directory &quot;1&quot; ?"
date: 2023-10-25
forum: General Help
---

### Post by ulrichmuc2 on 2023-10-25
In my home directory i see a subdirectory "1" with many subdirectories named "102", "103", ...

What is the pupose of these directories? May I delete them?

---

### Post by guiverc on 2023-10-25
You've provided few clues as to what Ubuntu product & release, but I'm a desktop user, and cannot think of any system that installed & created a directory named "1" with sub-directories under it named "102", "103" etc.

You may need to provide extra details; though if it was me, I'd explore some file *metadata* to explore when they were created, which may provide a clue.

eg.  On my own system, I can 

```

guiverc@d7050-next:~/uwn/issues/810$   cat /var/log/installer/media-info 
Xubuntu 23.10 "Mantic Minotaur" - Daily amd64 (20230829)guiverc@d7050-next:~/uwn/issues/810$   stat /var/log/installer/media-info 
  File: /var/log/installer/media-info
  Size: 56              Blocks: 8          IO Block: 4096   regular file
Device: 8,6     Inode: 2622362     Links: 1
Access: (0644/-rw-r--r--)  Uid: (    0/    root)   Gid: (    0/    root)
Access: 2023-10-25 17:54:37.595317567 +1100
Modify: 2023-08-29 13:49:41.298481128 +1000
Change: 2023-08-29 13:49:41.298481128 +1000
 Birth: 2023-08-29 13:49:41.298481128 +1000
guiverc@d7050-next:~/uwn/issues/810$

```

the first `cat /var/log/installer/media-info` command gave me details of the installation media used to install my current box, it was a Xubuntu 23.10 daily of date 20230829 which was shown by the contents of the file (ie. what I asked it to `cat`)

Next I view *metadata* of that file using `stat /var/log/installer/media-info` where

```

 Birth: 2023-08-29 13:49:41.298481128 +1000

```
I bet that is when I installed the system; whilst I don't recall exactly - I'm pretty sure.

Thus in your case I'd likely

```

stat ~/1

```

to see what your file-systems can tell you about the file; and I'd hope that gives you more details.  My belief is that will not be when you created/installed your system, but some time after that.

---

### Post by ulrichmuc2 on 2023-10-25
The system is ubuntu mate  22.04.3 LTS. The directories ~1/*/  contain 64 files named manifest.xml and 60 files named *.note, e.g. c5c50a5b-4fd2-4bd2-8e81-2b267b370b5f.note.
Looking into the *.note files, they seem to have been created by tomboy.
However, the tomboy man-page doesn't mention any files and the link given in the man-page is broken. I'll move ~/1 to ~/one and check whether tomboy still works.

---

### Post by TheFu on 2023-10-25
~1 is for the username '1".

Do you mean ~/1?  That would be a sub-directory $HOME/1.

In general, assuming you have good backups, then deleting it wouldn't matter, right?  Delete it and see if something breaks.  If something does, put it back.  As a guess, I'd think you had written a script or copy/pasted some bash commands without really understanding them.  Every once in a while, I'll accidentally create a file, 1, for that reason because I messed up a redirection in a shell script.  Sometimes the file names are 2.  1 = standard out (stdout).  2 = standard error (stderr). These are default file descriptors that every process has.  It is common for 1 process to output to stdout and use that as input to the next process as stdin.

Don't forget you can use the the 'file' command to get information about MIME-types.  
```
$ file ~/1
```
if it is a directory, it will say that. If it is a shell script or PDF file or specific type of image or video or pure data, it will return that too.s

```
$ file USHolidays.ics
USHolidays.ics: vCalendar calendar file
$ file USA.zip
USA.zip: Zip archive data, at least v2.0 to extract

```
**file** knows about hundreds of different types of files, but not all:
```
$ file selenium.side
selenium.side: ASCII text

```

I see you've traced it back to **tomboy**.  Perhaps there's an environment variable that should have been set or a config file that wasn't modified to setup where the tomboy data files should be placed? 

I use vimwiki.  Because I'm lazy, I wriote a little script to ensure I could access my wiki from anywhere, but not lose where I was.
$ more ~/bin/wiki
```
SAVE=$(pwd)
cd  ~/vimwiki
vim ~/vimwiki/index.wiki
cd "$SAVE"

```

It saves my current directory, changes to the wiki location, runs vim taking me into the wiki index. When I'm done, it returns me to the prior directory.  I use that wiki about 10 times every day to look up things. It is accessible from anywhere in the world that I have internet and ssh. No GUI needed, which I consider a requirement, but I could see where other people might require a GUI as a base thing in their note taking.  My first requirement was ASCII text as the default format, with some lite formatting (markdown).

---

### Post by guiverc on 2023-10-25
> **ulrichmuc2 said:**
> The system is ubuntu mate  22.04.3 LTS. The directories ~1/*/  contain 64 files named manifest.xml and 60 files named *.note, e.g. c5c50a5b-4fd2-4bd2-8e81-2b267b370b5f.note.

What file-system are you using for /home?  

That detail reminds me of a FAT file-system, which cannot store all POSIX compliant data & thus is a little different; some also are restricted to 8 characters thus use *tricks* to allow longer filenames; if that partition is shared with a windows system (*particularly if it's a FAT fs*) I'd be careful making any changes.  This however will not apply to any POSIX complaint file-system offered at install with a Ubuntu-MATE system as far as I recall (*I don't recall NTFS being offered; if it is that will be an exception as its not POSIX compliant*)

---

### Post by ulrichmuc2 on 2023-10-26
*What file-system are you using for /home?*

The file-system used is ext4.

Moving ~/1 to ~/one does&#8217;t hurt tomboy and tomboy dos not create a new ~/1 directory

I now found: tomboy uses ~/.config/tomboy/*

---

### Post by MAFoElffen on 2023-10-26
Just curious... On 
```

ls -lad ~/1

```
Does it say you are the owner of it? There is no way in Linux to track "who" created it, but that is usually the owner.I'm just wondering if it was a service account.

---

### Post by ulrichmuc2 on 2023-10-26
> ls -lad ~/1  gives

drwxrwxrwx 4 privat privat 4096 Oct 26 10:03 /home/privat/1, where "privat" is my user-name.

Since removing ~/1 yesterday, it reapeared today, containing 1/166/manifest.xml and 1/167/manifest.xml

Very funny!

---

### Post by TheFu on 2023-10-26
Are you using Java programs for anything?

---

### Post by ulrichmuc2 on 2023-10-26
[COLOR=#000000]> Are you using Java programs for anything?

[/COLOR] not that I know

---

### Post by MAFoElffen on 2023-10-26
Okay. You  have my curiosity going. (It's like a book that you can't put down until you find out what is going to happen next...)

I want to see what is there (LOL)
```

grep ~/1/167/manifest.xml

```

---

