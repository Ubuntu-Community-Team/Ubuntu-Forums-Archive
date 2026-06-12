---
title: "Very long (1+ wk, 20%) fsck.ext4"
date: 2012-11-30
forum: General Help
---

### Post by Die Mensch-Maschine on 2012-11-30
Hi,

On 10.04.4 LTS.

My backup server was improperly shut down due to power failure. However, at that time, backups were turned off.

When turned back on, an automatic fsck was launched on a disk (first one since creation, ~300 days ago). After three days, because no progress was advertised, I killed it by pressing C.

After a second killed fsck (I had to physically move the box and thus reboot again), a third one was launched manually.

```
sudo umount /backup/
sudo fsck -p -V /backup/
```

That was more than one week ago. fsck.ext4 progress bar reports 20% progress.

Unfortunately, I put a -V flag instead of a -v (man fsck is confusing on that point). I had to send a SIGUSR1 to fsck.ext4 to get a progress bar, but progress information is otherwise minimal.

The disk is 6TB, ext4, a physically RAID 0 on an Adaptec 5805 controller with a layer of LVM. As it is a backup server and copy is preserved everyday, many files are hard linked ~300 times. The box has 3GB RAM.

Why does it take so long? Should I expect trouble? Any idea what could speed up the process, either this time or next time?

Aslo, what filesystem would you suggest for my next backup server to avoid such issue?

---

### Post by rnerwein on 2012-11-30
> **Die Mensch-Maschine said:**
> Hi,

On 10.04.4 LTS.

My backup server was improperly shut down due to power failure. However, at that time, backups were turned off.

When turned back on, an automatic fsck was launched on a disk (first one since creation, ~300 days ago). After three days, because no progress was advertised, I killed it by pressing C.

After a second killed fsck (I had to physically move the box and thus reboot again), a third one was launched manually.

```
sudo umount /backup/
sudo fsck -p -V /backup/
```That was more than one week ago. fsck.ext4 progress bar reports 20% progress.

Unfortunately, I put a -V flag instead of a -v (man fsck is confusing on that point). I had to send a SIGUSR1 to fsck.ext4 to get a progress bar, but progress information is otherwise minimal.

The disk is 6TB, ext4, a physically RAID 0 on an Adaptec 5805 controller with a layer of LVM. As it is a backup server and copy is preserved everyday, many files are hard linked ~300 times. The box has 3GB RAM.

Why does it take so long? Should I expect trouble? Any idea what could speed up the process, either this time or next time?

Aslo, what filesystem would you suggest for my next backup server to avoid such issue?
oh i think there is something going the wrong street. 
1. are some error message ( multi of them) in /var/log
2.  question to you is: did the %  grow up or stay at 20% ?
3. what size are the files on /backup ( a mean the number of files) - you can guess that by using: df -i /backup
4. what is the load on that system 
5. is the system swaping (not enough freemem)

if the backup was switched off when the power failed the fsck have to run even no traffic is on that file system. because the "filsystem is clear bit" isn't set on power fail

---

### Post by Die Mensch-Maschine on 2012-11-30
> **rnerwein said:**
> oh i think there is something going the wrong street. 
1. are some error message ( multi of them) in /var/log“Nothing is logged yet” in every file inside /var/log/fsck.
> **rnerwein said:**
> 2.  question to you is: did the %  grow up or stay at 20% ?
The process is still running, albeit slowly. From 20.5% when I opened the thread to 20.7% as I write this.
> **rnerwein said:**
> 3. what size are the files on /backup ( a mean the number of files) - you can guess that by using: df -i /backupShould I run df while a fsck is running? Anyway, the file server contains ~2M files, so I guess that would be ~2M files on the backup server and ~600M hard links.
> **rnerwein said:**
> 4. what is the load on that system A little under 1.1 (2 processors)
> **rnerwein said:**
> 5. is the system swaping (not enough freemem)Yes, darnit. Around 1GB of swap for fsck.

Is it worth it to interrupt it and run it again with scratch files?

> **rnerwein said:**
> if the backup was switched off when the power failed the fsck have to run even no traffic is on that file system. because the "filsystem is clear bit" isn't set on power failYes, but serious fs corruption seems less likely.

---

### Post by rnerwein on 2012-12-01
> **Die Mensch-Maschine said:**
> &#8220;Nothing is logged yet&#8221; in every file inside /var/log/fsck.

The process is still running, albeit slowly. From 20.5% when I opened the thread to 20.7% as I write this.
Should I run df while a fsck is running? Anyway, the file server contains ~2M files, so I guess that would be ~2M files on the backup server and ~600M hard links.
A little under 1.1 (2 processors)
Yes, darnit. Around 1GB of swap for fsck.

Is it worth it to interrupt it and run it again with scratch files?

Yes, but serious fs corruption seems less likely.

sorry in your post i can see nothing where i can help you (do you speak german ?)
but my assumption is it has something to do with that millions of hard links.
your "df -i" must show only about 2 Mio. used inodes. 
my stomage tells me that is the direction where to look - but this is development stuff.
which version of ubuntu and ext4 are you running ?
cheers

P.S. if you have a nerv (absolutely no action on the fs) you can use the command tune2fs.
tune2fs -E  clear_mmp
                          Reset the MMP block  (if  any)  back  to  the  clean
                          state.  Use only if absolutely certain the device is
                          not currently mounted  or  being  fscked,  or  major
                          filesystem corruption can result.  Needs '-f'.
 and have a look at the manpages for tune2fs -->  -c or -C

---

### Post by Die Mensch-Maschine on 2012-12-01
> **rnerwein said:**
> sorry in your post i can see nothing where i can help you (do you speak german ?)Nope. I do speak French, though, if that is somehow easier for you.

> **rnerwein said:**
> but my assumption is it has something to do with that millions of hard links.
your "df -i" must show only about 2 Mio. used inodes. 
my stomage tells me that is the direction where to look - but this is development stuff.
which version of ubuntu and ext4 are you running ?
cheers

Ubuntu 10.04.4, kernel 2.6.32-45-server. Not sure what you mean by ext4 version or how to get it, but e2fsck and the EXT2FS library are 1.41.11.

> **rnerwein said:**
> P.S. if you have a nerv (absolutely no action on the fs) you can use the command tune2fs.
tune2fs -E  clear_mmp
                          Reset the MMP block  (if  any)  back  to  the  clean
                          state.  Use only if absolutely certain the device is
                          not currently mounted  or  being  fscked,  or  major
                          filesystem corruption can result.  Needs '-f'.
 and have a look at the manpages for tune2fs -->  -c or -CMmmh, that sounds like a bad idea.

Oh, and before I forget, thanks to everyone for the awesome support and to you in particular for your help in this very case.

---

### Post by Die Mensch-Maschine on 2012-12-09
Ok, I’ve located the issue. It was between the screen and the keyboard.

A while ago, I had to check RAID on this system and e2fsck failed on lack of memory. Hence, I set up e2fsck to use scratch files. And I forgot to turn it off after that.

Now that it is off, fsck runs in a few hours. You may call me an idiot.

---

### Post by Cheesemill on 2012-12-09
> **Die Mensch-Maschine said:**
> Ok, I’ve located the issue. It was between the screen and the keyboard.
Isn't that usually the case :)

---

