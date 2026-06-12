---
title: "Spare Hard drive Mirror of main drive."
date: 2007-03-03
forum: General Help
---

### Post by Dragon43 on 2007-03-03
I have a stand alone desktop computer running Ubuntu 6.06 and have got it all adjusted and updated and tweaked and set so that it works good.  I took a hard drive of the same size, ( 40 Gig's ) and used the CD to make a new installation.  Now I have the original adjusted and tweaked one in the main (a) or IDE 0 position {master}, (C) and the new hard drive installation as the slave.

Now, how do I do a complete mirror of the main adjusted and tweaked drive so that I can pull the spare HD off line and have a second system exactly like the first in case tomorrow lightning fries my hard drive. or I mess it up trying new stuff with Linux.  
I am real new and not much of a 'geek' so use small words and do not assume I know anything please.

Can someone lead me by the hand?

I am new to Linux.

---

### Post by joselin on 2007-03-03
Try with this program, can be usefull for you:

[http://www.partimage.org/Main_Page](http://www.partimage.org/Main_Page)

---

### Post by Dragon43 on 2007-03-04
I downloaded it and could not figure it out or how to work it.  I tried the one where you burn to a CD and tried that too.

Makes no sense to me.  
Is there better instructions for that program for a new guy?  All I could find was expecting me to know a lot more than I do.

Anyone around Central Arkansas that I can get with so I can learn this stuff?

---

### Post by Dragon43 on 2007-03-04
Surley someone knows how to do this......

---

### Post by Mr. C. on 2007-03-05
Dragon43,

First, I want to congratulations on your very wise move to create a clone after all your hard work!

The basic idea is simple - your goal is to copy the data from your configured disk to a backup disk so you can do a quick swap should the disk die.

There are many ways to accomplish this.  The most straightforward simply copies bit for bit, sector for sector everything on HD1 to HD2.  More complex schemes attempt to compress data, split it across multiple multiple media, stream across the network, etc.

You want a simple, plug-n-play solution.  Disk dies, take it out, replace it, boot system.

To accomplish this, you must not be booted into the system, as the file system is actively changing while the system is booted.  Therefore, you need to boot from another disk/floppy, and run some utility that allows bit for bit copying of your HD1 to your HD2.  Programs such as Norton's Ghost, or other freeware utilities (such as the one the previous poster mentioned) allow you to do this.  You will boot from a floppy, run a command, telling it which disk to copy from/to and wait a while until its done.  You will then have an exact clone of your HD1 on HD2.

With this in mind, perhaps the partimage documentation will make more sense - review it if you want a freebie solution.  If you don't care so much about $50, buy yourself a copy of something like Norton's Ghost and be done with it.

Make sense?
MrC

---

### Post by DagMan on 2007-03-05
The easiet way for me is to use the live install cd as an environment.

You would then mount the filesytem of the master at one point and the slave at another point.  You of course will want to format the slave to a linux filesystem if you have not already, if it is a fat filesystem then it is still easily done making an archive but plain copying will mess with the file permissions.  You can back up bit for bit from the live CD, the only thing that I'm not postitive about is cloning what's in the MBR for grub, but installing grub onto the drive later if you need it is also easy.

I'm sure someone can give specific instructions, but they'de need to know where your partitions are and how many you have assuming you have more than just / and swap.
Also it would be helpful if you could describe the filesystem of the slave drive... is it blank, does it have a windows install, where are the partitions on that drive, etc.

---

### Post by Mr. C. on 2007-03-05
A live CD is an excellent option.

Do not mount either master or slave!  This will cause the file systems to both be live and in use, and you will not get perfect copies, and will only be able to copy one file system at a time.

Instead, just use dd on the raw disks:

  dd if=/dev/hda of=/dev/hdb  bs=4096

and let it run to the end.  Change hda and hdb above with the correct devices that describe your entire hard drive.  It will error as the end of the disk is reached - thats fine.

You will then have two exact copies bit for bit of the entire disk.

MrC

---

### Post by DagMan on 2007-03-05
You say tomato I say tomato.

I say  may as well format the slave, mount both at separate points, use cp -a ending up with a less fragmented copy on the slave, unmount, tweak both filesystems, take the short extra step, since the slave is coming out anyway, of making it the master and getting grub on the mbr again via the live cd.  That would be more important to me, to end up with almost 0% non-contiguous space than to make a clone but I've honestly also done that and felt no differance, the rearanging of data to be more consistant part I mean

I'll leave this thread to you, you seem to know more,  I've never seen that sort of thing btw, even google doesn't have too much on it and the man page isn't very informative.  Would that clone the MBR as well?

---

### Post by Mr. C. on 2007-03-05
> **DagMan said:**
> You say tomato I say tomato.

I say  may as well format the slave, mount both at separate points, use cp -a ending up with a less fragmented copy on the slave, unmount, tweak both filesystems, take the short extra step, since the slave is coming out anyway, of making it the master and getting grub on the mbr again via the live cd.  That would be more important to me, to end up with almost 0% non-contiguous space than to make a clone but I've honestly also done that and felt no differance, the rearanging of data to be more consistant part I mean

I'll leave this thread to you, you seem to know more,  I've never seen that sort of thing btw, even google doesn't have too much on it and the man page isn't very informative.  Would that clone the MBR as well?

Dagman, you can certainly choose whatever method you want.  You asked for "complete mirror" ..." exactly like the first one".  Your method does not give you that.

dd is *the* standard for doing RAW disk copies.  You must not have looked very hard.  Try google dd clone.  

Does it give you a copy of the MBR you asked. I already gave you the answer - it copies the *entire disk* bit for bit.  You get exactly the same partition tables, including their boot records, all partitions, all data.  It is an exact clone of the disk.

I've been doing it for 25 years.  This is THE way we used to make clones for Unix kernel / build testing, and it is standard practice to set up cloning stations such as described for forensics.

If you wanted a defragmented backup, use "dump" and "restore".

My goal was to arm you with knowledge and comprehension - it is now yours to do with as you will.

Mrc

---

### Post by DagMan on 2007-03-05
Hey I'm looking back up at my previous post and It didn't come off how I intended.  I must not have read it over well before posting it.  I was being serious, that you seem to know more than me and are better qualified... and since you have decided that you are going to participate in the thread more actively than just saying that there's a lot of options. 
Thanks for the info.  Despite confusion, the rude manner was annoying but so far it looks helpfull.

---

### Post by Mr. C. on 2007-03-05
No sweat - I took no offense.  Too often in forums such as these, there is shoddy, misguided, or plain incorrect advice, often with more huffing than proof or evidence.  Any skepticism is likely justified.

Let us know how things turn out,
MrC

---

### Post by Dragon43 on 2007-03-06
Dragon43 here:

I tried the 'Ubuntu' CD.

I got all the way to (ubuntu@ubuntu:~$  {sudo dd if=/dev/hda of=/dev/hdc bs=4096} )  in the terminal after many false starts and a lot of 'bad commands' but this seems correct but it just sits there with a blinking cursor.

I do this several times and then figure that it is working but I can't feel any hard drive running.  the CD spins up every once in a while.  Let it set for 1.5 hours. I figure that should work for 2 Gigs.

Nada.....  What did I do wrong?

hda has my working system, ( master (only thing) on IDE O )

hdc is the Master on IDE 1 ( CDROM is slave on same ribbon)

hdc has a plain 'Ubuntu' CD install with nothing done to it but the install = I assume the HD is formatted and portioned correctly.

So, can you tell what I messed up?

---

### Post by Mr. C. on 2007-03-06
Its working - its a lot of data to copy, and I gave you a very small blocksize.

You can change the blocksize to something 64k, or 1M if you want.  That will speed up the transfer significantly.

Test it out with :

dd if=/dev/hda of=/dev/null bs=64K

When its reached the end of the disk, it will give an IO error, indicated it can't copy any more.

You'll see the disk light constantly (if you have one).

MrC

---

### Post by Mr. C. on 2007-03-06
A feature I'd forgotten about.

You can put the job in the background either at start, or if its already running with ^Z and bg.

Then, you can send that job or pid of the job a kill -USR1 signal to see how far along the copy has proceeded:

# dd if=/dev/hda of=/dev/null bs=1M &
# kill -USR1 %1
# 52414+0 records in
52413+0 records out
54959013888 bytes (55 GB) copied, 1905.77 seconds, 28.8 MB/s

---

### Post by Dragon43 on 2007-03-07
> **Mr. C. said:**
> Its working - its a lot of data to copy, and I gave you a very small blocksize.

You can change the blocksize to something 64k, or 1M if you want.  That will speed up the transfer significantly.

Test it out with :

dd if=/dev/hda of=/dev/null bs=64K

When its reached the end of the disk, it will give an IO error, indicated it can't copy any more.

You'll see the disk light constantly (if you have one).

MrC

**MrC**, You da man.......

I used {ubuntu@ubuntu:~$ sudo dd if=/dev/hda of=/dev/hdc bs=1M}  and I got my cloneof 41 GIG's in 57.75 minutes.  "Woot"

I have pulled the original, am working on the back-up HD now with a small 2.3 Gig in hdc just to make sure the CD ROM as the slave on that ribbon will work.  I checked the last little things on the drive I added just before the copy and it is all here.

Now that I have a safe copy, I can go back to learning stuff knowing I will not lose all that I have done to this point.  what a relief.

Thanks again

Dragon43

---

### Post by Mr. C. on 2007-03-07
You're welcome!  Glad you hung in there and saw the light at the end of the cloning tunnel.

Cheers,
MrC

---

### Post by tagra123 on 2007-03-07
[http://ubuntuforums.org/showpost.php?p=1917499&postcount=40](http://ubuntuforums.org/showpost.php?p=1917499&postcount=40)

The above link is a mini howto in an answer in another post.

You could actually mount your new drive as  tempdrive or backupdrive.  The images partimage create could then be saved on DVD's or CDs

dd is also good but partimage only copy where existing data is (saves space). This makes a great way to store images on other media.

---

### Post by Dragon43 on 2007-03-07
> **tagra123 said:**
> [http://ubuntuforums.org/showpost.php?p=1917499&postcount=40](http://ubuntuforums.org/showpost.php?p=1917499&postcount=40)

The above link is a mini howto in an answer in another post.

You could actually mount your new drive as  tempdrive or backupdrive.  The images partimage create could then be saved on DVD's or CDs

dd is also good but partimage only copy where existing data is (saves space). This makes a great way to store images on other media.

That is something I need to try also, Thanks for the links.

I like the way you make it a 'step for step' for new guys like me.

---

### Post by Mr. C. on 2007-03-07
There are lots of technical solutions to these types of problems, but they often miss the most critical aspect of making a recovery system.

The must be very SIMPLE and RELIABLE so that when necessary, the system can be brought back on line QUICKLY and RELIABLE.

Too many solutions optimize disk space with convoluted procedures.  And until these procedures are actually TESTED and proven that a RELIABLE restore can be made, they are focused on the wrong problem.

In this case, the OP wanted a simple and reliable way to bring the system back online quickly.

Here's my motto: A backup solution is only as good as your ability to guarantee you can restore the system.

---

### Post by tagra123 on 2007-03-07
> **Mr. C. said:**
> There are lots of technical solutions to these types of problems, but they often miss the most critical aspect of making a recovery system.

The must be very SIMPLE and RELIABLE so that when necessary, the system can be brought back on line QUICKLY and RELIABLE.

Too many solutions optimize disk space with convoluted procedures.  And until these procedures are actually TESTED and proven that a RELIABLE restore can be made, they are focused on the wrong problem.

In this case, the OP wanted a simple and reliable way to bring the system back online quickly.

Here's my motto: A backup solution is only as good as your ability to guarantee you can restore the system.

My backup method is 100% reliable if you follow the directions. Partimage 100%.  Daily weekly and hourly 100%.  

Using partimage I can restore my home and root director usually within 1/2 an hour.  

With the other If I overwrite a file I just copy a good copy from the tempdrive.  If I need to go back a week or two I just open up the tar file and copy what I need.  Cannot be too much simpler.  The most difficult part is the setup but that's not difficult either if the instruction are actually read and followed. It really should take lees than 1 hour to set up the script -- if that long.

Best of all there is no GUI in the way -- just enter the paths and you can count on it.

---

### Post by Mr. C. on 2007-03-07
> **tagra123 said:**
> My backup method is 100% reliable if you follow the directions. Partimage 100%.  Daily weekly and hourly 100%.

If you want to believe in your own hyperbole, enjoy the ride.

---

### Post by tagra123 on 2007-03-07
> **Mr. C. said:**
> If you want to believe in your own hyperbole, enjoy the ride.

C. 

Critics are a dime a dozen and enjoy critizing as if they are getting paid for it.

What is you solution?  

Post it, if you have one.

  I know mine has worked. I build computers and this is how I install systems and create restore disks. I haven't had one fail yet. 

I'm not here to argue -- to defend a post maybe.

Show us your solution or in your opinion is "dd" the only way.   I question if you even looked over the how-to.

---

### Post by Dragon43 on 2007-03-08
Well, being a new guy and the "OP" and a newbie to 'Linux' and more worried about hardware crash due to using old equipment, ( I'm poor, using 1998 equipment with Win 98se for example. ) or power loss or lighting strikes or cat spills coke on computer tower or I drop computer tower or virus eats my hard drive or hard drive dies of old age and since I use 'mobile trays' for my hard drives, being able to pull and replace a hard dive takes about 30 seconds if the computer is off when I start.

So, using the live CD once a week or when I get a major change working good, a complete back up or clone, all the spaces and warts and bumps and all, is just what I want.

When I get to the point that I am 100% on Linux and doing something important where daily back-ups would be needed, then I will want a different way I would think.

But for a 63 year old guy who is disabled and not likely to ever work again and who is just trying to learn Linux because I don't want to be sucked into the XP or Vista world ( Nor Macs ), then  the "live CD with dd" is just the thing.

Lots of ways to get from A to B.  I get frustrated with my sister for only ever learning one way and if that does not work, she is lost.  So I want to learn several ways.

That is what this thread is teaching me.  I have a lot of it bookmarked and will use it as I learn how.

Since I have a dedicated machine and many old hard drives, ( And mobile trays, did I say I love 'mobile trays?' ) the way MrC showed me was a good option for me at this time and it is so simple it took me only about 10 tries to get it to work.

My 'Sys Resc' CD is still asking for stuff I don't understand or know where to find. ( I've got about 50 tries in it and my G4L CD another 50 ) so I'll be asking about it soon so don't anybody go away.  I need you all.

---

### Post by tagra123 on 2007-03-08
Dragon43

I am mentioning this mainly for the folks that do not have mobile trays.

Search on ebay

USB to IDE Adapter  (they work on SATA drives too)

These things are nice for backing up computers especially when there is no network or no removable hard drive.

dd is fine if you have the space for an exact copy. Some of us do not have that kind of space.  You can also pipe the dd through gzip and create an exact compressed image. I use it myself  on smaller drives like laptops and I always use it to backup the MBR and partition tables.

I like partimage for bigger drives because if the 40GB drive only has 10GB of data on it than that is all that gets backed up to the image.  It also can compress the image it creates.  Its an advantage to me because harddrive space isn't free. What I like most about this method is when I get the 40GB drive to fit on 1 or 2 DVDs.  Now for large 250GB and larger surely the advantages can be seen.

All I was really trying to say in the previous post is that their is more than one way to do things like this.  


Just in case you want to save a drive or partition to a file image that can be saved to a dvd later on -- here is dd piped through gzip

dd if=/dev/hdx | gzip > /path/to/mybackupimage.gz

hdx could be hda,hdb,hdc,hdd or for partitions hda1,hda2 etc...

the images can be split to fit on dvds or cd

---

### Post by linuxjerk on 2007-04-02
All those still require the disk be unmounted to copy. Try G4U I got it to work on my system.
You can either do floppies or cd.
[http://www.feyrer.de/g4u/](http://www.feyrer.de/g4u/)

---

### Post by KuroYoma on 2008-06-19
I want to take my 40gig harddrive with ubuntu and make an exact copy of it to my External USB Haddrive.  I want the copy of the original harddrive to be copied to the 2nd partition space of my external usb harddrive.

---

### Post by greco8523 on 2008-06-20
why don't you just clone it with dd? that way you get an exact copy.

---

### Post by logos34 on 2008-06-20
> **KuroYoma said:**
> I want to take my 40gig harddrive with ubuntu and make an exact copy of it to my External USB Haddrive.  I want the copy of the original harddrive to be copied to the 2nd partition space of my external usb harddrive.

dd command is simple and elegant, but only when you're cloning one partition to another, or an entire disk to another empty disk. 

If your setup is still the same as [here]("http://ubuntuforums.org/showpost.php?p=5209356&postcount=9"), and you're trying to put everything in the sdb2 space, probably the easiest way is to use Gparted to first delete sdb2, then use the ['copy' function]("http://gparted.sourceforge.net/larry/move/move.htm") to transfer sda1 ubuntu root to the resulting unallocated space.  Do the same for swap if you want, or just make a new one (faster).  Edit your menu.lst and fstab files.

---

### Post by KuroYoma on 2008-06-21
I am trying to keep the first partition on my external because is comtains all my media and backups and so forth. But there is plenty of unpartitioned space after the first partition.  basically i want to know if there is a command for dd that tells it to use the 2nd partition or is it only hd1 to hd2.

i am still considering using the windows xp iso modification and keeping ubuntu as my internal OS but right now this is my best bet and at least i keep the OS i am worried about and experimenting with safe.  so just wondering.

thnx for your help

---

### Post by logos34 on 2008-06-21
> **KuroYoma said:**
> basically i want to know if there is a command for dd that tells it to use the 2nd partition or is it only hd1 to hd2.

you can only do one partition at a time.  

for root:

sudo dd if=/dev/sda1 of=/dev/sdb2 bs=4096 conv=notrunc,noerror

(use the livecd as both partitions need to be unmounted)

---

