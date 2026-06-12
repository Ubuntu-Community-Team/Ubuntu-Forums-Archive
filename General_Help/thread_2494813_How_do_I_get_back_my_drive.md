---
title: "How do I get back my drive?"
date: 2024-01-27
forum: General Help
---

### Post by dorasmith24 on 2024-01-27
When I run Windows 10 on my Ubuntu computer, I lose the ability to open my mail folders, and open other than in write access my other files, such as Libre Office.  My mail and my documents are in separate partitions on a separate drive. 

Both partitions are formatted as NTFS, as I wanted to be able to open them or store files on them from Windows as well.

Most recently, when in Windows 10, I ran windows updates and speed testing of my internet; I did not create, open, or alter a single file on that drive.  My Windows drive is not now even in my computer.  

Nevertheless I can't open my mail folders in Thunderbird, nor edit any document in Libre Office.

Eventually, after some indefinite number of reboots, this problem always mysteriously solves itself.   

This is an example of what ls -l gives me:

drwxrwxrwx 1 root root      4096 May 11  2019 'Typing Instructor Platinum'
-rwxrwxrwx 1 root root       445 Mar 21  2014  usmt32.bat

For every directory or file on the drive as appropriate, and ditto for the mail folders on the other partition.

It looks as if I have read and write access to everything there - or, rather, root does, which doesn't look inappropriate.

Running chown didn't fix it.   

But it looks as if I own my files - or root does.   Chown was supposed to change ownership to dora.   I didn't mess with group as I don't know what that does.

Actually, however, when I look at the Documents folder in my Ubuntu drive, dora as user and group owns every directory and file.

So do I need to change ownership from root to dora?  I did just learn that if root owns the directories and files, user can't fully access them.   

[COLOR=#333333][FONT=&amp]sudo chown -R dora [/FONT][/COLOR]/mnt/966A029F6A027C6D did nothing; do I have to do 

sudo chown -R dora:dora /mnt/966A029F6A027C6D?

I did sudo -i to change to root, then ran chown -R dora:dora /mnt/966A029F6A027C6D, and now ls -l gives me 

drwxrwxrwx 1 root dora      8192 May 11  2019 'Word Press themes'
-rwxrwxrwx 2 root dora  86770592 Mar 28  2014  WSUS30-KB972455-x64.exe

It changed the group to dora but not the owner.  

I tried it again.  Same thing.

 It may think I'm not in Root.  "[COLOR=#474747][FONT=&quot]On Linux, only root can use chown for changing ownership of a file, but any user can change the group to another group he belongs to"   [/FONT][/COLOR] Aren't you in root if you did sudo -i and you've got a #?  

How can I fix this instead of waiting until time ends for it to fix itself?

How is Windows 10 changing ownership of my directories and files from dora to root?   Windows 10 shouldn't even know what root means!  

Thanks!

---

### Post by jeremy31 on 2024-01-27
Sounds like what the Windows hybrid shutdown does to a drive
The usual fix is to boot into Windows, disable the hybrud shutdown/fast startup and then boot into Ubuntu

---

### Post by TheFu on 2024-01-27
NTFS file systems don't support Unix permissions which means **_chown/chmod don't work_**. Don't bother.  Only using mount options are owner, group, and permissions set to foreign file systems like exFAT, FAT32 and NTFS.  There's NO OTHER WAY to allow access, once the file system can be opened by Linux.  The best way to set mount options is in the /etc/fstab. Sorry, there's no GUI for this.  Further, using a file manager to access that storage won't use optimized settings, so it is likely performance will be 20-30% less than if you mount through the /etc/fstab (or autofs).

However, as Jeremy wrote, it is likely that some MSFT update re-enabled hibernation mode on the file systems. You probably disabled that years ago and need to do it again.  It is something easy to forget.

---

### Post by dorasmith24 on 2024-01-28
Please tell me exactly how to fix it.    What do I specifically do in /etc/fstab to give me back ownership of the drive?  I'm not seeing any way to use /etc/fstab to change drive ownership.  

What does mount options have to do with what owns the drive?

If this is the contents of my fstab folder, and the affected partitions are as follows, please tell me SPECIFICALLY AND EXACTLY what changes to make.  Every single discussion I can find is written entirely in Greek with a quarter of the instructions even actually provided.

Mail   Partition 1  /dev/sdb1 NTFS - Mounted at /mnt/32DE2C25DE2BDFB9  UUID 32DE2C25DE2BDFB9
Data  Partiton 2  /dev/sdb2  NTFS - Mounted at /mnt/32DE2C25DE2BDFB9  UUID 966A029F6A027C6D

Contents of fstab file:  (Please note that the Windows drive is not currently even in the computer.)

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda5 during installation
UUID=24029b02-231a-45b8-b4c5-7154e6bb0a53 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=6b7317f0-2b52-493a-bbc7-fa266e1ee64b /home           ext4    defaults        0       2
# swap was on /dev/sda1 during installation
UUID=2a7565aa-6abb-4db2-b713-acaf51624021 none            swap    sw              0       0
/dev/disk/by-label/Windows7VM /mnt/Windows7VM auto nosuid,nodev,nofail,x-gvfs-show 0 0
/dev/disk/by-uuid/32DE2C25DE2BDFB9 /mnt/32DE2C25DE2BDFB9 auto nosuid,nodev,nofail,x-gvfs-show 0 0
LABEL=Win7P32 /media/dora/Win7P32 auto nosuid,nodev,nofail,x-gvfs-show 0 0
/dev/disk/by-uuid/7BC3312A37E89C0F /mnt/7BC3312A37E89C0F auto nosuid,nodev,nofail,x-gvfs-show 0 0
/dev/disk/by-uuid/966A029F6A027C6D /mnt/966A029F6A027C6D auto nosuid,nodev,nofail,x-gvfs-show 0 0
```

---

### Post by ajgreeny on 2024-01-28
You need to edit fstab using the options shown for NTFS at [https://help.ubuntu.com/community/Fstab#Options](https://help.ubuntu.com/community/Fstab#Options)

Read it carefully then edit /etc/fstab using all the appropriate options that will give you ead/write permissions on that filesystem.
Sorry, there's no other way and no GUI that I know of, though I think I've read that it can be done in Gnome-disks (Disks in your menu system) so it might be worth looking at that.

This, I'm afraid one of the differences between the OSs that helps keep Linux more secure and you will have to accept this or find another way to share those files between the two OSs.
I can't give you more detailed info as I do not use NTFS or Windows any more.

---

### Post by oldfred on 2024-01-28
I see some mounts by UUID and some by label
Best to label every partition and then those partitions not mounted in fstab will auto mount by label. But default mount parameters may not be best for Windows formats.
Do not know if your label mounts overlap your UUID mounts.


Mount parameter examples, ext4, NTFS, exFAT:
[https://ubuntuforums.org/showthread.php?t=2464668](https://ubuntuforums.org/showthread.php?t=2464668)
[https://ubuntuforums.org/showthread.php?t=2467566](https://ubuntuforums.org/showthread.php?t=2467566)
NTFS example fstab entry - TheFu
[https://ubuntuforums.org/showthread.php?t=2493845](https://ubuntuforums.org/showthread.php?t=2493845)

---

### Post by dorasmith24 on 2024-01-28
Actually I probably didn't disable hibernation and fast start in Windows 10. .  I do usually disable hibernation in any OS as a matter of course; it's a profound nuisance and can cause problems in its own right.  But I have been strictly a LInux person for years.  I have Windows on a hard drive for work from home jobs that require use of Windows. I bought and installed it last summer.   Years ago I wasn't using Windows.  I might or might not have disabled hibernation, and I was running updates - and having a lot of trouble with them, so the same updates kept getting reversed and rerun.  I've only run Windows 10 for that one job and also to run genealogical software that won't run in Wine.  I may have disabled hibernation to keep the system from constnatly going to sleep on me, but disabling fast start is something I tend to only do for troubleshooting.  I'm used to Windows versions where you have to specify looooooooooooooooong start if that's what you want.   You can either have fast start, or very loooooooooooooooooong start.  

But who said Windows makes sense - not me!

However, from what you are saying, and other explanations say as well, the problem will recur the minute Windows runs its blasted updates.

---

### Post by oldfred on 2024-01-28
Windows boot slow. So they created Fast Startup which is a hibernation of just the boot files. It sets boot flag on all NTFS (and other Windows formats?). When hibernation flag is set the Linux NTFS driver will not fully mount the partition read/write. You can force mount manually read only.
That is to prevent loss of data, as any write from Linux will be erased when Windows restores the hibernated state.
Windows also turns fast startup back on with some updates.

Fast Start up off (always on hibernation), note that Windows turns this back on with updates, SHIFT + Shut down button
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[https://www.elevenforum.com/t/turn-on-or-off-fast-startup-in-windows-11.1212/](https://www.elevenforum.com/t/turn-on-or-off-fast-startup-in-windows-11.1212/)
[https://www.makeuseof.com/windows-11-turn-on-or-off-fast-startup/](https://www.makeuseof.com/windows-11-turn-on-or-off-fast-startup/)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)

---

### Post by dorasmith24 on 2024-01-28
Thanks. This iS the sort of answer I'm looking for, but some of the information is missing.


Probably partly because I didn't know I had to specify what access I need to those partitions.  Human common sense is that one wants to read, write, and execute one's files, but apparently IT common sense is that, for security reasons, one should ever want only read access to one's files.  


Does the value of 1000 for uid and gid give root, me, and anyone else who can use my computer, read, write and execute access?  If not, what value does?


I have been trying to see what I can find out.  But, even people who write help pages can't write clearly, and You Tube videos are especially good at leaving out most of the information.  


First of all, it isn't clear that uid and gid would have any effect at all on my problem. Can you or can you not change the ownership in Ubuntu, of NTFS partitions, when Windows messed has with it?  I am getting opposing answers on that, each from multiple places.  I understand UID and GID specificaly user and group ownership of their partitions?  


Some instructions say to use them, and use umask, dmask AND fmask, along with them.  Sometimes all three.  


Why do I need to use umask to get access to files and directories that uid already gave me ownership of?  Are some people not counting on uid and gid to work, because they don't know why it sometimes doesn't, like perhaps on NTFS drives that Windows has messed with?  


Is there any reason to use dmask and fmask with umask?  I understand that dmask gives you access to folders, fmask gives you access to files, IT version of common sense is that you wouldn't want to have to same access to folders and to files, but, Umask gives access to both files and folders, and does nothing else that dmask and fmask together don't do.   And, I've seen examples where umask, fmask, and dmask were all used, and each specified something different. 


Is there any reason NOT to use umask with UID and GID, as long as I don't give contradictory specifications, besides that if you actually trust both to work it seems stupid?


What value would I give umask, for read, write and execute access, for all users on my computer?  I can't find a version of hte instructions that even gives the ordinary not-root user access to those files of any sort, and I don't care about restricting other users.  I can not make head or tail out of the instructions on how to subtract base 2 whatever from base 2 whatever and get 7 in base 10 and then reverse it from whatever.

  This table contains I think the values for umask, dmask and fmask, but not for UID and GID.   And seems to contradict the partial instructions I found on the page I've just forgotten again who sent me to. 

[https://www.linuxtrainingacademy.com/all-umasks/](https://www.linuxtrainingacademy.com/all-umasks/)   

This page could be better.   There are two columns, of the effects that each mask has.   What should be the column headings that aren't there?  For example, One column, for 000, does make every file executable; the second column doesn't.  
[TABLE="width: 1"]
[TR="bgcolor: #F0F0F0"]
[TD]000[/TD]
[TD]rw-rw-rw-[/TD]
[TD]rwxrwxrwx[/TD]
[/TR]
[TR]
[TD]001[/TD]
[TD]rw-rw-rw-[/TD]
[TD]rwxrwxrw-[/TD]
[/TR]
[TR="bgcolor: #F0F0F0"]
[TD]002[/TD]
[TD]rw-rw-r&#8211;[/TD]
[TD]rwxrwxr-x[/TD]
[/TR]
[/TABLE]
 


To clarify a wrong assumption one of these two answers went by, these partitions were not CREATED in Windows, they were created in Ubuntu, using NTFS so both operating systems could use them. The only helpful answers I got on another forum, yesterday, and not long ago, explained that fast restart and hibernation enabled in Windows causes this problem, but also that disabling them in Windows won't stop the problem from happening, because it will happen all over again every time Windows runs its stupid automatic and mandatory updates.  They didn't actually tell me how to get back access to my files.  


Thanks!

---

### Post by dorasmith24 on 2024-01-28
Thanks!  That is the one part of this I clearly understand.   However it appears that since the problem happens over again when Windows runs its blasted updates, there is actually no way to prevent it from happening for any length of time, or even necessarily the  next time you boot into Windows.   For whatever reason why it may matter, I"m not using UEFI....

This thing separates my replies from what I'm replying to - if I have more than one paragraph to say.  If every reply I made to the restart/ hibernate suggestion/ explanation appeared with what I was replying to it would be clear why I have now said the same thing four times.

---

### Post by dorasmith24 on 2024-01-28
Thanks, I wish I could see who I'm replying to, but it sent me to a page that I'm supposed to read carefully and make the changes it suggests in fstab.

It's as clear as mud.  

Here are relevant pieces.

"I advise dmask=027,fmask=137 (using umask=000 will cause all your files to be executable). More permissive options would be dmask=000,fmask=111."

There is no explanation of what are the options in values I could use and what they mean.  Maybe it's that I'm an ordinary human being and not IT.  I hate to tell this author, but, I want everyone to have access to my files, who can use my computer.   I also want to make sure I don't leave it impossible to execute executable files.  What are the values that would accomplish that?

Why wouldn't I just use umask?  I don't understand the notion that giving one set of values to folders and another to files, since even by inheritance the files are going to end up with the most specific values!  that makes no sense.   

"user=user,uid=1000,gid=100  0  0" pulled from an actual line in a sample fstab file.   There is no discussion about uid and gid or when to use them or what to use, at all.  And is uid supposed tob e 1000 and gid 100?   What exactly do these values do?

There is no explanation of why or when to use umask vs uid and gid.  There is no discussion of what values to use for uid and gid. 

Because it doesn't explain that, it never even touches on whether uid and gid do anything at all if Windows messed with who owns your NTFS partition.

I've actually been visiting a bunch of such pages, and they're ALL as clear as mud.

---

### Post by dorasmith24 on 2024-01-28
Someone had told me his version of exactly what to put in my fstab file, and the post seems to have disappeared.  Fortunately I had copied it.

I made a further change.  His change was to insert uid=1000,gid=1000 into every line.  

I added fmask=111,dmask=100

Should these two lines involving the two problematic partitions work, one way or the other, even though either there is stupid repetition, or uid and gid will have no effect at all?

I want all users to have read, write and where appropriate execuite access to all of the files in all of the directories.  I'd like to own the partitions, if possible, but question whether that is possible.  


/dev/disk/by-uuid/32DE2C25DE2BDFB9 /mnt/32DE2C25DE2BDFB9 auto nosuid,nodev,nofail,x-gvfs-show,dmask=000,fmask=111,uid=1000,gid=1000 0 0
/dev/disk/by-uuid/966A029F6A027C6D /mnt/966A029F6A027C6D auto nosuid,nodev,nofail,x-gvfs-show,dmask=000,fmask=111,uid=1000,gid=1000 0 0

---

### Post by TheFu on 2024-01-28
So, Unix requires and assumes basic knowledge. This basic knowledge is built onto for more complex tasks.  Typically, mounting storage has been performed by trained administrators, which is why certain things aren't spelled out exactly where someone without the basic knowledge would like to know them.  That's because it is assumed they already know and recognize it.j

To gain basic Unix/Linux knowledge, start here:  [https://www.linuxcommand.org/tlcl.php](https://www.linuxcommand.org/tlcl.php)  

Nobody knows everything and nobody can remember all the things. Unix has built-in help in the form of "manpages".   They are on your system too and should explain every option for every command and every configuration file.  They start with general information and become more detailed the more you read - like a newspaper article starts with a headline, then a summary, followed by 2-4 sentences giving more details, then 1-50 pages of extreme detail, depending on the program or file.

We've been talking about "mount".  The command that does that is called "mount", but it is a front-end to many other mount commands for each specific type of file system.  Each file system type supports different mount options in addition to the mount options spelled out in the main "mount" command.  Think of it like the main newspaper article on page 1 (mount) with even more specifics when the article is continued on page 22 (mount.ntfs).   There's also the manpage for the "fstab" config file, which clearly says the require format for that file and the purpose for each field.

Ok, so to see all this help, use the "man" command.
```
$ man mount
$ man mount.ntfs
$ man fstab
```

Ok.  So, now you know how to find more detailed, exact, correct help, so when we post things here and make mistakes, you'll know to check the manpages on your system.  Every manpage install is tied to the exact version of the program installed on your system.  While manpages don't often change very much from program version to version, sometimes they change greatly, so the manpage on my system can be completely different than the manpage on your system for any specific command.  Use the manages ON-YOUR-SYSTEM for the most current information about any command or config file.

Ok, next, uid is short for {user id}.  If you use the '**id**' command, the uid and main gid for the current user will be shown.  With ubuntu, the first user created has a uid of 1000 and a gid of 1000. These are not connected and the uid or gid can be different.  The username is tied to the uid.  Inside the computer, the integer values for these things is watch matters for the owner and group.  
username ---> userid ---> uid.   Sometimes people will mix the (username and userid) or the (userid and uid).  The username and uid are never confused.  One is an integer number and the other is alphanumeric, but always starts with a letter, should be all lowercase and never contain spaces or punctuation characters.  Basically, it must be a-z and 0-9, nothing else.

The same applies to groupname ---> groupid ---> gid, so I won't repeat it.

dmask - is directory mask.
fmask - is file mask.
Both are like the opposite of file permissions.  They work like IPv4 subnetting masks.  masks are 4 numbers long, not 3.  

Ok, so here's the options I use when mounting NTFS file system.
```
nodev,windows_names,nosuid,noatime,async,big_writes,timeout=2,uid=1000,gid=1000,fmask=0002,dmask=0002
```

What does that all mean?  You can look up the first 7 options in the manpages.  Some are for MS-NTFS only like windows_names and big_writes.
The _uid_ says that the owner of all files and directories will have a Unix, POSIX, owner of uid 1000.  That's typically fine for single user ubuntu systems.
The _gid_ says that group will be used for all files and directories in the file system.  That's typically fine for single user ubuntu systems.
The _fmask_ says to set all files with 775 permissions on the mounted NTFS file system.
The _dmask_ says to set all directories with 775 permissions on the mounted NTFS file system.

It is fairly permissive, but won't allow other users access. For that, you'd probably want to setup a new group that both userids are in and change the gid=1000 to the gid for that new group.

Anyway, that's the NTFS-specific options, explained.  Something similar would be used for FAT32 or exFAT as well.

Just to be 100% clear, these mount options with uid, gid, fmask and dmask are the ONLY WAY TO CONTROL the owner, group and permissions for a foreign file system. There's no other method. chmod and chown will never work with NTFS or FAT-whatever.

BTW, if you want to quote a little bit of the post you are replaying do, use the "replay with quote" button.  Also the advanced editor is helpful to provide extra buttons for code-tags and attachments, though images of text are not good.  Copy/paste the text directly, please.  When quoting others, delete the parts that you aren't responding to. Leave just the parts that are relevant to your reply.

---

### Post by dorasmith24 on 2024-01-28
I specifically want to know if those two lines will work.

---

### Post by TheFu on 2024-01-29
> **dorasmith24 said:**
> I specifically want to know if those two lines will work.

I don't know. Did you try them?  I doubt the dmask and fmask are ideal. You can do the mask calculations, if you like.  Blocking the execute bit isn't bad, but masks need 4 octal numbers according to my notes.  Over the decades, perhaps 3 is acceptable now. Again, IDK. Try it.  I posted the options that I use and 100% know work.

---

### Post by oldfred on 2024-01-29
Old post on mask settings.
From user Morbius1 post #19
[http://ubuntuforums.org/showthread.php?p=12181259](http://ubuntuforums.org/showthread.php?p=12181259)

See post #4 in that thread on sticky bit or the first 0 in most cases.

---

