---
title: "What's a inode?"
date: 2007-05-03
forum: General Help
---

### Post by misfito on 2007-05-03
Well I allready post a problem that I have and I have not found the solution yet...

[http://ubuntuforums.org/showthread.php?t=430281](http://ubuntuforums.org/showthread.php?t=430281)

> /dev/sda1 contains a file system with errors, check forced.
/dev/sda1:
Inodes that were part of corrupted orphan linked list found

*WHAT'S A INODE?

> /dev/sada1: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
 (i.e., without -a or -p options)
 
*What does fsck do?

Does my problem has a solution???:confused:

---

### Post by vav on 2007-05-03
fsck checks the filesystem for errors (something like scandisk in windows). Do 'man fsck' at a terminal window to find out more about the -a etc options. Usually it just means that the system tried to run fsck on its own, using some default options, and that didnt work. So it wants you to run it using some other options.

inodes are part of unix/linux's virtual file system structure. They're links to different objects in the file system.
[http://en.wikipedia.org/wiki/Inode](http://en.wikipedia.org/wiki/Inode)
So any inconsistency in the file system (a misrepresented part of a file, for example) will show up as an inconsistency in the inodes. That's what fsck checks for anyway.

---

### Post by hal8000 on 2007-05-03
From Wikipedia:

When a file system is created, data structures that contain information about files are created. Each file has an inode and is identified by an inode number (often "i-number") in the file system where it resides. Inodes store information on files such as user and group ownership, access mode (read, write, execute permissions) and type of file. There is a fixed number of inodes, which indicates the maximum number of files each filesystem can hold.

A file's inode number can be found using the ls -i command, while the ls -l command will retrieve inode information.

You can also find inode using the linux stat command, and if youve come from a windows background, you can think of inodes as similar to the file allocation tables in windows.

Back to your problem, your file system has corruption, maybe it was not cleanly unmounted or a power surge/spike in your area?
To cure put in the Feisty live Cd wait until the cd has booted then open a terminal. To use fsck (file system check) your file systems need to be unmounted so open the terminal and type

sudo  fsck /dev/sda1

follow the prompts and hopefully this will repair the file system. What file system did you create? If its ext2 or ext3 fsck is ok, if you used reiser then the command is

sudo reiserfsck /dev/sda1


one last help, if the live disk wants a root password try this
sudo passwd
(enter a password of your choice , then do su  (enter root password) followed by
fsck /dev/sda1

---

### Post by misfito on 2007-05-03
> **vav said:**
> fsck checks the filesystem for errors (something like scandisk in windows). Do 'man fsck' at a terminal window to find out more about the -a etc options. Usually it just means that the system tried to run fsck on its own, using some default options, and that didnt work. So it wants you to run it using some other options.

inodes are part of unix/linux's virtual file system structure. They're links to different objects in the file system.
[http://en.wikipedia.org/wiki/Inode](http://en.wikipedia.org/wiki/Inode)
So any inconsistency in the file system (a misrepresented part of a file, for example) will show up as an inconsistency in the inodes. That's what fsck checks for anyway.

Thank you for your response I apreciate it... But could you tell me, why my machine keeps reseting by  its own, some times when I try to run a program or it just freeze. 
What do I need to post here to let you guys know my problem?
I got to the message of running fsck twice allready (I did run the program). Does fsck fix the problems that it encounters or it just check for them?

Latetly I try to see the updates thru the update notifier but after inserting my password i receive a message: 

E: Type 'Linux' is not known on line 1 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.

I don't not if is somenthing related or not:confused: 

I don't know how that list got damage or how to fix it.

---

