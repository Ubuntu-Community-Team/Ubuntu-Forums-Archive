---
title: "Backup Happiness"
date: 2008-06-11
forum: General Help
---

### Post by Vordark on 2008-06-11
I'm hoping that a friendly back-up guru can answer a couple of questions for me, chief of which is whether or not what I want to do makes for a valid backup strategy.  I'm running Ubuntu 7.10 64bit(currently, but I'm hoping to drop to 32bit soon).

I have two 300gig drives in my system.  The first drive has everything on it.  The OS, my programs, my home directory, everything.  The second drive is my "backup" drive.  I periodically create a folder on it with the current date, then copy my entire home directory into it.  This is my "oh crap, I deleted a file and need it back" system.

What I want to do is have a much stronger backup plan should my main drive/os/whatever gets hosed, since right now my plan would be:  wipe the drive, re-install the OS, patch the OS, re-install all my packages (or, at least, the ones I remember I installed in the first place), spend two days configuring the UI and such and work as I want then move my data in.

I hear tell that there is a magical command, perhaps "rsync" that allows one to make a byte-for-byte image of an entire drive.  I further hear tell that I could go out, but a relatively inexpensive large capacity USB drive, plug it into my system, run the mystical rsync command and then, should my OS get hosed, I can connect my USB drive, boot from the live CD, then run a reverse "rsync" incantation to completely restore my system with almost no thought or worry.

So, my specific questions are the following:

1.  Is there such a magical command?  What is the command to make a backup to an external USB drive?  What is the command to restore said backup?

2.  What are some good, yet relatively in-expensive, 300gig+ external USB drives which would work for this purpose?

3.  If my primary drive actually dies due to hardware failure, can I go out, buy a new drive of equal or greater size and restore to that, or would the image I create essentially be married to the original drive?

4.  Is any of this even correct, or have magic elves been whispering in my ear, leading me astray?

My main goal is to have a back-it-up-and-forget-it policy (perhaps running a nightly command via cron or just running a shell script periodically) that dumps the image to the external drive.  And, when my main drive hoses itself, I want to run one command, hopefully from the live CD, that fixes everything, let's me boot off my main drive and have everything *just work*.

Sorry for the book, but I'm very nervous when it comes to losing data.  Thanks for any help you can give me!

---

### Post by honda on 2008-06-11
I have been using rsnapshot. In short it uses rsync to maintain a few hourly, daily, weekly and monthly complete mirrors of the folder being backed up, without wasting any space for unchanged files. Easy to recover from (just copy over with whatever file copying tool you like to use). 

Get it from the repositories and check out the man page (or [http://www.rsnapshot.org/]("http://www.rsnapshot.org/"))

For a simple manual solution grsync is a graphical front to rsync, does a mirror of a folder without moving unchanged bits. 

When doing backup over a network I found rdiff-backup to meet my needs more than rsnapshot, again read the documentation and decide for yourself... [http://www.nongnu.org/rdiff-backup/]("http://www.nongnu.org/rdiff-backup/")

Hope this helps!

---

### Post by ilrudie on 2008-06-11
dd can do the byte for byte copies you mentioned above however it is not commonly used for backups.  rsync is common.  rsnapshot as mentioned above also sounds good.  I have heard very good things about bacula also.  [http://www.bacula.org/en/](http://www.bacula.org/en/)

---

### Post by Vordark on 2008-06-11
I am *very* happy for these suggestions, but I have a couple of requirements that I want to be sure are met by these solutions.

I want to be able to point the backup/imaging software at a drive and have it do a byte-for-byte copy, to the point where even if I format that drive and then restore from the image (presumably running the reverse of the image command) the drive will them have not only all the data, but the partition table, boot sector, etc.

When I hear words like "folders" this indicates to me that my *data* may be intact, but I may not be able to completely resurrect a drive if I should happen to, oh, I don't know, say hose my partition table.

I'd also like to know that if my internal drive fails utterly (the magic smoke escapes) that I can go into Circuit City, but a new drive, plug it in, then restore the image I made to that drive and have my system back.

I may be being overly anal in my interpretation of what you helpful folks have written (or I may just be misreading things or what have you), but I'd really like to know if this backup strategy will work.

Thanks again for all of your input so far!

---

### Post by bingoUV on 2008-06-11
Assuming your main drive is /dev/sda (most likely true if you have only one drive), and external drive is /dev/sdb. Format external drive as ext3 using gparted. Mount it at, say, /media/backup
```

sudo mkdir /media/backup
sudo mount /dev/sdb /media/backup
dd if=/dev/sda | gzip -9 > /media/backup/June11.gz

```


To restore, (will need a live cd to boot from as your main drive has been hosed). Need to mount external drive in this live cd environment too : 
```

sudo mount /dev/sdb /media/backup
gunzip /media/backup/June11.gz - | dd of=/dev/sda

```

---

### Post by drs305 on 2008-06-11
I use partimage. It copies an entire partition but doesn't use empty space (so it's not going to be the same size as the original partition). If my main partition dies, I can use partimage to copy the backup image directly to a new partition. It will retain my OS, settings, etc. If the partition is restored to the same location ( /dev/sda1, etc), I believe it will work exactly as the original partition.

The partimage solution to me is a "system restore" backup. I do it about once every 10 days or just before and after a major upgrade.

Some disadvantages: manual backups necessary; can't access particular files in the backup - it's all or nothing.

---

### Post by ilrudie on 2008-06-11
> **Vordark said:**
> I am *very* happy for these suggestions, but I have a couple of requirements that I want to be sure are met by these solutions.

I want to be able to point the backup/imaging software at a drive and have it do a byte-for-byte copy, to the point where even if I format that drive and then restore from the image (presumably running the reverse of the image command) the drive will them have not only all the data, but the partition table, boot sector, etc.

When I hear words like "folders" this indicates to me that my *data* may be intact, but I may not be able to completely resurrect a drive if I should happen to, oh, I don't know, say hose my partition table.

I'd also like to know that if my internal drive fails utterly (the magic smoke escapes) that I can go into Circuit City, but a new drive, plug it in, then restore the image I made to that drive and have my system back.

I may be being overly anal in my interpretation of what you helpful folks have written (or I may just be misreading things or what have you), but I'd really like to know if this backup strategy will work.

Thanks again for all of your input so far!

1 thing you might want to think about here is problems with differing hard drive sizes.  I'm not sure entirely sure how dd works but I've been kicking this around in my head and I thinkyou may encounter a problem:

If you write a partition table to disks that have different physical layouts your file system will most likely be corrupt.  That would mean you would have to buy the exact same hard drive or do your research and make sure the physical layout is the same.  For instance if you have a partition that is like 10 cylinders and each cylinder is 10 bytes you would have a partition that is 100 bytes.  Map that same partition to cylinders that are only 9 bytes and now you only have a 90 byte partition.  If you hade more that 90 bytes of data something bad is going to happen.  For that matter even if you only had 80 bytes of data the inodes won't match up and your filesytem will probably be unrecoverably corrupt.  I don't know if dd is intelligent enough to fix that or not.  My guess would be no.  It would be much better to have some method of quickly building the server 90% configured.  Copy the data and finish the configuration.  Also mirroring your drives can keep you out of the total rebuild a whole bunch of the time.  I'm not sure what the best solution for Ubuntu would be but Kickstart for RPM based systems is very good.  There may be a similar solution for deb based systems also.  

Just somthing that was kinda bothering me about the way you seem to be going about this backup thing.

Good luck.

---

### Post by bingoUV on 2008-06-12
> **ilrudie said:**
> 1 thing you might want to think about here is problems with differing hard drive sizes.  I'm not sure entirely sure how dd works but I've been kicking this around in my head and I thinkyou may encounter a problem:

If you write a partition table to disks that have different physical layouts your file system will most likely be corrupt.  That would mean you would have to buy the exact same hard drive or do your research and make sure the physical layout is the same.  For instance if you have a partition that is like 10 cylinders and each cylinder is 10 bytes you would have a partition that is 100 bytes.  Map that same partition to cylinders that are only 9 bytes and now you only have a 90 byte partition.  If you hade more that 90 bytes of data something bad is going to happen.  For that matter even if you only had 80 bytes of data the inodes won't match up and your filesytem will probably be unrecoverably corrupt.  I don't know if dd is intelligent enough to fix that or not.  My guess would be no.  It would be much better to have some method of quickly building the server 90% configured.  Copy the data and finish the configuration.  Also mirroring your drives can keep you out of the total rebuild a whole bunch of the time.  I'm not sure what the best solution for Ubuntu would be but Kickstart for RPM based systems is very good.  There may be a similar solution for deb based systems also.  

Just somthing that was kinda bothering me about the way you seem to be going about this backup thing.

Good luck.

This is no big deal. You dd a hard disk to a **file** on another disk. Preferably gzipped so that the empty space on the hard disk takes negligible space in the file and other space is also reasonably compressed.

Whatever the size and layout of the new hard disk, does not matter in the least.

---

### Post by Vordark on 2008-06-12
> **bingoUV said:**
> This is no big deal. You dd a hard disk to a **file** on another disk. Preferably gzipped so that the empty space on the hard disk takes negligible space in the file and other space is also reasonably compressed.

Whatever the size and layout of the new hard disk, does not matter in the least.

I was kind of wondering about this too when I read the previous post, since in my experience dd just treats whatever it's reading as a stream of bytes ("stream of bytes!?! In *my* Unix!?!") but I think the question is that if critical bits of data like partition tables are just ripped off one drive and thrown onto a completely different drive on a restore (your drive melted, you bought a new one at Circuit City and just did a restore) you might be pushing critical yet wrong data about the disk itself onto the new drive.

I guess the question is, does dd grab all of these files *and* do these files do bad things to disks with different geometries?  I used to know how partition tables and such were constructed, but that was back in the day when real men rolled their own device drivers. :)

Thanks again for all the great input!

---

### Post by bingoUV on 2008-06-12
I once dumped a 40GB IDE Samsung hard disk onto a 160 GB Seagate SATA. Difference in manufacturing times was 5 years. It worked, except that the 160 GB hard disk showed 120 GB unpartitioned data. It may not work always, this is just an anecdote.

---

### Post by ilrudie on 2008-06-12
> **Vordark said:**
> I was kind of wondering about this too when I read the previous post, since in my experience dd just treats whatever it's reading as a stream of bytes ("stream of bytes!?! In *my* Unix!?!") but I think the question is that if critical bits of data like partition tables are just ripped off one drive and thrown onto a completely different drive on a restore (your drive melted, you bought a new one at Circuit City and just did a restore) you might be pushing critical yet wrong data about the disk itself onto the new drive.

I guess the question is, does dd grab all of these files *and* do these files do bad things to disks with different geometries?  I used to know how partition tables and such were constructed, but that was back in the day when real men rolled their own device drivers. :)

Thanks again for all the great input!

Forget about dd.  dd writes everything.  It writes the files, inodes, partition tables... everything.  As I said before.  If you are restoring to something that has the same physical layout or you get lucky and the layout is similar you will be ok.  You can't guarentee availability of a disk with an identicle or similare physical layout though.  I have discussed this with about 30 combined years of unix experience in 3 people and they all agree.  Using dd as a backup solution is a mistake you will only make once.

Look into bacula.  It has a "bare metal restore" feature that I think is what you are looking for but its intelligent.  It doesn't just dump bits from a file to the disk it actuall recreates the file system and partitions for you while its restoring all your data.  Full system restores can be done from a bootable cd and an NFS share.

Otherwise rsynce is a very capable program aswell.  There is not bare metal restore but it will backup your files.

---

### Post by chunchengch on 2008-06-12
try Clonezilla, it is powerful and very easy to use.

[http://www.clonezilla.org/](http://www.clonezilla.org/)

---

### Post by paulsjv on 2008-06-12
Has anyone ever used [Duplicity]("http://freshmeat.net/projects/duplicity/")?

---

### Post by Vordark on 2008-06-12
> **ilrudie said:**
> Look into bacula.  It has a "bare metal restore" feature that I think is what you are looking for but its intelligent.  It doesn't just dump bits from a file to the disk it actuall recreates the file system and partitions for you while its restoring all your data.  Full system restores can be done from a bootable cd and an NFS share.

As soon as I can grab more that five minutes from my oh-so-adorable three-year-old I'll read up on bacula.  Thanks for the suggestion!  Can I ask three quick questions though about this software:

1.  Can I do my backups to generic external, USB hard drive?  I'm not too worried about cron automation, I can click a button myself every night if I have to, but I'm hoping to use such a device as my backup hardware.

2.  If I hose my drive at the software level, completely blowing out the partition table, etc., can I restore my entire system using the backup I made and this software?

3.  If my drive completely eats itself, hardware and all, can I go to Circuit City, buy a new drive, plug it in and restore to that, thus having my system as good as new?

Thanks again everyone for the guidance.  I'm becoming increasingly paranoid about data loss as I realize I have nearly a decade of mail, documents, source code and god knows what else just waiting to evaporate into the great beyond. :)

---

### Post by ilrudie on 2008-06-12
> **Vordark said:**
> As soon as I can grab more that five minutes from my oh-so-adorable three-year-old I'll read up on bacula.  Thanks for the suggestion!  Can I ask three quick questions though about this software:

1.  Can I do my backups to generic external, USB hard drive?  I'm not too worried about cron automation, I can click a button myself every night if I have to, but I'm hoping to use such a device as my backup hardware.

2.  If I hose my drive at the software level, completely blowing out the partition table, etc., can I restore my entire system using the backup I made and this software?

3.  If my drive completely eats itself, hardware and all, can I go to Circuit City, buy a new drive, plug it in and restore to that, thus having my system as good as new?

Thanks again everyone for the guidance.  I'm becoming increasingly paranoid about data loss as I realize I have nearly a decade of mail, documents, source code and god knows what else just waiting to evaporate into the great beyond. :)

First I would like to let you know that I have not used yet bacula myself however it comes very highly recommended from a co-worker with many years of Unix and GNU/Linux experience.  That said:  Bacula is a highly scalable solution.  It should support backing up to a generic external hard disk.  It will also allow you to install a client on other computers (OSX, Unix, GNU/Linux and Windows) that will backup over the network.  I just don't know about the push a button thing but it is supposed to be easy to schedule nightly backups so you should be fine there.  You will have to read up on the bare metal restore feature which is essentially restoring to a totally janked up (data wise not hardware wise) system or a fresh disk.  I know that with a cd you can restore from a networked server very quickly and easily.  You can look to see if you can just boot the cd and restore from a USB hard disk.  That seems like it should be possible but considering this can be used with hundreds of computers you might need to have another computer to act as the server.  You could always contacted the developers and ask for the USB restore feature in future version if its not there.  Finally bacula is an intelligent backup solution.  Unlike dd which just copies the bits bacula actually understands the partitioning and file systems.  This allows you to do a quick complete restore ("Full Bare Metal") to a brand new blank hard disk regardless of physical layout as long as it is large enough to hold the partitions.  

Sorry thats not the best written or organized paragraph but I wanted to get some quick answers up and get on with my night.  Good luck!

---

### Post by rbmorse on 2008-06-12
If Bacula doesn't do it for you there is also PING (Partimage in not Ghost). It's got one of those text mode GUIs from back in the day when men were men. 

It only does a partition at a time, but it will do the track 0 stuff. I use it to backup to an external in a USB enclosure...works fine. Based on Partimage which is pretty well proven.

---

### Post by Knightwise on 2008-06-18
What you can also do is setup software mirroring. 

thanx to Popey from #ubuntu-Uk on freenode (be sure to check out his website and great video tutorials too) 

Here is the video on how to do it : [http://screencasts.ubuntu.com/MoS2007/10_Installing_Ubuntu_Part_2](http://screencasts.ubuntu.com/MoS2007/10_Installing_Ubuntu_Part_2)

Here is some more info on how to setup raid on fedora
[http://www.texsoft.it/index.php?c=hardware&m=hw.storage.grubraid1&l=it](http://www.texsoft.it/index.php?c=hardware&m=hw.storage.grubraid1&l=it)

and the great manual on how to do it in Ubuntu
[http://advosys.ca/viewpoints/2007/04/setting-up-software-raid-in-ubuntu-server/](http://advosys.ca/viewpoints/2007/04/setting-up-software-raid-in-ubuntu-server/)

---

### Post by cariboo on 2008-06-18
Have you had a look at sbackup, it is in the repositories and you can use synaptic to install it.

Jim

---

