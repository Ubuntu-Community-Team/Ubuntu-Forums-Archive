---
title: "Very basic Linux  permisison issue"
date: 2020-10-12
forum: General Help
---

### Post by helen314 on 2020-10-12
I have a file with permission "root",  I am copying it to directory with same permission -  root . 
I cannot , have no valid permission. 

What gives?

---

### Post by Impavidus on 2020-10-12
Required reading for all Linux beginners:
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

"root" is probably the owner of the file and directory. The permissions are something like read-write for owner, read for group, read for others, encoded as (depending on tool) rw-r--r-- or 644 or something like that. To copy a file to a directory, you need write and execute permission on the directory and read permission on the file you want to copy.

---

### Post by HermanAB on 2020-10-12
$ sudo cp filename /root/.

---

### Post by TheFu on 2020-10-12
> **helen314 said:**
> I have a file with permission "root",  I am copying it to directory with same permission -  root . 
I cannot , have no valid permission. 

What gives?

What they said above plus, unix systems are multi-user, always.  Every program runs with an effective userid and effective groupid.  Those values and both directory and file permissions are what determine read, write, move, delete access.  Every popular OS today uses this model except 1. Unfortunately, that one has over 90% of the desktop market.

Permissions are core to Unix security.

---

### Post by helen314 on 2020-10-12
> **TheFu said:**
> What they said above plus, unix systems are multi-user, always.  Every program runs with an effective userid and effective groupid.  Those values and both directory and file permissions are what determine read, write, move, delete access.  Every popular OS today uses this model except 1. Unfortunately, that one has over 90% of the desktop market.

**Permissions are core to Unix security**.

No argument there, however, if a user creates a disk (partition) , is allowed to format it  etc.  -  then why he is not allowed to write into it? 
IMHO  this "security" issue goes along same philosophy as  asking user  to  confirm  anything - "are you sure you want to do that ?" 
Developers need to be more responsive , perhaps having a single "security"  option

"do you want to be second-guessed at every step   yes / no " 
Just kidding

---

### Post by TheFu on 2020-10-12
> **helen314 said:**
> No argument there, however, if a user creates a disk (partition) , is allowed to format it  etc.  -  then why he is not allowed to write into it? 
IMHO  this "security" issue goes along same philosophy as  asking user  to  confirm  anything - "are you sure you want to do that ?" 
Developers need to be more responsive , perhaps having a single "security"  option

"do you want to be second-guessed at every step   yes / no " 
Just kidding

Seems we have a misunderstanding as to what actually happened when the disk was partitioned and formatted.  Your userid didn't do that. Something asked and received authority to change the effective userid whether that was clear or not, I don't know.

Unix wasn't created by dumb people. Step into the golden light of "the Unix way".  There are books about it.  [https://en.wikipedia.org/wiki/Unix_philosophy](https://en.wikipedia.org/wiki/Unix_philosophy)  It as been around almost 50 yrs.

We aren't going to change the entire permissions model of unix. Change that and we don't have unix anymore.

As you learn more, you will see why things are the way they are.  For now, just know there are reasons, required by the OS security model.  [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php)

---

### Post by Impavidus on 2020-10-13
> **helen314 said:**
> No argument there, however, if a user creates a disk (partition) , is allowed to format it  etc.  -  then why he is not allowed to write into it? 
IMHO  this "security" issue goes along same philosophy as  asking user  to  confirm  anything - "are you sure you want to do that ?" 
Developers need to be more responsive , perhaps having a single "security"  option

"do you want to be second-guessed at every step   yes / no " 
Just kidding

An ordinary user can't create a partition. Only the root user can. Linux (and the rest of the UNIX family) was designed from the start as a multi-user system. So imagine that you run a school system. The system admin can run sudo to effectively become the root user, so he can format partitions, create users, set disk quota etc. The pupils from class 3 can't. They can only do whatever they want in their own home directory and read or execute some other files if they are allowed so by the owners of those files. This is necessary, as otherwise they would be able to destroy the system.

Even if you're the only human user of your computer, this model is useful. There are various services running as their own user, which have access limited to particular parts of the filesystem, and applications run by that single human user are also limited to that user's home directory, even if that user can use sudo. This helps to contain malware and to limit the effects of user errors.

BTW, Linux rarely asks “Are you sure you want to do that?” It just does what you ask if you're allowed to do so, even if you ask to destroy the system.

---

### Post by helen314 on 2020-10-13
> **Impavidus said:**
> An ordinary user can't create a partition. Only the root user can. Linux (and the rest of the UNIX family) was designed from the start as a multi-user system. So imagine that you run a school system. The system admin can run sudo to effectively become the root user, so he can format partitions, create users, set disk quota etc. The pupils from class 3 can't. They can only do whatever they want in their own home directory and read or execute some other files if they are allowed so by the owners of those files. This is necessary, as otherwise they would be able to destroy the system.

Even if you're the only human user of your computer, this model is useful. There are various services running as their own user, which have access limited to particular parts of the filesystem, and applications run by that single human user are also limited to that user's home directory, even if that user can use sudo. This helps to contain malware and to limit the effects of user errors.

BTW, Linux rarely asks “Are you sure you want to do that?” It just does what you ask if you're allowed to do so, even if you ask to destroy the system.

With all respect to your post , please read the OP and then explain how  "permission"  and  "read / write /etc. " relate?
Let me repeat - as "root" I created a resource which I cannot use as ROOT. 
BTW solved the issue by changing the ownership.

---

### Post by GhX6GZMB on 2020-10-13
You're mixing up ownership (user/group/others) with permissions (r/w/x).

Think about it this way: you own a car and have it in a garage with two spaces. Both spaces are owned by you.

But that doesn't mean that your neighbor can go into your garage and move your car from one space to the other. Only you can do that.

---

### Post by The Cog on 2020-10-13
If you couldn't copy the file to another directory, then either you didn't have read permission for the file, or you didn't have write permission for the directory. Very likely, you weren't trying to do it as root, because root almost always has permissions to things. One exception (which may be relevant in this case since you mention partitions) is if the directory has a read-only filesystem mounted on it.

But I think it is most likely a permissions issue. > I have a file with permission "root" A file doesn't have a single permission - it has different permissions for the file owner, for members of the user group the file is allocated to, and for all other users. So you have to ask yourself which of those categories you fall into and whether those categories have permission.

>  I am copying it to directory with same permission - root 
Same issue here - you need write permission to the directory to be able to add files to it. Are you the owner, group member or just someone else? What permissions does that give you?

When you created a partition, you **must** have done that as root (because only root can). Whatever you used will have asked you for your password again before doing the partitioning **as root**. 

What user id were you using when you tried to copy the file? Probably your login id. 
How did you try to copy the file? Graphical file manager or command line?  
HermanAB already showed how to copy a file **as root** by using the command line (post #3). sudo asks to do something as root.

---

### Post by Impavidus on 2020-10-14
Yes, I read your OP. It's fairly short. You wrote you have a file and a directory with root permissions. However, root is not the permissions of a file or directory. It's the owner, or maybe the group. The permissions are the read/write/execute thing set separately for the owner, the group and others (there are also the setUID, setGID and sticky bit as part of permissions, but those are not so important here). So if you encounter a permissions issue, you look at the owner and group of the involved files and directories, compare that to the user ID and group ID of the process accessing them and look at the permissions set for that user and group. If the effective user ID of the process matches the owner of the file, look at the permissions for the owner, if the effective user ID doesn't match, look at the group ID, if that doesn't match, take permission set for others.

One occasionally says that a process has root permissions. That means that it has root as its effective userID.

When you run an ordinary program, its effective user ID is you. The sudo program is owned by root and has the setUID bit set, which means that sudo always has root as its effective user ID. This allows you to run programs as root via sudo. Never set this bit on any program yourself, unless you're really sure about what you're doing.

---

### Post by helen314 on 2020-10-16
I  have gained some basic understanding about this issue.
AS I said , I have corrected the problem by changing ownership of the /media folder.
So now I can copy files from one place to another in /media folder.

BUT 
I cannot do **"find"  ALL files recursively ** until I CHANGED  into 
/media  folder.



[```

a@a-SATA:~$ sudo find . -name  "*.pro" 
./untitled/untitled.pro
a@a-SATA:~$ 

a@a-SATA:/media$ sudo find . -name "*.pro"
./a/Ex Drive Co/Briefcase OpenLW/0 tcc_mdi/Downloads/Multhreaded QT/qt-opencv-multithreaded-1.21/qt-opencv-multithreaded-1.21/qt-opencv-multithreaded.pro
./a/Ex Drive Co/Briefcase OpenLW/OpenCamera Keep/Downloads/Multhreaded QT/qt-opencv-multithreaded-1.21/qt-opencv-multithreaded-1.21/qt-opencv-multithreaded.pro
./a/Ex Drive Co/Disk G/0 OpenCamera/Downloads/Multhreaded QT/qt-opencv-multithreaded-1.21/qt-opencv-multithreaded-1.21/qt-opencv-multithreaded.pro
^C
a@a-SATA:/media$ 



```

Until I found that changing the folder "find" does what is advertised - looks for  files recursively,
this was THE MAJOR problem in  fixing my system.

---

### Post by TheFu on 2020-10-16
```
find .  -some other arguments ....
```
Says to search from the CWD down.  If you'd like to search elsewhere, 
```
find /media  /var /etc -some other arguments ... 
```

---

### Post by Impavidus on 2020-10-17
> **helen314 said:**
> I  have gained some basic understanding about this issue.
AS I said , I have corrected the problem by changing ownership of the /media folder.
So now I can copy files from one place to another in /media folder.
I doubt changing the owner of /media to something other than root is the best solution to any problem. /media contains nothing other than mountpoints for other devices. One can change ownership there or, if they are non-linux filesystems that don't support permissions, use the mount options.

> BUT 
I cannot do **"find"  ALL files recursively ** until I CHANGED  into 
/media  folder.
The first argument of find is the the directory where it has to search. The directory "." refers to your current directory. So indeed, if you use that, you should change to the right directory first.

---

### Post by T6&amp;sfpER35% on 2020-10-17
> [COLOR=#000000]*BTW, Linux rarely asks “Are you sure you want to do that?”*[/COLOR]

[CENTER][COLOR=#3C3C3C][FONT=&amp]&#8593;[/FONT][/COLOR][/CENTER]

this made me chuckle

[ATTACH=CONFIG]287166[/ATTACH]

---

### Post by The Cog on 2020-10-17
Just to reinforce what Impavidus said: find searches a given directory and its contents - searching down the tree through directories in that original directory. It doesn't search up and outside of the search directory, and . is your current working directory (as shown by the **pwd** command). This is your home directory **/home/username** when you start a new command window. To search the entire filesystem, you need to search from / downwards. This will take a long time though. Unfortunately, /media/username is way outside of /home/username, so you really do need to specify /media/username when you launch the search (/media would probably do actually). Incidentally, the search directory is optional, and defaults to your current working directory.

That set me thinking. Slightly off topic but ever mind. Users who are new to the command-line interface are probably not aware of the concept of a current working directory - all they have ever seen and used will be file managers or open/save dialogs which don't even hint of such an idea. I dimly remember having it explained to me when being shown the DOS command prompt many years ago and it has had time to become second nature to me. But even now it feels slightly odd to know that every process has a current working directory, even GUI ones like file managers or LibreOffice. 

I'm not suggesting that helen314 doesn't know of current working directories, but it just occurred to me in an idle moment that I don't think I have ever seen a post trying to explain the idea to newcomers.

---

### Post by helen314 on 2020-10-17
> **The Cog said:**
> Just to reinforce what Impavidus said: find searches a given directory and its contents - searching down the tree through directories in that original directory. It doesn't search up and outside of the search directory, and . is your current working directory (as shown by the **pwd** command). This is your home directory **/home/username** when you start a new command window. To search the entire filesystem, you need to search from / downwards. This will take a long time though. Unfortunately, /media/username is way outside of /home/username, so you really do need to specify /media/username when you launch the search (/media would probably do actually). Incidentally, the search directory is optional, and defaults to your current working directory.

That set me thinking. Slightly off topic but ever mind. Users who are new to the command-line interface are probably not aware of the concept of a current working directory - all they have ever seen and used will be file managers or open/save dialogs which don't even hint of such an idea. I dimly remember having it explained to me when being shown the DOS command prompt many years ago and it has had time to become second nature to me. But even now it feels slightly odd to know that every process has a current working directory, even GUI ones like file managers or LibreOffice. 

I'm not suggesting that helen314 doesn't know of current working directories, but it just occurred to me in an idle moment that I don't think I have ever seen a post trying to explain the idea to newcomers.

OK, I will freely admit ALWAYS having issue with Linux structure and consequentially with "security". 
So is this correct understanding ?
When I log in I go to  "current directory / folder " - which in the structure  is 
"?/ home / user"  ? 

So if I do this command 

```

a@a-SATA:~$ cd //
a@a-SATA://$ ls
bin          dev         initrd.img.old  media  root  srv  var
boot         etc         lib             mnt    run   sys  vmlinuz
cdrom        home        lib64           opt    sbin  tmp  vmlinuz.old
dead.letter  initrd.img  lost+found      proc   snap  usr
a@a-SATA://$ 

```

what is my "current directory " in Linux structure ?

---

### Post by GhX6GZMB on 2020-10-17
This might help:

[https://www.thegeekstuff.com/2010/09/linux-file-system-structure/](https://www.thegeekstuff.com/2010/09/linux-file-system-structure/)

Unless you're modifying your system, the only place you need to be is in /home

Under /home, every user has an own file structure rof work, documents, pictures etc.

---

### Post by helen314 on 2020-10-17
> **ml9104 said:**
> This might help:

[https://www.thegeekstuff.com/2010/09/linux-file-system-structure/](https://www.thegeekstuff.com/2010/09/linux-file-system-structure/)

Unless you're modifying your system, the only place you need to be is in /home

Are you calling using /media "a system modification" ?


Under /home, every user has an own file structure rof work, documents, pictures etc.

Absolutely  correct IF you are NOT using any external storage devices.

 
Your comments are much appreciated, however,
using / searching external storage was THE MAIN reason for my original post, hence somewhat 
simplifying the actual resolution  of the  issue. 
Thanks

---

### Post by The Cog on 2020-10-17
The top directory is /, not //. I guess you've tried the **cd** command.  This changes your working directory. So next time you use **ls**, it lists the contents of / rather than /home/username. Because that's your working directory. 
So if you want to search in /media/username, there are two ways. One is to go there and search where you are:
```
cd /media/username
find -name "*pro"
```
and the other is to stay at home and tell find where to look:
```
find /media/username "*pro"
```
Which I use depends: If I am likely to use several commands on the contents of that directory then it's easier to change so it's my working directory than having to keep typing the path to the "other" directory into each command. Any command you type that takes a filename will use your current working directory as the starting point. So if your cwd is /home/you, then "ls Documents" will list the contents of /home/you/Documents. There are two ways to look outside of your home /home/you. One is to use the double dot ".." meaning "up one directory" so that "ls .." will list the contents of /home (see all the other user's names). The other way is to start at the top by starting the path with "/". "ls /" lists the contents of the very top directory.

Hope that helps. Gotta go now.

---

