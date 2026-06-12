---
title: "Partitioning Filesystem"
date: 2006-10-18
forum: General Help
---

### Post by morequarky on 2006-10-18
There are a lot of partitioning related threads on this forum.  Some questions relate to total novices who have never partitioned a hard drive before.  Other questions relate to what partitions they need from the given list during install.  Still others ask questions relating to partitions running out of space after creating a partition they might not really have needed without knowing what size to make it.  Then there are the few who have created some or many linux partitions and are about to re-install and want to know how to leave a particular partition from the previous install intact.

I would like to ask one more question. ](*,)  Why?  What is the benefit of having particular partitions?  From threads I have read, '/home' seems to be the only partition worth making outside of '/' because it is the easiest to include in a new install.

What went through the mind of the programmers when they decided to allow all these partitions?  The thought of testing just popped into my mind.  Perhaps testing was the reason.  If anyone could answer these questions I would appriciate the knowledge.

Thanks.  Great forum. Very helpful.

---

### Post by aysiu on 2006-10-18
In general, the idea of a separate partition is to preserve.

For most people, preserving /home is all they need.

Some, however, like to preserve /boot and /usr

It's your choice how many partitions you want. You don't even have to do a separate /home. You can just have one large / partition.

It's your choice.

It's your choice.

---

### Post by mssever on 2006-10-18
Multiple partitions are most meaningful in a server environment (where Linux started). Multiple partitions--especially if they're spread across several disks--can at times increase performance (due to disk I/O patterns), as well as easily manage more disk space than is available on a single disk. Of course, RAID can accomplish some of these, as well.

On the desktop, though, there probably isn't much advantage to multiple partitions, other than /home. In the old days, it was often necessary to have a separate /boot partition because BIOSes couldn't boot from large disks unless the boot files were before a certain cylindar. And if you dual-booted, creating a /boot partition was the only solution.

---

### Post by morequarky on 2006-10-18
I love choice, but what good does choice give me when I am not sure  I have enough knowledge to choose correctly?

Preserve.  That leads me to think of backups.  Couldn't a person backup '/home' or whatever even if it was in one large '/' partition?  If no back up is available and a re-install in in order, then having a separate /home makes some sense, but that doesn't work for other partitions so easily.

Wouldn't a RAID system be better for backing up  /var or /etc in a way that they would still be usable.  Just switch hard drives and boot the backup.  Most people don't have anymore then one hard drive making that great for servers but maybe not at all useful for the average joe.

Servers.  Maybe that is the golden ticket.  There is a benefit to servers that desktops don't need perhaps.

I guess it is possible to put each partition on a different hard drive but I don't see how that is going to be good for cash-strapped users.

Maybe you need to explain more?

Thanks.

---

### Post by morequarky on 2006-10-18
MSSever:

Thanks, maybe that starts to answer my question.

---

### Post by aysiu on 2006-10-18
> **morequarky said:**
> I love choice, but what good does choice give me when I am not sure  I have enough knowledge to choose correctly? Then you choose the default and have Ubuntu choose your partitions for you (if you do this, Ubuntu will create only a swap and / partition).

> 
Preserve.  That leads me to think of backups.  Couldn't a person backup '/home' or whatever even if it was in one large '/' partition?  If no back up is available and a re-install in in order, then having a separate /home makes some sense, but that doesn't work for other partitions so easily. Yes, you can back up /home, but that would make extra steps--back it up, then restore it. If you have a separate /home partition, you can do a reinstall and not have to "restore" /home--you just leave it alone.

But again... you have a choice. If you want to back up home, you can back up home.

> 
Wouldn't a RAID system be better for backing up  /var or /etc in a way that they would still be usable.  Just switch hard drives and boot the backup.  Most people don't have anymore then one hard drive making that great for servers but maybe not at all useful for the average joe. I don't know anything about RAID, but if you don't have more than one hard drive, I don't see how switching drives helps. That's where a separate partition comes in handy.

> I guess it is possible to put each partition on a different hard drive but I don't see how that is going to be good for cash-strapped users. What's the difference? Separate /home drive, separate /home partition. In the end, they serve the same purpose.

> 
Maybe you need to explain more? I think it's been explained.

Separate partitions are extremely handy for servers, not so much for desktop use. Still, a separate /home partition can be handy for desktop use. It all depends on what you want.

Personally, I have a / partition and a /documents partition. I don't like preserving /home because when I reinstall (I almost always reinstall when a new version of Ubuntu comes out--just want to see how the installer performs), I like to have fresh configuration files.

---

### Post by morequarky on 2006-10-18
Aysiu:  MSSever kind of put it in a nutshell for me while we were typing.

I remember you posting some stuff in another thread, you are very knowledgable.  Can you tell me how you have a /documents partition? How do you use it?  How did you set it up?

Thanks for your replies.  It seems clear that we don't need any extra partitions on a desktop install.  I currently have a '/boot', '/home', swap and '/'.  I probably don't need the '/boot' partition, but I had some trouble in the past so I thought I would have one this time around.  I love Ubuntu.  I am trying to get others to use it, honestly.  I tell'um like it is.  It is different and not perfect, but by far better then anything windows dishes out.

---

### Post by aysiu on 2006-10-18
Well my /documents partition is set up the same way any partition is (/boot, /home, /usr).

I just created a separate partition, dumped my stuff on there (music, photos, websites). And when I did the Ubuntu installation, I asked it to leave that partition alone and mount it at /documents.

Then I symlinked the folders inside of there to my /home folder and symlinked my Firefox and Thunderbird preferences from there as well.

In other words, /home/username/.mozilla on my computer is just a link to /documents/.mozilla

That way--as opposed to having a separate /home partition, only the config files that I *want* to bring over will be brought over.

Does that make sense?

---

### Post by morequarky on 2006-10-18
I think I got it.

---

### Post by paganini on 2006-10-18
Partitioning schemes are almost as religious as the choice of editor. :)

IMHO, you should create a partition for a given mount point when:

1) You want containment: If you have a system full of users, you want your users to have a separate /home from /. This would prevent system problems in case someone decides to fill up his/her home directory.

2) Special options: You may want to activate certain options on certain partitions, such as not allowing users to execute programs from their home directories, quotas, etc. Also, you may wait to mirror (RAID) specific partitions, or encrypt them. In these cases ,it may also make sense to have separate partitions for certain mount-points.

3) Data security: Even though it's rare, a bug in the filesystem would have less chance of corrupting the whole disk. Again, this is rare, and I don't believe it's a reason to have separate partitions in most cases.

So, the plan is:

If you know you'll have TONS of foreign users in your server, create /home as a partition. It may be a good idea to create /tmp and other system directories like /var as separate partitions as well. This should make it a bit harder for your users to "clog" the system.

If you know you'll use a large data partition (videos, music, etc), it may make sense to have it separate. This will allow you to mirror this partition more easily in the future. Note that it is still possible to mirror the whole thing, just a bit more complicated.

Some people prefer to create /boot under cylinder 1024. This is for historical reasons, but AFAIK, grub can handle anything, so it shouldn't be a problem.

If you are just putting together a workstation for your own use, I'd recommend a single filesystem / (with everything under it as directories) and a swap partition. This setup will maximize your disk space.

Regards
--Paga

---

### Post by mssever on 2006-10-18
I just thought of another reason to use multiple partitions: Using multiple filesystem types. For example, some filesystems are ideal for large files, while others are great for many small files. If you were trying to squeeze every ounce of performance out of your system, it might make sense to pick the best filesystem for a given directory based on expected usage.

---

### Post by morequarky on 2006-10-18
What files systems are best for small files and which is best for large files, like movies?

This is a very informative thread.

Thanks.

---

### Post by morequarky on 2006-10-18
Is reiser4 going to be added to debian linux kernel soon?  Is it the best available now?

---

### Post by mssever on 2006-10-18
> **morequarky said:**
> What files systems are best for small files and which is best for large files, like movies?

I haven't tried to do that kind of optimization, so I don't know. I use ext3 for everything.

---

### Post by FyreBrand on 2006-10-27
> **aysiu said:**
> Well my /documents partition is set up the same way any partition is (/boot, /home, /usr).

I just created a separate partition, dumped my stuff on there (music, photos, websites). And when I did the Ubuntu installation, I asked it to leave that partition alone and mount it at /documents.

Then I symlinked the folders inside of there to my /home folder and symlinked my Firefox and Thunderbird preferences from there as well.

In other words, /home/username/.mozilla on my computer is just a link to /documents/.mozilla

That way--as opposed to having a separate /home partition, only the config files that I *want* to bring over will be brought over.

Does that make sense?Do you still keep a separate /home partition or do you use both /home and /documents as mount points?  I'm sorry if I'm a bit dense I just want to be perfectly clear before I spend the time on this.

I like the idea of a /documents partition because I have a lot of pictures and a little bit of music.  I would rather not reload them all from archive everytime I nuke and would also like them separate from /home.

I've found your suggestion of a /home partition to particularly valuable and it has mitigated many problems.

I am not very familiar with symlinking so I will give this a whirl and see what I learn from it.

---

### Post by aysiu on 2006-10-27
I don't have a separate /home partition at all, just a separate /documents partition.

So /home is just a folder inside of my / partition.

Then I just create a symlink (or shortcut or alias) from the /documents partition to inside my /home folder.

For example, in /documents, I have a music folder and a pictures folder.

So I've symlinked it so that it looks as if there's /home/*username*/music, but that really just points to /documents/music, and it looks as if there's /home/*username*/pictures, but that really just points to /documents/pictures.

So none of my essential files live within the /home folder--they all just *appear* to live there--they really live on my /documents partition.

---

### Post by FyreBrand on 2006-10-27
Thanks for explaining that.  I find that quite amazing and interesting.  Symlinks in Linux seem so very seamless and quite powerful.

This is fun stuff.  I will check it out over the weekend.

Thanks again.

---

### Post by mssever on 2006-10-27
> **aysiu said:**
> I don't have a separate /home partition at all, just a separate /documents partition.

So /home is just a folder inside of my / partition.

Then I just create a symlink (or shortcut or alias) from the /documents partition to inside my /home folder.

For example, in /documents, I have a music folder and a pictures folder.

So I've symlinked it so that it looks as if there's /home/*username*/music, but that really just points to /documents/music, and it looks as if there's /home/*username*/pictures, but that really just points to /documents/pictures.

So none of my essential files live within the /home folder--they all just *appear* to live there--they really live on my /documents partition.
If I used a separate documents partition, I would simplify it even more by mounting it on /home/*username*/documents (I also have a separate /home partition, BTW); that way I wouldn't even have to symlink it. Remember, you can mount a partition pretty much wherever you want.

In my current setup, I symlink only the My Documents folder from my XP partition to ~/My Documents--but I rarely use this as I only boot into Windows once avery couple of months.

---

### Post by aysiu on 2006-10-27
> **mssever said:**
> If I used a separate documents partition, I would simplify it even more by mounting it on /home/*username*/documents (I also have a separate /home partition, BTW); that way I wouldn't even have to symlink it. Remember, you can mount a partition pretty much wherever you want.

In my current setup, I symlink only the My Documents folder from my XP partition to ~/My Documents--but I rarely use this as I only boot into Windows once avery couple of months.
I deliberately don't do that because I would rather have the folder hierarchy go /home/*username*/music than /home/*username*/documents/music

---

### Post by mssever on 2006-10-27
> **aysiu said:**
> I deliberately don't do that because I would rather have the folder hierarchy go /home/*username*/music than /home/*username*/documents/music

I see.

---

### Post by aysiu on 2006-10-27
> **mssever said:**
> I see.
Well, to each her own. That's just the way I do it.

---

### Post by MS_Prisoner on 2006-10-28
> **aysiu said:**
> Well, to each her own. That's just the way I do it.

I'm a total Linux noob. :KS  This is my first post. :mrgreen:  I'm thinking of dual booting via two hard drives.  I've read several threads describing how to do this...basically each hard drive will have its own OS (my plan).  One will be Windows XP and Ubuntu on the other. ](*,) 

Now, I have a 180GB for Ubuntu.  Aysiu, I like the idea of having a separate "/documents" partition and symlinking the data.  So from what I read so far (favoring Aysiu's structure), it appears that three partitions are ideal, "/" partition,"/documents" partition and "/swap" partition.

I read that the recommend /swap partition size is ~2.5 times the system's RAM.  The rest will be dedicated to the "/" and "/documents" partition.

To the questions:
- What partition size do you recommend for "/"?  I want to make this big enough so that I can replace the OS that reside in this "/" partition with any Linux OS.  For example, I'm installing Dapper (currently more stable IMO)...later on I want to do a fresh install over Dapper with Edgy (not an upgrade but fresh new install).

- Is this three partition structure good enough?  Will this protect me from losing my important files (pictures, music, documents...etc)?  Well, of course if the HD fails...I'm screwed.  All else, I should be ok, right?

Thank you for your time! 8)

---

### Post by morequarky on 2006-10-28
'/' should be about 20Gigs or so, depending on how much extra stuff you install.
Your not making a /home partition?  I would.  

Put your "documents" in /documents.
When you reinstall, don't 'format' your '/documents'.
If you have a /home partition, don't 'format' that either.
whatever holds your largest files like videos and pictures should be your largest partition.

---

### Post by aysiu on 2006-10-28
I don't think you'll need more than 6 GB (I currently use 3.5 GB) for your / partition, but since your hard drive is 180 GB, it probably couldn't hurt to go with morequarky's recommendation of 20 GB for /

The rest you can dedicate to /documents, as your personal files will probably take up the rest of the room on your hard drive.

By the way, swap is supposed to be 1.5 times your RAM, as far as I know. If you have over 1 GB of RAM, you probably don't even need it to be that large.

---

### Post by galileon on 2006-10-28
> **morequarky said:**
> What files systems are best for small files and which is best for large files, like movies?

This is a very informative thread.

Thanks.

reiser is supposed to be good with small files, but i didnt like reiser because it takes ages to mount (and at one point, i had about 6-8 reiser partitions to mount at boot, which made my boot time painfully long)

now i use ext3 for everything, because its got journaling, which means it survives a crash without scandisk (though it does fschck once every 30 or so boot, but that can be fine tuned if you want to)

i used to have an ext2 for /tmp, and i planned to copy video files there when I watch them, but i found it was pointless, ext3 is really fast on most modern hard disks...

you might want to have an ext2 if you do video editing though, it should make a difference i think - if anyone tests it, please let us know...

---

### Post by galileon on 2006-10-28
> **MS_Prisoner said:**
> I'm a total Linux noob. :KS  This is my first post. :mrgreen:  I'm thinking of dual booting via two hard drives.  I've read several threads describing how to do this...basically each hard drive will have its own OS (my plan).  One will be Windows XP and Ubuntu on the other. ](*,) 

Now, I have a 180GB for Ubuntu.  Aysiu, I like the idea of having a separate "/documents" partition and symlinking the data.  So from what I read so far (favoring Aysiu's structure), it appears that three partitions are ideal, "/" partition,"/documents" partition and "/swap" partition.

I read that the recommend /swap partition size is ~2.5 times the system's RAM.  The rest will be dedicated to the "/" and "/documents" partition.

To the questions:
- What partition size do you recommend for "/"?  I want to make this big enough so that I can replace the OS that reside in this "/" partition with any Linux OS.  For example, I'm installing Dapper (currently more stable IMO)...later on I want to do a fresh install over Dapper with Edgy (not an upgrade but fresh new install).

- Is this three partition structure good enough?  Will this protect me from losing my important files (pictures, music, documents...etc)?  Well, of course if the HD fails...I'm screwed.  All else, I should be ok, right?

Thank you for your time! 8)

i like to have a 20 gig / so that i dont have to worry about space when installing loads of programs (which i dont really use, but hey its fun to try out things!) 

things that tend to baloon out: /var, if you use vmware and use the default place to save your virtual machines, /home, where your personal files live

/var/cache/apt/archive also tends to get heavy after I've been installing and removing software, because its got the .deb files for the programs i install

what i like to do is to make a folder in my /data (equivalent to /document in the present discussion) and link 
/var/cache/apt/archive to /data/apt-archive

---

### Post by MS_Prisoner on 2006-10-28
Thanks for the reply y'all!

> **aysiu said:**
> I don't think you'll need more than 6 GB (I currently use 3.5 GB) for your / partition, but since your hard drive is 180 GB, it probably couldn't hurt to go with morequarky's recommendation of 20 GB for /

The rest you can dedicate to /documents, as your personal files will probably take up the rest of the room on your hard drive.

By the way, swap is supposed to be 1.5 times your RAM, as far as I know. If you have over 1 GB of RAM, you probably don't even need it to be that large.

As it turns out, my first system has 180GB while the other has only 60GB spare. :-\"  I plan to install it in my old system (60GB).  Maybe later I'll convert my new one(180GB).  So here are my future partitions in the 60GB system (in this order):

/ - 8GB (so I can have a small room to try out some applications, like Galileon said)
/documents - 50.5GB (for my personal files and some application settings[e.g. profiles])
/swap - 1.5GB (~2 times my 640MB RAM)

This should be sufficient right?  I'm new to Linux so I don't think I'll fill up the "/" partition anytime soon.  Although, I'll keep this in mind:

> **galileon said:**
> 
what i like to do is to make a folder in my /data (equivalent to /document in the present discussion) and link 
/var/cache/apt/archive to /data/apt-archive

If I ever need more space than 8GB, I should be able to symlinked folders between "/" partition and "/documents" partition.  This should be ok right?

I need your expert blessings before I begin.  What do you think? :mrgreen:

Thanks again. 8)

---

### Post by galileon on 2006-10-28
looks good to me, and the /apt/archive thingy helps if you want to nuke the / and start over - you dont have to wait for the packages to download again

---

### Post by morequarky on 2006-10-28
> / - 8GB (so I can have a small room to try out some applications, like Galileon said)
/documents - 50.5GB (for my personal files and some application settings[e.g. profiles])
/swap - 1.5GB (~2 times my 640MB RAM)


Your mention of "profiles" worries me.  Your profile will be in /home, NOT /documents.

---

### Post by MS_Prisoner on 2006-10-28
> **morequarky said:**
> Your mention of "profiles" worries me.  Your profile will be in /home, NOT /documents.

I haven't tried it yet but I will try storing my Firefox and Thunderbird profiles in my /documents partition.  I will then create a symlink of the profile's location in /home (which is located in the "/" partition).

This way, I can protect some of my "personal" application files.  If "/" partition ever gets corrupted, my settings are still ok.

Well, this is all theoretical to me...I'll try this when my Ubuntu OS is up.

---

### Post by handy on 2006-10-28
In my recent install of **Edgy RC1**, I created **/var** partition & also moved my **/swap** to the same separate drive, a completely different disk to the **/**. The **/** partition on my machine is **9.77Gig** in size & only uses **2.17Gig** of that!

I already had a separate **/home** drive, which by the way makes doing a clean install so much  quicker & easier.

I did not really need to make the 3Gig **/var** partition, for my machine is not used by anyone else & is really no server, I just did it for fun. I really don't need a **/swap** at all probably as there is 2 Gig of ram on the machine.  Having **/swap** on a separate drive to **/** will speed up a system that actually uses **/swap** though.

I guess the bottom line of this lot is that if you prefer to do a clean install when you upgrade Ubuntu, having a separate **/home** partition really streamlines the process.  Unlike **Aysiu**, I don't have a use for the knowledge gained from a **totally** clean install.

---

### Post by craft47 on 2006-11-06
I recently did a new install of Dapper, previously I had Hoary, but a failed update for firefox screwed up my wireless and a few other things, so I decided it was time for a newer version.  
I wanted to leave my /home partition alone, so I chose manual partitioning.  I resized my / partition (hda6), left my swap partion (hda5) as it was and then I was left with my /home partition (hda7) and a newly created partition that I didn't name, but formatted as hda8.  After the install, I found that my Windows XP partition (hda1) is mounted as /media/hda1 (that's ok I guess) and the new partition is mounted as /media/hda8, and my /home partition shows up as /media/hda7/home!  When I try to open my Home Folder from the taskbar, I get my 'username' folder, but not the one that I had on /home/'username'.  I'm wondering what I've done wrong.  I'm sure I set the mount point for my old /home partition correctly.  Anyone had this happen to them?

---

### Post by galileon on 2006-11-06
> **craft47 said:**
> I recently did a new install of Dapper, previously I had Hoary, but a failed update for firefox screwed up my wireless and a few other things, so I decided it was time for a newer version.  
I wanted to leave my /home partition alone, so I chose manual partitioning.  I resized my / partition (hda6), left my swap partion (hda5) as it was and then I was left with my /home partition (hda7) and a newly created partition that I didn't name, but formatted as hda8.  After the install, I found that my Windows XP partition (hda1) is mounted as /media/hda1 (that's ok I guess) and the new partition is mounted as /media/hda8, and my /home partition shows up as /media/hda7/home!  When I try to open my Home Folder from the taskbar, I get my 'username' folder, but not the one that I had on /home/'username'.  I'm wondering what I've done wrong.  I'm sure I set the mount point for my old /home partition correctly.  Anyone had this happen to them?

hello, please post your /etc/fstab, we'll tell you which lines to change...

---

### Post by craft47 on 2006-11-07
> **galileon said:**
> hello, please post your /etc/fstab, we'll tell you which lines to change...

Thank you!  I'm on nightshift right now, but will try to check it in the morning and post it here.:)

---

### Post by craft47 on 2006-11-07
here is my /etc/fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda6       /               reiserfs notail          0       1
/dev/hda1       /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hda7       /media/hda7     reiserfs defaults        0       2
/dev/hda8       /media/hda8     reiserfs defaults        0       2
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by galileon on 2006-11-07
please read the bit at the end of this post BEFORE you try anything!!
---------------------
ok, make a backup of your current fstab, thus:

sudo cp /etc/fstab /etc/fstab.backup


if things go wrong, then do this:

sudo rm /etc/fstab
sudo cp /etc/fstab.backup /etc/fstab


-------------------------------------------------

now lets modify the fstab:

we want /dev/hda7 to be mounted at /home, right? therefore change this line:
/dev/hda7 /media/hda7 reiserfs defaults 0 2

into this:
/dev/hda7 /home reiserfs defaults 0 2

this may create problems with your configuration files (the hidden ones in your /home/username/) because of the upgrade in OS....you might want to copy them into /media/hda7/username BEFORE you do any of the above...

---

### Post by mssever on 2006-11-07
Additionally, before doing the above, you should backup everything in /home and then delete everything from /home so that /home is just an empty directory. Once you mount another partition on /home, the previous contents will become inaccessable, so there's no sense wasting disk space.

---

### Post by craft47 on 2006-11-07
> **galileon said:**
> please read the bit at the end of this post BEFORE you try anything!!
---------------------
ok, make a backup of your current fstab, thus:

sudo cp /etc/fstab /etc/fstab.backup


if things go wrong, then do this:

sudo rm /etc/fstab
sudo cp /etc/fstab.backup /etc/fstab


-------------------------------------------------

now lets modify the fstab:

we want /dev/hda7 to be mounted at /home, right? therefore change this line:
/dev/hda7 /media/hda7 reiserfs defaults 0 2

into this:
/dev/hda7 /home reiserfs defaults 0 2

this may create problems with your configuration files (the hidden ones in your /home/username/) because of the upgrade in OS....you might want to copy them into /media/hda7/username BEFORE you do any of the above...


Ok, this is what I thought I might have to do.  But I don't understand why it happened in the first place.  I have, in the past, used the same /home partition for multiple distributions of Linux and never had it mounted in this way (/media....).  I haven't done anything with this new install except to config my wireless adapter, so I was thinking of just reinstalling before going any further.  What I wondered was, is it something to do with Ubuntu, or should I just pay more attention when I do the install and make sure that /home is integrated into the new filesystem? Am I making sense?  I have always used a separate partition for /home and never had this problem. Do you think reinstalling would change anything, or is this just the way it's gonna be no matter what I try?  I mean Ubuntu did create a /home/username file under / , but I want my original /home/username file under root.  Maybe I could replace the /home/username with /media/hda7/home/username? Or link it somehow?  hmmmm, gotta go to work anyway, nightshift again, but let me know what you think and TIA for all your help! You are all :KS :KS :KS

---

### Post by galileon on 2006-11-08
it asks you about where to mount filesystems just after partitioning...maybe you missed it...

yes you can link... to do it,

1st backup those pesky .hidden files and folders in /home/username now,

then sudo rm /home/username

sudo ln -s /media/sda7/home /home/username

copy back these .hidden files into the folder (/media/sda7/home or /home/username, its the same now) - thats what i usually did....(right now my system is a nightmare of links and cross links, that i lost myself, lol)

---

### Post by mssever on 2006-11-08
> **craft47 said:**
> Ok, this is what I thought I might have to do.  But I don't understand why it happened in the first place.  I have, in the past, used the same /home partition for multiple distributions of Linux and never had it mounted in this way (/media....).  I haven't done anything with this new install except to config my wireless adapter, so I was thinking of just reinstalling before going any further.  What I wondered was, is it something to do with Ubuntu, or should I just pay more attention when I do the install and make sure that /home is integrated into the new filesystem? Am I making sense?  I have always used a separate partition for /home and never had this problem. Do you think reinstalling would change anything, or is this just the way it's gonna be no matter what I try?  I mean Ubuntu did create a /home/username file under / , but I want my original /home/username file under root.  Maybe I could replace the /home/username with /media/hda7/home/username? Or link it somehow?  hmmmm, gotta go to work anyway, nightshift again, but let me know what you think and TIA for all your help! You are all :KS :KS :KS
I use a separate /home partition, and I've had no problems with Ubuntu's setup. During install, I always choose the manual partition option. Then I specify a partition to be mounted on /home.

I recommend backing up /home/username somewhere, deleting everything in /home, and changing the /dev/hda7 line in /etc/fstab to point to /home instead of /media/hda7. Then reboot.

---

### Post by craft47 on 2006-11-08
> **galileon said:**
> it asks you about where to mount filesystems just after partitioning...maybe you missed it...



Yes, of course it did](*,) I must have been trying to install in my sleep.  I've fixed it now with a re-install since I hadn't used the new system yet.  All is well so far, just need to get back a few favourite apps like aMorak (sp?) and Kaffeine and fix my sound the way it used to be!

Thank you all for your help and advice.:)

---

