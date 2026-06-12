---
title: "Where are inode tables for USB drives?"
date: 2013-06-25
forum: General Help
---

### Post by Iggy64 on 2013-06-25
As a Linux beginner, I am trying to comprehend how file permissions are created and saved.  Of particular interest to me are permissions for files on detachable USB devices.  With my very limited knowledge of how these file systems work, I get the general idea that a file's permissions (and ownership and block location and so on) is stored in its inode.  So, the file's name can be looked up in its directory, which provides the inode number, which can then be used to look up the permissions in the inode.  

Next, I have this vague notion that the inodes are stored in tables that are distributed throughout the physical storage devices, so that an inode table is reasonably close to the file(s) it describes.  I don't know if these means it is in the same group block, or just the same disk cylinder, or what.  Too many opinions out there.

Anyway, when I attach a USB drive and then mount it, I assume the mounting process must be creating inode mappings to all the files on the USB drive.  I would really like to know if the inode tables for the files on the USB drive are actually written onto the USB drive.  If so, what happens when I unmount it?  Does the system take all those inodes back into the pool, and the permissions info about the files is simply gone?  When I re-attach and remount the drive later, is a fresh batch of inode tables created? And therefore do I have to re-specify the desired permissions?

Maybe I'm asking the wrong questions because my knowledge of all this is so rudimentary.  But I find file permissions to be rather bewildering and challenging.  If I could better understand what is stored where, and how persistent or temporary it is, it would be very helpful

---

### Post by VMC on 2013-06-25
I'm not sure how deep you want to pursue this, but ```
chgrp --help,chmode --help
```, and ```
ls --help, ls -i (inodes)
``` Also read up on coreutils ```
info coreutils
```

---

### Post by Bashing-om on 2013-06-25
Iggy64;

A different perspective but highlights file structure and the role of inodes:
[http://linux.sys-con.com/node/117909?page=0,0](http://linux.sys-con.com/node/117909?page=0,0)[INDENT=2]
inquiring minds want to know

[/INDENT]

---

### Post by mcduck on 2013-06-25
It's same as with any other drive, really. If the USB drive is formatted into Ext4 or some similar Unix filesystem, then the inodes are stored on the drive itself as they are part of the filesystem.

And on the other hand if the drive is formatted to FAT, for example, there are no inodes as FAT doesn't use them. (And in the same way, the permissions & ownerships can't be stored at all since FAT doesn't support them either)

---

### Post by Iggy64 on 2013-06-25
I do want to learn as much as I can about how GNU/Linux systems work, so  that I can fully break free from Windows.  I very much appreciate the  helpful resources suggested by VMC and Bashing-om.  I have "bookmarked"  those pages (and commands) and have starting drilling down through  them.  I can see how much more I need to learn.  But I am grateful to  know where to find this information.  Indeed, the link at [http://linux.sys-con.com/node/117909?page=0,0](http://linux.sys-con.com/node/117909?page=0,0) definitely provided some "glue" to confirm some of my suspicions and then go a step beyond.  Thanks much for that.

Thanks,  too, to mcduck for your "take" on where the inode information is  stored.  It is consistent with the ideas in the above-mentioned link.   If - in fact - the inodes for the files on a USB drive formatted ext4  are stored in the group blocks on that drive, then I would expect the  permissions (which are contained in those inodes) to continue to exist  when I detach the USB drive and store it elsewhere.  If I re-attached it  a week later, those permissions should still be there, and I won't have  to reset them.  I'll have to try to confirm this with some more  experiments later this week.  Presumably, I could similarly attach the  USB drive to a completely different Linux machine, and still have it  recognize those permissions?  Again, something else to try.

I  suppose if you had lots of different USB drives and took turns  connecting them up to one Linux box, you might use up all the inodes  that the system allocated at system creation time?  If so, how would you  go about freeing up those inodes?  There is so much to learn.

I  understand the business about how FAT drives are different.  But I  wonder about an NTFS USB drive that has been mounted with the  --permissions option.  Are inodes created on such a drive?  If not,  where are the permissions stored?  How persistent are they, compared  with those on an ext4 drive?

Why do I want to know all this?  So  far, I am much more of a user than a OS expert (as if you couldn't  tell).  A main hobby is collecting, processing, and playing music  files.  Some of my legacy collections are on NTFS drives.  (Sure, I  could copy them all to ext4 drives; but there is only so much time.)   Over the years, I have had various overzealous software packages mess  with the metadata in my music files ("helping me out" by updating stuff I  don't want to change).  In my Windows days, I soon learned to make all the music  files "read only" and leave them that way, except when I really wanted  to make changes.  So no more costly "accidents" happened.  Now, when moving to  Linux, I hear about all the added security features.  But I quickly  found that these features come with a price: they can be very  complicated for someone who is mainly a "user."  In Windows, the "read  only" attribute was simply stored with the file -- easy to visualize.   In Linux, the permissions are broken into three groups (user, group,  other), and not stored with the file, but spread around in various inode  tables.  The directory links the file to the inode table which is  somewhere in the group block, which is .... .  So there seems so much  more to learn if you don't want to screw up, and you want to feel  comfortable that you are actually protecting your files.

Therefore,  I thank those of you who responded because your help is invaluable.  I  have read for many hours, and made little diagrams all over my  notebook.  I am beginning to understand how this works, but am not super  confident.  Without your help, this would take me forever.  I really,  really appreciate the support offered by this forum.

---

### Post by mcduck on 2013-06-26
As inodes are not an opertaing system feature but instead a file system feature, there is no one pool of inodes the OS would assign from when you mount a drive. INstead each filesystem has it's own inodes, created at the time when the drive(or partition) was formatted.

So you'll never run out of inodes by mounting drives, only by using more inodes in a specific filesystem (partition or a drive) than what it was set to have when it was formatted. And filesystems that don't use inodes don't get assigned any when they are mounted either. Different filesystems have their own ways for managing files and their ownerships, permissions and other metadata.

What comes to permissions on removable drives formatted with Unix filesystems, they are indeed stored on the filesystem itself and will work after removing and reconnecting the drive, or when moved to another machine. The only limitation is that ownership is not tied to user name, but the UID which is the numerical version of user name, and same UID might be used by different user account on another computer.

---

### Post by Iggy64 on 2013-06-26
mcduck, that is extremely helpful stuff!  I have been reading one tutorial after another for days on this subject, I haven't come across such a straightforward, logical explanation.  Now I feel like I have a decent idea of how to protect my files on an ext4 drive/partition.  I am saving your explanation to my KeepNote notebook.

Do you by chance have any thoughts on my other question, concerning NTFS drives?  I probably won't be using them much longer, since I will be working on transfering all that old content onto newly formatted ext4 drives.  Meanwhile, though, it would be nice to understand how permissions are stored for files on those NTFS drives.  To the best of my knowledge (which isn't much, yet), I can enable Linux-type permissions on an NTFS drive by mounting the drive with the --permissions option.  What I wonder now is: does Linux somehow write inode tables into the blocks on an NTFS drive, even though it is not a native Linux file system?  Or are the permissions stored some other way/place?  Bottom line: Are they stored on the NTFS disk (as in the case of an ext4 drive), so they will persist when the drive has been detached and then re-attached and remounted?

Thanks very much for your continuing support.  This has been one of the most helpful discussions I've had in trying to learn Linux basics.

---

### Post by mcduck on 2013-06-26
NTFS has it's own way of storing file permissions and file metadata, and when you mount an NFTS drive with the --permissions the filesystem driver in Linux simply remaps the UNIX permissions into NFTS permissions, and then the filesystem is able to store them just like if you were setting the permissions while running Windows. So no inodes are created or used to store permissions on NFTS drives.


Anyway, like I said the ownership of files is based on UID, not a specific user, so file ownership and permissions are not a secure way to restrict access to your file. They are intended to protect files between users of a running system, but if somebody is able to move the drive to another computer, or even boot the same computer with another operating system, the ownerships won't help you. To secure your files in that kind of situations encryption is the only option.

(if you want a simple to use and flexible way of encrypting files & directories, I recommend taking a look at [Gnome EncFS Manager]("http://www.webupd8.org/2013/05/gnome-encfs-manager-cryptkeeper.html#more"), which allows you to create encrypted directories and mount & unmount them as you wish rather than having to encrypt the complete filesystem. Works nice with removable drives and even with Dropbox and other cloud storage services ;))

---

### Post by Iggy64 on 2013-06-26
Thank you, mcduck, for the additional info.

From my reading, I get the impression that NTFS systems store their file metadata (permissions, dates, block locations, etc.) in a "Master File Table," with an entry for each file on the system.  Each record in the MFT is therefore equivalent to an inode in Linux.  However, it sounds like all the records are in one large file (MFT), rather than distributed about the disk in smaller tables, as they are in Linux.

So, if I mount the NTFS drive using the permissions option, does Linux use my current Linux default permissions to overwrite the entire MFT, or does Linux simply read the permissions that are already present in the MFT and interpret them in Linux terms?  And if I use chmod to change permissions on the NTFS drive, does Linux "do its best" to create the Windows-equivalent permissions in the MFT?  (I realize that I should be simply trying this out, but I really don't want to play games with any of valuable NTFS data right now.  Perhaps I can find an old drive to use for experimenting.)

Thanks for the advice on encryption.  Right now, that is not my concern.  I'm virtually the only one with access to any of these disks.  My worry is the accidental modification of files that are not write protected.  As I may have noted earlier, I have had certain music-playing software automatically changed the metadata in hundreds of my files without my knowledge, only to be discovered sometime later --- causing me to spend hours/days repairing them.  Therefore I want these music files to be read-only, unless I want to switch them briefly to writable, when I WANT to change/update the tags.  So I want to make the NTFS disks read only most of the time, but also want to be able to temporarily chmod to writable when I need to update at tag.

With your help (and patience), I feel that I am getting closer to understanding how this works.  If I can understand it, I can probably avoid making dumb mistakes.

---

### Post by JKyleOKC on 2013-06-26
> **Iggy64 said:**
> So, if I mount the NTFS drive using the permissions option, does Linux use my current Linux default permissions to overwrite the entire MFT, or does Linux simply read the permissions that are already present in the MFT and interpret them in Linux terms?  And if I use chmod to change permissions on the NTFS drive, does Linux "do its best" to create the Windows-equivalent permissions in the MFT?  (I realize that I should be simply trying this out, but I really don't want to play games with any of valuable NTFS data right now.  Perhaps I can find an old drive to use for experimenting.)Since McDuck seems to be offline at the moment, I'll jump in and possibly confuse the issue. While I've disassembled the original FAT file system code from MS-DOS days, and learned the major differences for FAT32 (known to Linux as vfat), my knowledge of the internals of NTFS is limited to some semi-educated guesswork.

That said, I do know that Linux will never overwrite the MFT, although when it writes to an NTFS system it may have to modify a few entries. For many years, NTFS filesystems were only mounted in read-only mode because the Linux drivers of the day were not reliable in the MFT modification. However, for the past 6 years or more NTFS systems have been just as reliable as EXT2, 3, or 4.

What does happen is that when an NTFS filesystem is mounted, the driver establishes the Linux permissions for everything to the same set of NTFS permissions. This is controlled by the "options" parameter of the "mount" command or the /etc/fstab file. The default permissions, as I recall, are read-only and execute (even if the file is not executable!) and the file owner defaults to the user that mounted the file -- usually "root" since by default normal users cannot mount anything. However, options can be used to set read-write mode, and the user and group owner values.

These permissions, set at mount time, apply to every file and directory within the mounted system and cannot be changed. The "chmod" and "chown" commands do not work on NTFS systems -- and this often confuses newcomers. However there's a "remount" option to the mount command that you can use to change things if need be. I use it so often to make USB drives writeable that I've created an alias for it!

I hope this helps some... Keep asking questions and you'll find many of us eager to help.

---

### Post by Iggy64 on 2013-06-27
Thanks very much, JKyleOKC!  Your comments give me additional perspective on this situation.  Elsewhere on the internet I have read that:
[COLOR=#000000][FONT=arial]
[http://swerdna.dyndns.org/susentfs.html](http://swerdna.dyndns.org/susentfs.html)
[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][I]Permissions and Ownership on NTFS Partitions
[/I][/FONT][/COLOR]
*The NTFS filesystem does not support Linux permissions or ownership  per se. You can't successfully change ownership with the Linux command chown and you can't successfully change permissions with the Linux command chmod. Ownership and permissions are set only in the mount command.*
*The  permissions and ownership properties that are available for NTFS under  Linux are not written into the individual files to be retained when the  filesystem is unmounted or the computer is turned off. Permissions and  ownership obtained under Linux are temporary artifices imposed via the  mount command and maintained temporarily  by the operating system. They  are transient properties that last only until the NTFS partition is  unmounted.*

This pretty much mirrors what you have described.

What bugs me is that there is a great deal published about the "permissions" option for the mount command, and how it enables the per-file adjustment of permissions under ntfs-3g, and - according to some - even the use of chmod.  Here are a few examples:

[B][I]Access Handling and Security
[/I][/B]

[I]By default, files and directories are owned by the effective user and group of the mounting process and everybody has full read, write, execution and directory browsing permissions. You can also assign permissions to a single user by using the **uid** and/or the **gid** options together with the **umask,** or **fmask** and **dmask** options.

Doing so, Windows users have full access to the files created by ntfs-3g.

But, by setting the **permissions** option, you can benefit from the full ownership and permissions features as defined by POSIX. Moreover, by defining a Windows-to-Linux user mapping in the file **.NTFS-3G/UserMapping**, the ownerships and permissions are even applied to Windows users and conversely.
If **ntfs-3g** is set setuid-root then non-root users will be also able to mount volumes.
[/I][http://www.tuxera.com/community/ntfs-3g-manual/](http://www.tuxera.com/community/ntfs-3g-manual/)
 
 
***************
 
[I]**Why have chmod and chown no effect?**
By default files on NTFS are owned by root with full access to everyone. To get standard per-file protection you should mount with the &#8220;permissions&#8221; option. Moreover, if you want the permissions to be interoperable with a specific Windows configuration, you have to [map the users]("http://www.tuxera.com/community/ntfs-3g-advanced/ownership-and-permissions/#usermapping").
[/I][http://www.tuxera.com/community/ntfs-3g-faq/#permissions](http://www.tuxera.com/community/ntfs-3g-faq/#permissions)
 
**************
 
[B][I]STABLE Version 2009.11.14 (November 15, 2009)
[/I][/B]


[LIST]
[*]*New: Full file ownership and permissions support. The [ownership and permissions]("http://www.tuxera.com/community/ntfs-3g-advanced/ownership-and-permissions/") of files are interoperable with Windows and [conforms to the POSIX rules]("http://www.tuxera.com/community/posix-test-suite/").* 
[/LIST]
 
[http://www.tuxera.com/community/release-history/](http://www.tuxera.com/community/release-history/)



*****************

[I]**NTFS ONLY:**
You may now mount a ntfs partition with the "permissions" option. This options supports standard linux permissions on ntfs.
UUID=12102C02102CEB83 /media/windows ntfs-3g auto,users,permissions 0 0 [/I]
 
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

*************

[I]If you mount the ntfs partition with the permissions option, then chmod / chown will work
/dev/sda2   /mnt/excess ntfs-3g    permissions,locale=en_US.utf8    0   2
You can then 
sudo chown your_user:your_user /mnt/excess
Easier then uid,dmask,fmask[/I]
[http://askubuntu.com/questions/113733/how-do-i-correctly-mount-a-ntfs-partition-in-etc-fstab](http://askubuntu.com/questions/113733/how-do-i-correctly-mount-a-ntfs-partition-in-etc-fstab)

*********

So I am left wondering: Has something changed?  I guess probably not.  I'm probably misinterpreting what some of these citations are trying to say.  Or, maybe my options depend on how the NTFS file system was created in the first place.  I am clueless.

For now, I'm going to assume that the interpretation you (JKyleOKC) provided is correct.  After all, it will do everything I need in a tried-and-true fashion.

But, when I get the chance, I will find a spare hard drive, format it NTFS, pile on some files, and do some experimenting.  (I don't want to experiment using my existing NTFS drives, which contain valuable music files.)

Meanwhile, if someone knows the proper interpretation of the references I cited above - especially those from tuxera - I'd really like to hear it.

---

### Post by JKyleOKC on 2013-06-27
Your plan to experiment for yourself is undoubtedly the best way to find out, and if you report back with the results here it will be a help to everyone.

My initial reaction to these references was that there's a huge amount of simply incorrect information on the internet, but after seeing that some of them appear to be from changelogs for the ntfs-3g package -- which is the one that made writing to NTFS systems practical -- I'm inclined to believe that maybe things really have changed and my insistence that the Linux commands don't work is no longer correct! For instance, I hadn't been aware of the "permissions" option at all -- I use the UID and rw options to claim ownership and make the drive writeable. I'll have to do a bit of experimenting myself with a flash drive formatted as NTFS and see what happens...

It's good to see that you're double-checking all the data you come across, so you're already aware how much misinformation is circulating. We regulars here try to keep these forums cleaned out and as reliable as possible, but getting total reliability is simply not possible!

---

### Post by Iggy64 on 2013-06-27
Yes, there certainly is plenty of misinformation out there, on the internet and elsewhere.  Some of this is no doubt due to honest mistakes.  A good deal is also due to difficulties in fully explaining what is meant.  Especially when we are trying to keep things brief/concise, we assume that readers already know a certain amount of background, when many actually don't.  Misinterpretation often ensues.  I suppose that's the price we pay for keeping things manageable.  I was very skeptical about the postings that said chmod would work on NTFS.  But when I saw the information on the tuxera site regarding ntfs-3g, I started to waver a bit.  Unfortunately, that site says nothing about chmod; it only makes a somewhat vague statement about making greater use of the permissions in NTFS, with more granularity.  So the confusion continued.  

I'm keeping an open mind on this NTFS permissions business.  The method you currently use should certainly be sufficient for my present needs.  But there may well arise some situations where it would be nice to apply different permissions to different folders/files on an NTFS drive.  So I look forward to the experiments.

I sure do appreciated your giving this some thought.  You clearly have a lot more background in Linux, and may very well recognize the resolution well before I do.

Thanks much!

---

### Post by JKyleOKC on 2013-06-27
> **Iggy64 said:**
> You clearly have a lot more background in Linux, and may very well recognize the resolution well before I do.Well, I began on mainframes back around 1965, and got into personal machines fairly early in 1981. I avoided MS-DOS as long as I could, but finally got into it and immediately began delving into the system code itself -- which led to several books in the 90s. (FWIW, I've been retired since 1996 but like to say I'm 82 going on 22 mentally.)

I didn't get seriously into Linux until about six years ago, but my general background made it fairly easy to get up to speed in a hurry. I actually programmed on the system that inspired Unix, as far back as 1970-75, and many of the *nix commands are the same as they were on MULTICS while the main system concepts are almost identical. It didn't hurt that I spent almost 20 years as a tech writer working with the folk who designed and built most of Seagate's current hard drives, and I wrote the service manuals for several models, so I know what has to be present somewhere or other in any file system and its driver code.

I'm looking forward to the results of your experiments, and will be doing some of my own as soon as I get a few non-computer-related problems (that started with a leaky hot water heater and escalated from there) out of the way...

---

### Post by JKyleOKC on 2013-06-27
Okay, the plumbers have left and I hope all the problems are now corrected.

I re-formatted a spare 1-GB flash drive using "mkntfs" which is part of my 12.04 installation, then mounted it and added a couple of photos that I had on hand. I then used "ll" which is my alias for "ls -l" to show the ownership and permissions at that point, followed by a "chmod" command intended to change the permission of just one file on the drive to "rwx" for both group and other. You can see the result:
[CENTER][ATTACH=CONFIG]244220[/ATTACH][/CENTER]
Since this first attempt failed to make any change, I tried it again using "sudo" but got the same result -- chmod did nothing at all.

I didn't try mounting the drive using the "permissions" option; I simply mounted it automatically with my default values setting my own user ID and no permissions at all for group and other. These are mapped into the driver as I described previously, and as you can see did not change although "chmod" gave no error messages.

Next test will be to mount the drive using the "permissions" option if I can do so, and seeing whether that behaves differently, but it may be a few hours before I do it...

---

### Post by JKyleOKC on 2013-06-27
And here's the first test of using the permissions option. As you can see, it did exactly what those references said it would do. I put "UID" in uppercase rather than lowercase when mounting the drive, so it was ignored and the owner was set to "root" but the important part is that "chmod" did exactly what it was expected to do!
[CENTER][ATTACH=CONFIG]244223[/ATTACH][/CENTER]

The next test will be to take the drive to a Win8 machine and see whether the permissions stay at their new settings.

I've learned a lot in the past few hours; thank you, Iggy64, for starting such an interesting and educational thread!

---

### Post by Bashing-om on 2013-06-27
+1 ! ... Following with great interest ......
continue to monitor for educational expansion.
[INDENT][INDENT]still learning even after all these years[/INDENT][/INDENT]

---

### Post by JKyleOKC on 2013-06-27
The next chapter (but no screen shot this time)...

I took it to the Win8 machine and sure enough, the permissions remained just the way "chmod" had set them. While there, I changed the drive label (so that Xubuntu wouldn't use the drive serial number when mounting it). I then brought it back to the Xubuntu system, and the new drive label remained and took over its job of identifying the drive.

I discovered that Win8 had added a directory named "System Volume Information" to the drive, and this directory contained a single 96-byte file that contains binary data of some sort. So far I have no clear idea of what this is, but my best guess is that it contains metadata describing the drive itself.

All in all, I think using the "permissions" option is better than the way I've done things up to today, so I'll be changing my practice a bit...

---

### Post by Iggy64 on 2013-06-27
Well, JKyleOKC, I owe you another one.  Thanks for running those tests.  I wish I could have beat you to it, but I had a household emergency, just like you did.  My A/C died when a small animal crawled inside and got "exploded."  It took me a couple of sweaty hours to clean all the fur and guts out of the compressor cabinet.  When I got cleaned up, I tried to format a fresh USB stick as NTFS, but ran into some snags.  I need to read up on detail of how to create the NTFS on the stick.  That should be no big deal.

It's great to hear that this "permissions" option thing could be for real.  I would be able to use my precious music collections on my Linux box with more confidence.

Now I come full circle to the original question (of this thread).  When you change the permissions on the NTFS drive, where are they written?  This is a little more complicated than in the case of an ext4 drive, since the NTFS drive doesn't have inode tables per se, but instead a single MFT (or at least, so I believe).  It would be interesting to next see whether the chmod actually changes that MFT, so that the new permissions will persist after the drive is unmounted and then remounted.  The other possibility is that the new permissions are sort of "memorized" by Linux until the drive is dismounted (as is the case when you change the permisions with masks during mounting).  

I won't get a chance to play with this at all until tomorrow (Friday) evening after work.  

I really enjoy trying to figure out things like this.  The better I understand this OS, the better I will be able to use it.  And solving puzzles has always been fun for me.  I'm lucky to find a kindred spirit who is willing to help me with it.  Thanks very, very much for all this kind help and the great background lessons.

I hope to have something to chip in when I get back at it tomorrow.

---

### Post by Iggy64 on 2013-06-27
Wow.  By the time I wrote my apologies for not keeping up with you, you had already answered by new question.  It's great to hear that the chmod changes to an NTFS drive are persistent.  That means the behavior is fairly similar to that with an ext4 drive, and I won't have to reset the permissions every time I remount the drive(s).

The fact that the permissions are interpreted properly by a Win8 machine seems pretty solid evidence that the chmod has actually changed the MFT on the NTFS drive, right?

Again, you have my gratitude.  I may have taken me quite a while to fumble through this, at my level of expertise.  Now I have a better idea on how to approach it.  

If I learn anything new on the topic, I'll check back in and tack it on.

Have a great weekend!

---

### Post by JKyleOKC on 2013-06-27
> **Iggy64 said:**
> The fact that the permissions are interpreted properly by a Win8 machine seems pretty solid evidence that the chmod has actually changed the MFT on the NTFS drive, right?Seems that way to me. I used my wife's new Win8 machine for a couple of reasons: it was simpler than firing up one of my WinXP virtual machines, and I felt that if it would persist for Win8 it ought to persist for all the older NTFS systems.

Incidentally, I found a link on that Tuxera site you referenced earlier that tells a lot more about NTFS structure and the ntfs-3g driver package. It's over on the left side of the page that comes up on your link, titled "NTFS-3G MANUAL." I'm going to be studying it quite a bit, and I think you'll find it helpful in your own studies.

A good weekend to you, too!

EDIT: To format a drive as NTFS, I made sure it was recognized (as /dev/sdb on my system; it could be different on yours), unmounted it, then used "sudo mkntfs /dev/sdb1" with no options to get default cluster sizes and so on. The mkntfs program was already on my 12.04 system as part of the standard installation. It took several minutes to do the job; I left it running while dealing with non-computer errands. You can use "man mkntfs" to read the manual pages about the command and learn its options, but the defaults seem okay to me...

---

### Post by oldfred on 2013-06-28
I think somewhere you will find a thread where I linked to the NTFS permissions. But those that know a lot more suggested not to use it.

 New versions of NTFS-3g allow some permissions:Feb 1, 2012
[http://b.andre.pagesperso-orange.fr/permissions.html](http://b.andre.pagesperso-orange.fr/permissions.html)
But see comments by Morbius1 - post #11
[http://ubuntuforums.org/showthread.php?t=1979873](http://ubuntuforums.org/showthread.php?t=1979873)

---

### Post by Iggy64 on 2013-06-28
Yep, it worked for me, too.

I grabbed one of my precious music drives (NTFS) and mounted it using the permissions option.  I then used chmod to successfully change permissions individually and recursively on various files and directories, as reflected in ls -l.  

A few quick tests showed that when I switched permissions, they actually took effect; for example, I could not add files to protected directories.

According to your experience, the permissions created under ntfs-3g will persist after unmounting and then remounting on a Win8 machine.  From what I've read, you need to create a special user mapping file (see earlier post) in order to get nearly-complete interoperabilty of a NTFS drive between Linux and Windows.  I wonder if changes made under Windows will persist when opened in Linux.

A few more experiments to go, I guess.

However, my main goals for this thread have been met, thanks to all the great help.  I know where the inodes are stored on USB ext4 drives and now on USB NTFS drives.  And, even better, I know how to control the permissions on either type, which I wasn't at all certain could be done at the outset.  This is great stuff, since I was on the edge of giving up on trying to understand permissions under Linux.  They are powerful and comprehensive, but potential confusing and dangerous, if you don't understand what is going on (at least, in my opinion).  While I still have a lot to learn on the subject, I now feel comfortable enough to at least hook up my music and play it, without fear of unwanted writing to the files by some miscreant music software.  (Yes, I have backups; but who needs the aggravation?)

I may try messing with that user-mapping file, just to see how much interoperability I can achieve.  But this would be mostly for the education.  I don't have a lot of need for that capability right now.

I'll check back in here if I lean anything more that is relevant.

Thanks again for the help!!

---

### Post by Iggy64 on 2013-06-28
Well, it looks like - for the second time in a row - someone (this time oldfred) posted new info to the thread while I was writing my post.  And oldfred has provided some new references for me to study.

First of all, thanks very much for contributing more experiences to this discussion.  As I said, I am getting more comfortable with Linux permissions, but I very much realize I have much more to learn.

Secondly, perhaps the references you posted will teach me that using chmod on a USB NTFS drive is not a great idea.  I haven't read them yet, but I will do so sometime this evening when I can pay good attention.  I'll check back in then.

I mentioned early on in the thread that I have read greatly varying opinions (and, perhaps experiences) on whether one can use chmod on NTFS.  Some of the discrepancy may be due to what versions of ntfs-3g are being used by various people at the times (years) they posted.  Other differences may be due to the fact that some dug much deeper than I, and found that while it may APPEAR to work, there are problems.

So, I will continue to study, and then maybe test some more.  I'd rather be safe than sorry.

Thanks, again, for the info.

---

### Post by JKyleOKC on 2013-06-28
Very good! The problems that OldFred mentions are definitely connected with that user-mapping file, and the NTFS-3G Manual link that I mentioned goes into good detail about exactly what is involved in creating and maintaining one. To oversimplify, it's possible to accidentally create an "unknown user" at the Windows side, by making changes to the permissions via Linux. However if you're getting comfortable with the permissions jungle in both NTFS and POSIX, you'll be able to untangle this fairly easily should it rise up and bite.

I found that my test files, owned by "root" in Linux, are owned by the ADMINISTRATORS group in Windows, so had no problem at all. Had there been multiple user accounts present on both machines the outcome might have been different.

---

### Post by Iggy64 on 2013-06-28
Thanks for the continuing interest and help.  This is definitely easier to navigate with a knowledgeable guide.  I see what you mean about the oldfred links and the user mapping.  I had read earlier about the lack of complete correspondence between users in Linux and Windows NTFS; the groupings are simply not divided up the same way.  Thus the need for the mapping file.  As you said, with enough knowledge of this, I could probably swap the drives back and forth between Windows and Linux.

As it is, I will be using Linux almost full time.  But, if I should want to share one of the drives with a Windows-using friend, I think I'll be able to deal with it.

Thanks, again, for the support.

---

### Post by Iggy64 on 2013-06-30
Here we go again! I think I see another reason why there is considerable disagreement on whether chmod works with ntfs-3g. When I tried to make what I thought were "improvements" to the mount command, chmod stopped working for me.  It seems it is a bit fussy.

Recently, JKyleOKC and I were each successful in using chmod on a USB NTFS partition, when we mounted the partition this way:

> sudo mount /dev/sdb1 /media/usb -o permissions,UID=1000

However, I noticed that everything was owned by root root, despite the UID=1000 option. So I consulted the man page for mount, and learned that the mount options for NTFS include uid, gid, and umask (all lower case). I didn't see and UID option. Therefore, I modified the mount command to be:

> sudo mount /dev/sdb1 /media/usb -o permissions,uid=1000

Now the ownership came up john root, meaning I was now owner. So the uid option appeared to have worked. HOWEVER, now chmod would not work, whether I used sudo or not. What the heck?

Next, I tried dropping the UID option altogether:

> sudo mount /dev/sdb1 /media/usb -o permissions

Of course, ownership came out root root again. But chmod worked OK again.


OK. One more time ---------

I again used

> sudo mount /dev/sdb1 /media/usb -o permissions

and this time followed it with

> sudo chown -R john /media/usb

Now the ownership showed up as john root (as expected).

Now I was able to chmod successfully without sudo.

So it seems like you can't change ownership as part of the mount command and then use chmod. But you can change ownership AFTER the mount command, and chmod works OK. Yikes.

***************

On another matter, note that the mount commands here could have been written:


> sudo mount -t ntfs-3g /dev/sdb1 /media/usb -o permissions

That is, with the system-type option, which seems to be the preferred form. Without it, Linux reportedly takes its best shot at determining the drive's file system by comparing with items in a couple of configuration files. Apparently, this is working successfully in the examples I've run so far. I guess if I run into a snag, I can insert the -t option.

I also tried this idea:

> sudo mount -t ntfs-3g /dev/sdb1 /media/usb -o permissions,uid=1000

which again successfully made ownership john root, but chmod would not work at all.


Bottom Lines:

If I specify myself as owner when mounting the drive (uid=1000), ownership comes up as john root, but chmod will NOT work, even if I use sudo.

If I specify no owner when mounting the drive, ownership comes up root root, and chmod works OK if I use sudo.
If I subsequently use chown to change the ownership to me, I can run chmod successfully even without sudo.

I suspect that I lack knowledge of how to properly use the uid option (or the UID option, if there is one) in the mount command for NTFS systems. I spent several hours fiddling with this, without success.

Nevertheless, I am successfully using chmod to selectively change permissions on selected groups of files on a USB NTFS drive.

---

### Post by JKyleOKC on 2013-06-30
I think (but it's only a guess) that what you've demonstrated means that you've run into the user-mapping problem. Here's the scenario I envision: When you mount the drive with root owning it, the driver maps the ownership to the NTFS group ADMINISTRATORS, which always is able to change permissions. When you mount the drive to be owned by john (uid=1000) then the driver cannot find a matching Windows user, so maps ownership to an unknown guest, which has only read and execute permissions in NTFS. Without modify permission, no chang can be made.

If you want to test this you'll need to create that user mapping file; I've not carried my experiments that far, and since I don't have a convenient Win7/8 system to work with, don't plan to do so. However the results could be quite interesting and educational.

By the way, it's quite serendipitous that I goofed and put UID in caps for my initial experiment; had I not, the result would have been quite different and we might not have learned nearly as much as we have!

---

### Post by Iggy64 on 2013-06-30
Man, that is _excellent_!  I wouldn't have thought of that possiblity if I'd messed with it for a year.

I do have a Win7 machine available, so I could probably carry out the experiment.  I'll need some time for that, but it might be worth the education, as you say.  I can see situations down the road where I might want to share a drive with a Windows user, and it would be nice to properly protect the files on such a drive.  I'll read up on it some more, then check it out when time allows.

And boy, are you right: If not for the slight miscue on the UID option, you'd have gotten a negative result, and we might have given up, like a lot of other people probably did.  Now, we know how it can be done: First mount with permissions, then change ownership afterward.

If we can figure out the user mapping business, we might have the whole enchillada.

Thanks again for the continuing help.

---

### Post by JKyleOKC on 2013-06-30
Check out the permissions, on the Win7 side, for the file/folder that you did the chown for; if my guess is correct, it should now be owned (in Win7) by an unknown user, and may no longer be writeable from Win7! This, I believe, is the danger that we were warned about earlier.

Fortunately, we should be able to change it back from the Linux side if this has happened; I don't think it's a permanent disaster. You might even be able to change ownership back in Win7 when logged in as administrator rather than john...

---

### Post by Iggy64 on 2013-06-30
No chance to check the Win7 permissions today.  Will do as soon as machine available.

Meanwhile, will look into creating the mapping as suggested here:
[http://b.andre.pagesperso-orange.fr/usermap.html](http://b.andre.pagesperso-orange.fr/usermap.html)

It looks a bit intimidating for someone like me, who is more of a casual user than a guru.  I think I'll create a simple NTFS USB stick like you did, and then have a go.

---

### Post by Bashing-om on 2013-06-30
Iggy64; 
As you keep up the good work ... you will soon no longer classify yourself as a "casual user"... you have already come a long way !

Welcome to the club -> open source.
 I will revert back to lucking mode for my continuing edification !

[INDENT][INDENT]watch wait learn[/INDENT][/INDENT]

---

### Post by Iggy64 on 2013-06-30
Thanks very much for the kind words, Bashing-om.  Yes, I have learned a few things; but, in the process, I was somewhat intimidated by how much, much more I still needed to understand.  Luckily, I enjoy learning, so I will soldier on.  I wish I had more free time available for this, so it could come more quickly.  But I'm very grateful for this forum, which has made my education much more efficient.

---

