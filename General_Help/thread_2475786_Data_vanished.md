---
title: "Data vanished"
date: 2022-06-08
forum: General Help
---

### Post by UBUminJ on 2022-06-08
I had a large number of subdirectories which I wanted to upload to my online storage.
So I grouped them into a smaller number of subdirectories
examples: 0-B, C, D, ...

When I wanted to start uploading, I realized that the 0-B subdirectory has vanished.
What happened? How do I get the data back?

Thank you.

Ubuntu 20.04

---

### Post by The Cog on 2022-06-08
If you're lucky, you accidentally dragged and dropped it into another directory. "find -name 0-B" should find it if that's what happened. Failing that, search for something that would have been inside the 0-B directory. If the directory really disappeared, I don't know why that might be, or what you can do other than restore from your backups.

---

### Post by UBUminJ on 2022-06-08
No, find doesn't find it. 
If nobody has an idea, it means that I have to look through 100 CDs/DVDs. :(

---

### Post by TheFu on 2022-06-08
> **UBUminJ said:**
> No, find doesn't find it. 
If nobody has an idea, it means that I have to look through 100 CDs/DVDs. :(

You aren't the first person to misplace files.  It is like searching for my eyeglasses that I've left somewhere.  It on s trip, they are probably in some store we stopped at, on a shelf.  At home, they are probably on my nose or head (tilted up).  From the description of the issue, nobody else can really help. We don't know how you use the computer, so we can't really guess what might have happened.  Do you even use the mouse for stuff like this?  I don't.

To move directories, I'd use the mv command if on the same partition and the rsync command to a different partition or over the network.  I suspect you work different, so any ideas I have to see exactly where the files were moved/copied isn't helpful.  By using the shell, a history of the exact command used is stored, so I can ask to see that command using 'history'.  The mouse/GUI way doesn't store a command history. 

Did **find** locate anything?  Perhaps you are using it wrong?  If you post the exact command and the PWD (which should be in the shell prompt), someone might have some other guesses.  Probably not, but who knows?

---

### Post by dragonfly41 on 2022-06-08
I have at times misplaced folders/files.

There are different workflows to follow to recover.

You can start by sorting your home folders into date order last used.
My personal preference is Krusader file manager but you can use another GUI such as Nautilus or Thunar.
Or master commands which sort by date.

This narrows down your search list to *when* the loss occurred.

Now you can search each folder in order that they were last used.

You can search for name of a folder/file.

Or you can search for a text snippet, word or phrase *inside a lost file*.

For the latter I use ripgrep-all.

[https://github.com/phiresky/ripgrep-all](https://github.com/phiresky/ripgrep-all)

Another useful tool is SearchMonkey.

---

### Post by HermanAB on 2022-06-08
Hmm, I think the search syntax is not good.

Try this:
$ find ~ -name 0*

---

### Post by UBUminJ on 2022-06-10
While the problem is not SOLVED, the data are back. After the 10th or so start, they were suddenly back.
It might have to do with Ubuntu 20.04 not running stable on my old PC (16 years now).

I will now switch to a "new" PC, 6 years old.
:-)
(As soon as the browsers run on that new system.)

---

### Post by TheFu on 2022-06-10
> **UBUminJ said:**
> While the problem is not SOLVED, the data are back. After the 10th or so start, they were suddenly back.
It might have to do with Ubuntu 20.04 not running stable on my old PC (16 years now).

I will now switch to a "new" PC, 6 years old.
:-)
(As soon as the browsers run on that new system.)

This is scary.  Data doesn't disappear and reappear.  There's some issue and your data is massively at risk.  I'd run **fsck** on the file system AND check the disk **SMART data** for leads into what might be happening.  Also, I'd backup all data constantly, because it could be gone forever at any point based on your report.

---

### Post by UBUminJ on 2022-06-10
Scary is the best word to describe the situation.
I am always in the process of backing up all data. New data arriving on the PC are copied immediately into my online storage.

But I was in the process of copying all my old (DVD-R/CD-R)W into online storage too.
First were the topics like photos, music, ...
Then should have come the rest, copied from a number of CDs into one directory. When I divided the huge directory into a number small, fate struck and the next day a part of it had vanished. 

Anyway, the data are back, the are copied and everything is fine.
Thanks to everyone who responded to my question.

---

### Post by TheFu on 2022-06-10
I wouldn't put all those files into a single directory.  Whenever there is more than about 100 files in a directory, the possibility of data loss seems to increase exponentially regardless of file system or OS.    I keep my online CD/DVDs in separate directories and let the OS keep track of the locations using locate, recoll and some very specific scripts that keep specific files in an easy to grep text file for blazingly fast lookups.

Eventually, I stopped using optical media to avoid hassles and wasted time and just bought another HDD to hold the backup data. I added 10% par2 parity files so any data corruption could be known and small amounts could be fixed.  This is how RAR files work except that it keeps the parity files separate from the data files.  Because of the way that media center software works, I keep each different content type organized in the way that every media center seems to prefer.

Movies/Title-YYYY/all the files
TV/Series-Title/S1/Episode numbers
Photos/yyyy/mm-event/
Music/genre/Artist/Album/Tracks

Anyway, you get the idea.  When multiple HDDs are needed, the media center software will logically merge different drive mounts into a single view, so there's no need to use odd file-system merging tools like mergefs/unionfs to trick the libraries into thinking there's only 1 TV directory on 1 disk.  The software is smart enough to handle that - Kodi, Plex, Jellyfin, MiniDLNA, etc ... all do this easily.

But if data disappeared and you don't know why, definitely run fsck and check the SMART stats for the device.  There are posts in these forums about doing both of those things.  Smart data really should be checked weekly with long tests run monthly. Keep a few months of SMART test results, so differences over time can be noticed.  And be certain to use the raw data values, not the percentage values. The % values are nearly worthless most of the time.  If there is more than 10 relocated sectors, it is time for new storage and that failing drive needs to be repurposed as a scratch disk or for sneakernet.  Don't use it for primary or backup data storage.

---

