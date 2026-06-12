---
title: "rsync bass ackwards"
date: 2013-02-18
forum: General Help
---

### Post by Langstracht on 2013-02-18
I would like to get "all" my files on an external hard drive so that I can change machines and still have access to everything.

Being prudent, I would also like to back all this data up.  But I would just as well NOT buy a second drive.

So!  Can I back up the HD to a computer.  Perhaps even alternately to the two machines I principally use.

So the question is, can rsync back up FROM an external drive to a computer? And, if so, how?  Or can perhaps BackinTime do so.

Thanks in anticipation of some needed hand holding.

---

### Post by sudodus on 2013-02-18
The short answer is yes, between drives in the same computer and between computers.

Have a look at ```
man rsync
``` which is well written and contains examples. You need not learn it by heart or do everything on your own, so come back after looking at that text.

Rsync is normally using ssh, so you need to have the ssh server installed in the 'other' computer(s).

See [[COLOR="Red"]https://help.ubuntu.com/community/SSH/OpenSSH/Configuring[/COLOR]]("https://help.ubuntu.com/community/SSH/OpenSSH/Configuring")

---

### Post by Langstracht on 2013-02-18
Thanks for your prompt reply.

You've certainly given me a bunch of reading which I will try to plough through.

That said, and just for clarity (in case I wasn't clear "last time"), I want to back up an external HD on either of two computers.

Your reply said "drives in the same computer and between computers".  Which is not the same.  At the risk of being persnickety, I CAN do what I want.  Right?

I suppose once the command is defined it becomes a no brainer, but I noticed you avoided talking about BackInTime.  Does that mean BackInTime will not do what I want?  Or are you perhaps not familiar with it?  Or prefer rsync?

All of that said, I reckon to get this to work I will need MAJOR hand holding.  So rest assured, after I've tried to assimilate man, I WILL post.

Again, many thanks.

---

### Post by sudodus on 2013-02-19
> **Langstracht said:**
> 
That said, and just for clarity (in case I wasn't clear "last time"), I want to back up an external HD on either of two computers.

Your reply said "drives in the same computer and between computers".  Which is not the same.  At the risk of being persnickety, I CAN do what I want.  Right?

When an external drive is mounted it is treated by rsync in the same way as an internal drive. So the answer is yes. It might be a good idea to mount it by an entry in /etc/fstab, or to add a label to it, so that it will always be mounted to the same mount-point.
> 
I suppose once the command is defined it becomes a no brainer, but I noticed you avoided talking about BackInTime.  Does that mean BackInTime will not do what I want?  Or are you perhaps not familiar with it?  Or prefer rsync?

I am not familiar with BackInTime. There are many front-end programs for rsync (and other backup programs too). Please describe what kind of backup you want: complete system backup, incremental backup, synchronizing (also deleting from the backup) ...
> 
All of that said, I reckon to get this to work I will need MAJOR hand holding.  So rest assured, after I've tried to assimilate man, I WILL post.
Again, many thanks.
I use rsync as it is sometimes. But I also use Clonezilla to make complete images of whole drives or partitions, and I use Unison to backup by synchronzing my photo and multimedia partition.

---

### Post by kurt18947 on 2013-02-19
When I do what I think the O.P. is trying to do, I find it useful to synchronize two folders.   I can have the same contents on 2 machines and an external drive.  To accomplish this in Ubuntu, I find lucky backup the most intuitive GUI to use.  I can either backup a folder or synchronize it.  I didn't find Grsync or Unison as intuitive when trying to synchronize folders on local drives.

---

### Post by Langstracht on 2013-02-19
Sorry I haven't figured out (nor can I find) how to selectively quote from other replies.

That said, thanks for both of your replies.

I think I want basically everything in the home folder.  Although if there is some reason that I should not get that please speak up.

That said the present size (of the home folder) is about 50 Gig.  And the machine drives better than double that (they're partioned for a dual boot).  The external 10x.

So!  My thinking is keep "everything" on the external - i.e. no deletions.  BUT squirrel away (archive if you will) some stuff and NOT copy it (the archived) over (back it up) to the 2 machines.  

Again, please, if that don't make sense, please say so.

As for mtg - again a place of blissful ignorance for me.  Guess I'll need to do some more reading/exploring.

Continue to appreciate your involvements in this.

---

### Post by kurt18947 on 2013-02-19
50 GB. of data in your home folder?   Perhaps create an archives folder and an active folder?  Then you'd only need to synchronize the active folder?  There's likely a way to sort files by the date last accessed.  If a file hasn't been accessed in so many days, move it to the archives folder.  If a file in the archives is modified, it moves to the active folder until it's been inactive for so many days then back to archives.   I have not done this but it seems feasible.

---

### Post by sudodus on 2013-02-19
50 GB in the home partition or is it a home folder in the root partition)?

If separate partitions I guess the root partition contains less than 10 GB. Or do you have a lot of program packages installed?

I would suggest that you have different sets of backup.

1. Complete backup of the whole Ubuntu system or the whole drive

Do this seldom, maybe 2-4 times a year, or when you make major changes (for example upgrade to a new Ubuntu version). Keep two backup versions (the two newest ones). Use a Clonezilla boot CD or USB drive and make compressed images. Many files will be easily compressed. But photos and multimedia files are already compressed, and it might be a good idea to keep them separated from this imaging process, for example keep them in an own partition.

2. Incremental or synchronizing backup of the home directory

You can use rsync or some GUI application for this task. The advantage with incremental backup is that some file that was deleted by mistake will be saved. The advantage with synchronizing is that the system will be clean after restoration (no obsolete files will be there that might cause problems).

3. Incremental or synchronizing backup of photos and multimedia files

Maybe you can include other big compressed files to this group of files. You can use rsync or some GUI application for this task. I like Unison for this task, because at each sync there are a limited number of changes, and quite easy to see which way to go (if old files should be kept or wiped). But there are several tools, and you should test a few tools to find what suits you the best.

This method will automatically cater for the 'archived files'. What was your idea with those files? To keep them in the computer without backup and accept if they are lost in a disk crash, or to keep 'only backups' of them? In that case I would suggest the latter method, and to have some kind of manual incremental backup to the 'archive', where you move files or directories ( I mean delete from the original place after copying).

---

### Post by kjohri on 2013-02-20
Once an external drive is connected (mounted) on a computer, you can copy files using rsync in either direction. That is from the local hard disk of the computer to external drive and vice-versa. 

The same applied when you connect the external drive with the second computer. You can copy files using rsync in either direction - external drive to local hard disk and vice versa.

You can look at the following rsync tutorial,

[http://www.softprayog.in/tutorials/rsync](http://www.softprayog.in/tutorials/rsync)

---

### Post by Langstracht on 2013-02-21
Thanks to kjohri for the tutuorial link.  Most helpful.

As to the questions.  Yes 50 Gig.  And yes lots of programmes ... but also images, sound and video files.  All ubuntu is in one partition.  So I guess it is a home folder in the root partition.  

However something else has come up that I don't quite understand.  Is not a bunch of files on an external hard drive equivalent (or indeed better) than them being in a separate partition on the same drive as the o/s?  Sort of like a belt and suspenders ...

Once I get it figured out how to 'rsync' I'll see what I can do about taking your advice on the various backups.  Thanks for sharing the expertise.

---

### Post by sudodus on 2013-02-21
> **Langstracht said:**
> Thanks to kjohri for the tutuorial link.  Most helpful.

As to the questions.  Yes 50 Gig.  And yes lots of programmes ... but also images, sound and video files.  All ubuntu is in one partition.  So I guess it is a home folder in the root partition.  

However something else has come up that I don't quite understand.  [COLOR="Red"]Is not a bunch of files on an external hard drive equivalent (or indeed better) than them being in a separate partition on the same drive as the o/s?  Sort of like a belt and suspenders ...[/COLOR]

Once I get it figured out how to 'rsync' I'll see what I can do about taking your advice on the various backups.  Thanks for sharing the expertise.
It is OK to have your system and home on the same drive (with or without separate partitions). ***The important thing is to have the backup somewhere else***: on an external drive, in another house, in a safe-deposit box ...

---

