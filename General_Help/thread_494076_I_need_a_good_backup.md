---
title: "I need a good backup"
date: 2007-07-06
forum: General Help
---

### Post by catnappist on 2007-07-06
I tried something simple (my favorite).  It was one line that I typed into the terminal that backed up what was necessary and ignored everything that supposedly wasn't (I don't remember what it was or where I found it).  It was great.  Then ubuntu crashed because I was advised to install nvidia through Restricted Drivers Manager, which was okay because I had a backup.  The backup didn't work at all.

After doing another complete install, I tried to use PartImage on my system rescue CD.  It wouldn't copy a partition or explain why.  I downloaded partimage from their site and couldn't figure out how to compile it even with their instructions.  I tried something else that wanted a server address when all I wanted was an image of my main drive tucked safely onto my catch-everything drive.

All I want to do at this point is backup my /home partition - it isn't big enough and I need to make it bigger.  I can go into gParted (on my system rescue cd) and copy a partition, but I don't know where or how to paste it, or how to recover it when (not if, because this is Linux) necessary.

Any suggestions?

---

### Post by tszanon on 2007-07-06
> **catnappist said:**
> I tried something simple (my favorite).  It was one line that I typed into the terminal that backed up what was necessary and ignored everything that supposedly wasn't (I don't remember what it was or where I found it).  It was great.  Then ubuntu crashed because I was advised to install nvidia through Restricted Drivers Manager, which was okay because I had a backup.  The backup didn't work at all.

After doing another complete install, I tried to use PartImage on my system rescue CD.  It wouldn't copy a partition or explain why.  I downloaded partimage from their site and couldn't figure out how to compile it even with their instructions.  I tried something else that wanted a server address when all I wanted was an image of my main drive tucked safely onto my catch-everything drive.

All I want to do at this point is backup my /home partition - it isn't big enough and I need to make it bigger.  I can go into gParted (on my system rescue cd) and copy a partition, but I don't know where or how to paste it, or how to recover it when (not if, because this is Linux) necessary.

Any suggestions?
I backup my files using tar and 7z. The only problem is that, if I open it using file-roller, the contents of the .tar.7z file is the TAR archive...I should take a look at how to use a pipe between 7z and tar, so I can decompress my files without creating a big tar file in the middle of the process...

Well, If that pair tar + 7z meets your needs, I'll give you the command-line when I get home.

---

### Post by catnappist on 2007-07-06
Take your time, I'm reading up on 7zip, something else I've never heard of.  I appreciate your assistance.:p

---

### Post by catnappist on 2007-07-06
Okay, 7zip was explained quite well, even got good instructions on zipping my /home folder and putting it where I wanted it.  After I screw up the resizing, can I replace everything with the live feisty fawn CD?  Permissions seemed to be a problem on my last effort.

---

### Post by tszanon on 2007-07-06
> **catnappist said:**
> Okay, 7zip was explained quite well, even got good instructions on zipping my /home folder and putting it where I wanted it.  After I screw up the resizing, can I replace everything with the live feisty fawn CD?  Permissions seemed to be a problem on my last effort.
Sorry, I don't think I really understood what you said. If you're asking if you can restore your backup using the live cd, then the anwser is yes, you can.

As I promised, here's how to backup your files using tar and 7z:
```
tar --create --exclude-from=dont.backup.list.txt /home | 7z a -mx=9 -ms=off -t7z -si backup.tar.7z
```
Piece by piece:
**tar --create**: creating new tar archive
**--exclude-from**: list of what you don't want to backup. Each item can be a file or a directory. Put one item per line. If you don't have anything you don't want to backup, just cut off this parameter;
**/home**: directory what you want to backup;
**7z a**: create new compressed archive
**-mx=9**: compression level. Can be 0, 1, 3, 5, 7 or 9. The higher the level, more resources (memory+cpu+time) it will need to compress.
**-ms=off**: solid archiving. Not necessary, because we're already doing it with tar;
**-t7z**: file type 7z. Not necessary, because it's the default.
**-si:** read from standard input (in this case, whatever tar creates).

Once you install 7zip, file-roller will be able to open .7z archives. Then, it'll be easy to extract everything. Maybe you will have to run file-roller with gksu, to ensure you will have write-access to everything, but I'm not sure.

Go on, give it a try before you do the real thing.

---

### Post by brennydoogles on 2007-07-06
A great utility for this is Tarlimit, which will automatically make tar.bz2 files from wherever you specify, and you can set how large you would like the archives to be (meaning you can specify 4.7 GB for DVD's or 700 mb for Cd's) You can download it [HERE.]("http://sourceforge.net/projects/tarlimit") I hope everything works out for you!!

---

### Post by catnappist on 2007-07-06
Hey, thanks tszanon, brennydoogles, I'll try it both ways.  BIG help!:p

---

### Post by catnappist on 2007-07-06
> **tszanon said:**
> Sorry, I don't think I really understood what you said. If you're asking if you can restore your backup using the live cd, then the anwser is yes, you can.

As I promised, here's how to backup your files using tar and 7z:
```
tar --create --exclude-from=dont.backup.list.txt /home | 7z a -mx=9 -ms=off -t7z -si backup.tar.7z
```
Piece by piece:
**tar --create**: creating new tar archive
**--exclude-from**: list of what you don't want to backup. Each item can be a file or a directory. Put one item per line. If you don't have anything you don't want to backup, just cut off this parameter;
**/home**: directory what you want to backup;
**7z a**: create new compressed archive
**-mx=9**: compression level. Can be 0, 1, 3, 5, 7 or 9. The higher the level, more resources (memory+cpu+time) it will need to compress.
**-ms=off**: solid archiving. Not necessary, because we're already doing it with tar;
**-t7z**: file type 7z. Not necessary, because it's the default.
**-si:** read from standard input (in this case, whatever tar creates).

Once you install 7zip, file-roller will be able to open .7z archives. Then, it'll be easy to extract everything. Maybe you will have to run file-roller with gksu, to ensure you will have write-access to everything, but I'm not sure.

Go on, give it a try before you do the real thing.

Well...I tried it and got this:

tar --create --exclude-from=dont.backup.list.txt /home | 7z a -mx=9 -ms=off -t7z -si backup.tar.7z
tar: dont.backup.list.txt: No such file or directory
tar: Error is not recoverable: exiting now

7-Zip 4.43 beta  Copyright (c) 1999-2006 Igor Pavlov  2006-09-15
p7zip Version 4.43 (locale=en_US.UTF-8,Utf16=on,HugeFiles=on,1 CPU)

Updating archive backup.tar.7z

Compressing  [Content]                                                    

Everything is Ok

---

### Post by tszanon on 2007-07-07
> **catnappist said:**
> Well...I tried it and got this:

tar --create --exclude-from=dont.backup.list.txt /home | 7z a -mx=9 -ms=off -t7z -si backup.tar.7z
tar: dont.backup.list.txt: No such file or directory
tar: Error is not recoverable: exiting now

7-Zip 4.43 beta  Copyright (c) 1999-2006 Igor Pavlov  2006-09-15
p7zip Version 4.43 (locale=en_US.UTF-8,Utf16=on,HugeFiles=on,1 CPU)

Updating archive backup.tar.7z

Compressing  [Content]                                                    

Everything is Ok
It seems that:
1. You didn't create a list containing what you don't want to backup, but specified one (--exclude-from=dont.backup.list.txt);
2. You created that list, but tar searched for it in the wrong place.

Solution for (1): Do you have anything you don't want to backup inside /home? Like ~/.Trash, ~/.thumbnails, or anything else? Then, write each of these things in a text file, like this:
```
/home/your.username/.Trash
/home/your.username/.thumbnails
```
and specify the filename in that parameter **--exclude-from=<filename>**. As you can see, I created a list called **dont.backup.list.txt**.

Solution to (2):
Specify the absolute filename (include the path from / where it is), like **--exlude-from=/home/your.username/dont.backup.list.txt**. It surely will solve the problem.

Does the problem persist?

P.S. One thing I forgot to say is that the progress bar of 7zip will keep at 0% until it finishes. Don't worry about it..

---

### Post by catnappist on 2007-07-07
That's what I did (didn't do).  :D  I'll work on that.  Thanks!

---

