---
title: "Backup troubles"
date: 2007-07-05
forum: General Help
---

### Post by Ozor Mox on 2007-07-05
I've been trying to use a more sophisticated way of backing up than logging my changes to a text file and copying them across manually when I feel like it.

Attempt 1 - HUBackup

This is what the Ubuntu documentation suggests. I tried out backing up my home folder to my external hard drive, and it sat there for hours doing what appeared to be nothing at all ("preparing backup"), so I cancelled it and gave up.

Attempt 2 - rsync

I tried:

```
sudo rsync -av /home/me /media/disk
```

to copy my home folder to my external hard drive, formatted as FAT32 (so I can mount it on Linux and Windows systems). It got a short way through, and then bombed out, giving me some error message about not being able to write x bytes to the destination drive. While doing this it somehow managed to corrupt my external hard drive's filesystem and break my Ubuntu installation as well. On restarting to remount my hard drive, as I tried to log in I got the error (not exact):

```
GDM failed to write to your authorisation file. Your hard drive may be full, or some other reason that I can't remember. In any case, you could not be logged on.
```

And I was dumped back at the login screen. Bit worried now, cause both copies of all my files appeared to be borked, but I could still log in using the command line and rescued my files that way. For some reason, after deleting what remained on the external hard drive and restarting again, I could now log in without a problem.

Attempt 3 - rsync again

After revising my backup strategy (it's now always have two copies of my files in two different locations at any one time!), I tried again to see if it was a fluke. Same exact thing happened.

Attempt 4 - rsync again again!

This time I formatted my external hard drive to ext3 and tried rsync again. It worked perfectly.

Questions:

Is there some limitation of FAT32 that caused rsync to blow up when it got to a certain file? This did not happen when copying all my files manually to the drive. Did it maybe have to do with an automatic shutoff feature on my external drive after 5 minutes or whatever? Using rsync when it was ext3 seemed to be writing more stuff and maybe kept it "alive"... The drive is a Western Digital MyBook 250 GB by the way.

Is there a way I can make it work in FAT32? It works fine in ext3, and I imagine it's probably a better filesystem, but it's useful to be able to access my drive in Windows too.

Is there a reason why right clicking on my drive on the desktop and clicking eject results in "cannot unmount volume"? I'm sure it didn't do that before. Using umount in a terminal works ok, except I have to switch it off manually.

Thank you so much if anyone can help me.

---

### Post by njknight on 2007-07-05
There is a limit of 4.0Gb that can be transfered across to a fat32 file system - I encountered the same issue recently. rather than go the route of re-formating my external hard drive I simply split the output of (eg) my .tgz file then rejoin it with the cat command when required - all of which is well documented

best wishes

---

### Post by Ozor Mox on 2007-07-06
Thank you for your reply.

I always thought the 4 GB limit was for individual files... is it actually that you cannot transfer more than 4 GB at once, which would explain it falling over a short way in?

In either case, I have copied the whole lot across using Nautilus before, but maybe that works because it splits up the work unlike rsync?

I have since read that using rsync with FAT32 can be troublesome. It is working absolutely fine with ext3 now anyway.

My only remaining question is why I can't eject the darn thing! It switches off and then back on immediately saying "cannot unmount volume". I'm sure it used to work fine.

---

### Post by mannheim on 2007-07-06
The "-a" option to rsync tells rsync to do a bunch of things which really can't be done when the destination is FAT: eg, it tells rsync to preserve file permissions, preserve symlinks, preserve special files and device files, none of which make sense on FAT. 

If rsync really messes up, then that is a bad design in rsync; but you should really use ext3 or one of the linux alternatives instead of FAT if you want to preserve a good copy. If you really want to use FAT, then my guess is that you should give rsync different options -- maybe just "rsync -rtv ...", meaning "recurse into subdirectories, preserve timestamps, and be verbose".

---

### Post by Ozor Mox on 2007-07-09
Thanks mannheim.

I was thinking about this, and it has just suddenly come to me why that happened. I only had about 4 GB of free space on my laptop, and when I did

```
sudo rsync -av /home/me/Desktop/MyFolder /media/disk
```

the reason why it exploded after a short while was because it was copying files to that location on my internal hard drive and it ran out of space! Once I did

```
sudo rm -Rf MyFolder
```

when in the /media/disk location, all that stuff got deleted and I could log in again. Yes, I know rm -Rf was a bad idea, but I couldn't log in so I had to use the command line, and that was the only delete command I knew! I've since learnt to use rm -Rv instead.

Now, when rsync went wrong, my external hard drive was formatted as FAT32. I formatted it to ext3 and did the same command and it worked fine.

So...

1. If I'm located in /media/disk and I do

```
rm -Rf folder
```

to remove a folder located there, am I definitely only touching what's in /media/disk? I want to make sure nothing got deleted by accident, as I cancelled the operation soon afterwards after worrying that I couldn't see what was going on. (It did free up enough space for me to be able to log in though).

2. Why did rsync copy the files to my internal hard drive and run out of space when the external one was FAT32, but work absolutely fine now it's ext3? Is it some stupid FAT limitation to do with it having to copy everything to the mounted location and then on to the drive under FAT32 or something?

If I had had enough free space on the internal drive to duplicate everything, would the rsync to FAT32 have completed?

---

### Post by Ozor Mox on 2007-07-10
Bump. Anyone know whether I can use rsync to backup to FAT32 if I don't have enough space on my hard drive to duplicate everything? Would using rsync -rtv instead of rsync -av as mannheim suggested do the trick? (I will try this at some point soon, I'm just a bit wary of breaking my login again, I think I know how to fix it now though, I just wonder if -av really doesn't work with FAT32 at all)...

---

