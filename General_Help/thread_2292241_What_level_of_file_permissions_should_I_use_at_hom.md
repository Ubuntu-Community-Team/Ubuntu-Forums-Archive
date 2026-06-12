---
title: "What level of file permissions should I use at home?"
date: 2015-08-26
forum: General Help
---

### Post by seeker.k3 on 2015-08-26
I'd like to know what file permission I should use for my files and directories. When I started using Xubuntu a couple of years ago on a desktop computer, permission wasn't a problem, but when I set up the second computer (Lubuntu) and started transferring files between them I ran into problems Permission Denied. To save myself from resetting the permissions all the time, I tend to set everything to 777, which I suspect is not the right way to go. I'm the only user and I'm logged in automatically at start up. The files and directories are my personal files and directories in my Home directory, and the files are typically .txt, .tex, .pdf, and some scripts, such as .py. Directories can be troublesome too. 
Cheers.

---

### Post by Lars Noodén on 2015-08-26
777 is definitely the wrong way, especially if there are multiple users.  

I'm guessing that you may have different UIDs on the two machines.  If you make them the same, the copying goes like it should. 

What method are you using to try to transfer?

---

### Post by efflandt on 2015-08-26
If you have the same username as on a system you are connecting to through a network (or specify your username on the remote system when connecting), permissions for your own files should normally not be a problem.

Or if using an external drive with Linux file system and you are the initial user on 2 different Ubuntu related systems it should not be a problem (since they should both have same UUID). If it is FAT32 or NTFS file system, they have no concept of *nix directory/file permissions and depending upon default or set mount options may have too much or not enough permissions (executable files or scripts missing the execute bit or execute bit set on all files including non-executable files).

You said you only have 1 user, but if you have more than one user on a system, create them in the same order, so they have same user ID (and preferably with same names, so you do not need to specify name when network connecting to a remote system). However, non-Ubuntu related systems may start the first normal user with a different user ID, which should work if using same username for a remote network connection (or if specifying the remote system username during connection), but may not work accessing a drive from the other system directly (same computer or external drive) if user IDs do not match. If you type *id* in a terminal it shows your uid, gid, and id's of groups you are in. Note that for directories the x bit is sort of like an "access" bit (you need x permission on a directory in order to do "ls" to list its contents or "find" files in it, although, you can still read files that you have read permission for if you know their name).

---

### Post by seeker.k3 on 2015-08-27
I'm using external drives that are either vfat or ntfs.

---

### Post by nerdtron on 2015-08-27
> **seeker.k3 said:**
> I'm using external drives that are either vfat or ntfs.

Then permissions won't matter because NTFS or FAT filesystem doesn't support the linux permissions.

---

### Post by bab1 on 2015-08-27
> **nerdtron said:**
> Then permissions won't matter because NTFS or FAT filesystem doesn't support the linux permissions.
Linux does support permissions on NTFS partitions via [**nffs-3g**]("http://www.tuxera.com/community/open-source-ntfs-3g/").  You have to set the permissions when mounting the partition and they can't be changed after that.  Ubuntu comes with the ntfs-3g package installed by default.

---

### Post by nerdtron on 2015-08-27
> **bab1 said:**
> Linux does support permissions on NTFS partitions via [**nffs-3g**]("http://www.tuxera.com/community/open-source-ntfs-3g/").  You have to set the permissions when mounting the partition and they can't be changed after that.  Ubuntu comes with the ntfs-3g package installed by default.

What I mean to say is that even if you set the permission on mounted NTFS drives, when you open that drive on a windows machine (not samba), the permissions you set on linux won't be honored.

---

### Post by seeker.k3 on 2015-08-28
Here it is:
> **seeker.k3 said:**
> I'd like to know what file permission I should use for my files and directories.

> **seeker.k3 said:**
> The  files and directories are my personal files and directories in my Home  directory, and the files are typically .txt, .tex, .pdf, and some  scripts, such as .py.

The recommended octals is all I'm asking for.

All the stuff about non-linux files systems is irrelevant to me. The confusion is my own fault, mostly because I answered a question from Lars Noodén without quoting it. I'm sorry about that. (I'm no expert here.) To be sure, I'm very grateful for the responses and information provided above, much of which is helpful, but my original question remains.
Thanks all.
:D

---

### Post by Lars Noodén on 2015-08-28
> **seeker.k3 said:**
> The recommended octals is all I'm asking for.

If you want others to be able to read the files and directories then the directories should get 755 and the files 644.
If you want to prevent others from being able to read the files and directories, then the directories should get 750 and the files 640.  

That's assuming no changes to the default group memberships and so on.  It gets more complex obviously if you want to share only some directories or certain files.

---

### Post by seeker.k3 on 2015-08-28
Thank you very much. Cheers.

---

