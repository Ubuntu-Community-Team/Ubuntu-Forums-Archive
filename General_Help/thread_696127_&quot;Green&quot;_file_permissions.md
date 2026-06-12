---
title: "&quot;Green&quot; file permissions"
date: 2008-02-13
forum: General Help
---

### Post by BobLand on 2008-02-13
I downloaded the contents of an XP drive that I wish to reformat.  All of the files have the "x" attribute set and are owned by root.  It is easy to traverse the branches to change ownership but if I do the same, after changing, them with chmod, the files loose all permissions and I can't do anything, even cd.  I have do delete the branch with root and recopy them.

So far, the only way to chmod them is going to the end of the branch and chmod directory by directory up the branch.  Fine, for a few files but this particular branch has 35000 files.

As you can imagine, this is hugely time consuming and very tedious.  One slip and the directory is down the drain.

Ideas?

bobland

---

### Post by seventhc on 2008-02-13
Are you just formatting it, or are you also trying to back up the files?
If just formatting it then install gparted
```
sudo apt-get install gparted
``` and at the terminal and type ```
gksudo gparted
``` which will give you the permissions you need.
If you need to get files from itfirst , you can try ```
gksudo nautilus
```

---

### Post by BobLand on 2008-02-13
Formatting is no problem.   I can chown all the way down the branch.  If I chmod then all the files have permissions 
??? - - - ? - ? the file is listed in a black background and the only thing I can do is delete is via sudo.  

So far, I have to go to the tip, do the chmod and work my way back.  This is agonizing but I'll do anything to get as far away from Windows as possible.

---

### Post by seventhc on 2008-02-13
I don't understand why you would need to change permissions to format it, am missing something here? :confused:

---

### Post by BobLand on 2008-02-13
My only concern is the downloaded files.  They all came into linux from xp owned by root with 777 permissions.

The files are in a directory called PhotoArchives.  There are, or will be, 6 main branches.  The branch I'm on now is called D30.  There are 12,000 files in various directories in this branch.

I can change ownership to myself using a simple
```
sudo chown -R me:me D30
```
Every file and directory on that branch is now owned by me.  If I execute 
```
sudo chmod -R 644 D30
```
then everything below the D30 directory will have no permissions, with only ? in place of characters.  I can no longer read the file or cd to the directory, even as root.

The only option is to delete from there down.  The PhotoArchive will eventually hold over 50,000 files.  I really don't want to go thru every directory changing the permissions.

I could leave them all 777 but I don't know if there are side-effects to this.  For this reason, I'd like to globally change all jpg, jpeg, png, psd and the like to 644.  I imagine I could devise a similar scheme to convert the directories to 755.

After all of this is done, I'll reformat/repartition the drive using gparted, which I have on a LiveCD.

I know this sounds kooky but I hope it is somewhat clear.


bobland

---

### Post by BobLand on 2008-02-13
I want to clarify something.  I've mounted the drive with ntfs-3g so all the permissions went to root as 777.  I'm wondering if I can remount it so the permissions are kept, if xp has such a concept, and the owner would be me, as it is on xp.  Actually, the drive was originally created with Windows2000.  The mbr was trashed so I just installed xp over it.  I don't know if that contributed to the problem or this is just the way ntfs-3g works.

I've tried a few different syntaxs but it always comes out like this.  I'm open to any ideas for formating the mount string.

Thanks,
bobland

---

### Post by seventhc on 2008-02-13
OK, But couldn't nautilus do this for you?
I mean before you change anything *gksudo nautilus* then right click on *PhotoArchive* and change permissions and check the box to *Apply Permissions to Enclosed Files*?
Are you trying to save these files? You never said if you were, only that your formatting.

**Edit:** I didn't see your last post when i was writing this. just saw it now
I don't have any experience with ntfs-3g

---

### Post by BobLand on 2008-02-13
I re-read my initial post and realized I shouldn't have said anything about reformatting.  As far as the drive is concerned, the garbage can would be just as good a place for it as it is fairly old and a bit too noisy.

My real concern is the permissions on the files.  Every file mounted in /media/xp via ntfs-3g from the XP disk is owned by root and has permission 777.  I don't know if it really makes any difference that they are 777, 775 or 644 but I thought they should be changed to their appropriate designation.

Changing ownership is no problem.  Changing permissions is.

My reason for this is post is that using chmod -R kills everything below the parent. 

Example:
Here's what I start with
The directory PhotoArchive/Celtic Art/General is already owned by me as well as the files in it.  The files are marked 777. 
```
ls -la General
drwxrwxrwx 2 burt burt  4096 2007-03-27 18:17 .
drwxrwxrwx 7 burt burt  4096 2008-02-13 18:13 ..
-rwxrwxrwx 1 burt burt 50264 2006-03-02 17:17 boxknot.jpg
-rwxrwxrwx 1 burt burt 15524 2006-03-02 16:54 GorgonS.jpg
-rwxrwxrwx 1 burt burt  5161 2006-03-02 16:54 IrishGargS.jpg
-rwxrwxrwx 1 burt burt 11836 2006-03-02 16:54 LoversS.jpg
-rwxrwxrwx 1 burt burt  7661 2006-03-02 16:55 MillstattSunS.jpg
-rwxrwxrwx 1 burt burt 32889 2006-03-02 16:56 Scandinavia Box.jpg
-rwxrwxrwx 1 burt burt 12238 2006-03-02 16:54 StPatrickS.jpg
-rwxrwxrwx 1 burt burt  8390 2006-03-02 16:54 TripleFaceS.jpg
```
When I try to change permissions
```
burt@maxland:~/PhotoArchive/Celtic Art$ chmod -R 644 General
```
Here's what I get
```
chmod: `General': Permission denied
```

```
burt@maxland:~/PhotoArchive/Celtic Art$ ls -al General
total 0
?--------- ? ? ? ?                ? General/.
?--------- ? ? ? ?                ? General/..
?--------- ? ? ? ?                ? General/boxknot.jpg
?--------- ? ? ? ?                ? General/GorgonS.jpg
?--------- ? ? ? ?                ? General/IrishGargS.jpg
?--------- ? ? ? ?                ? General/LoversS.jpg
?--------- ? ? ? ?                ? General/MillstattSunS.jpg
?--------- ? ? ? ?                ? General/Scandinavia Box.jpg
?--------- ? ? ? ?                ? General/StPatrickS.jpg
?--------- ? ? ? ?                ? General/TripleFaceS.jpg

```
At this point, everything in General is a zombie that must be shot in the head.

Hope this makes things a little more clear.
bobland

---

### Post by seventhc on 2008-02-13
AH, now it is much more clear, sorry it took so long for that to sink in. lol
I have to try to find something then I'll post back.

---

### Post by seventhc on 2008-02-13
hmmm
I just tried a test and here is what I get.
```

j0hn@cipher:~$ chmod -R 644 test
j0hn@cipher:~$ ls -la test
ls: cannot access test/.: Permission denied
ls: cannot access test/..: Permission denied
total 0
d????????? ? ? ? ?                ? .
d????????? ? ? ? ?                ? ..
j0hn@cipher:~$ sudo ls -la test
[sudo] password for j0hn: 
total 8
drw-r--r--  2 j0hn j0hn 4096 2008-02-13 20:55 .
drwxr-xr-x 86 j0hn j0hn 4096 2008-02-13 21:00 ..

```tried this
```

j0hn@cipher:~$ chmod  -R 744 test
j0hn@cipher:~$ ls -la test
total 8
drwxr--r--  2 j0hn j0hn 4096 2008-02-13 20:55 .
drwxr-xr-x 86 j0hn j0hn 4096 2008-02-13 21:00 ..

```this would give you the owner *read/write/execute* capabilities, while everyone else can only read it.

---

### Post by BobLand on 2008-02-13
Have you tried this with populated directories?  I'm wondering if it has something to do with an "illegal" setting of 644 on a directory that causes the "crash."

bobland

---

### Post by seventhc on 2008-02-13
well, sort of empty, I created a test folder then put one folder in that(test1) and another sub folder in that folder (test2)
So 3 folders total, but all empty.

---

### Post by BobLand on 2008-02-13
If I run the chmod -R 644 from the parent it crashes the files inside.

I guess the real question is do files have to be 644 and directories 755?  Is this a tradition or is there some reason for it?  On the same hand, does it matter if a non-executable file has an executable attribute?

All that green is sort of ugly...

bobland

---

### Post by seventhc on 2008-02-13
I am not to sure really, trying to find some info on it.

---

### Post by pjkoczan on 2008-02-13
The 'x' bit for directory permissions is used to answer "can I traverse this directory?"

Quoth the Wikipedia ([http://en.wikipedia.org/wiki/File_system_permissions](http://en.wikipedia.org/wiki/File_system_permissions)):
The execute permission, which grants the ability to execute a file. This permission must be set for executable binaries in order to allow the operating system to run them. When set for a directory, this permission grants the ability to traverse its tree in order to access files or subdirectories, but not see files inside the directory (unless read is set).

To solve this, you can use the 'find' command. You can find all the directories in a given filesystem tree with:

```
find -type d .
```

Even better, you can run commands from within find. So, you can chmod all your regular files with:

```
find -type f . -exec chmod 0644 {} \;
```

and your directories with:

```
find -type d . -exec chmod 0755 {} \;
```

find can also filter based on name, uid, timestamps, etc. Check the man page for all the fun things you can do with find. :)

---

