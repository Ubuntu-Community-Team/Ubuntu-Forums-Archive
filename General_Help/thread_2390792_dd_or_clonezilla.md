---
title: "dd or clonezilla"
date: 2018-05-02
forum: General Help
---

### Post by sp40140 on 2018-05-02
Hello 
I have 60 gig SSD with OS and coups of other partitions.
I want to clone it so that I can use the SSD for different PC and put the cloned (new platter drive) on this one.

The thing is new HDD is bigger 250 gigs. And I would like to be able to use the remaining approx 190 gigs.

What is better option? dd or clonezilla or something else entirely?

I am not  worried about speed as it's just 60 gig SSD (and about half of it free).
I am concerned about accuracy and other things (which I am not aware of as this will be my first attempt at cloning).

---

### Post by TheFu on 2018-05-02
You need to work at the file system layer, not lower.  But really, the best option is to make a backup using your normal backup method, then restore using the restore technique required. There can be performance issues when the physical sector sizes change between storage devices when working below the file system.  Something like **aptik** would be the quickest way to backup only those things most end-users need.

Cloning is best when moving between very closely related systems. If you want to copy file systems, **fsarchiver** is the tool I'd use.

There is an issue with GPT disk formats.  Since the partition table is written at both ends of the disk, cloning can leave 1 of those GPT tables in the wrong location, which will need to be fixed.  Best to fix this before any data is on the disk, but that isn't always possible.  Doing a fresh install, then restoring data is how I'd do it.

But this really is a chance to fully test the backup and recovery processes in a very useful way.  Please take advantage of it, take lots of notes, so when you need to restore from backups next time, perhaps when you don't have time, you'll have more confidence.

---

### Post by sudodus on 2018-05-02
Test both SSDs to check if they have the same physical sector size, 512 bytes or 4096 bytes.

```

sudo parted -ls

```

If the same physical sector size you can clone, and *I would recommend **Clonezilla***. it is both faster and safer than dd.

After cloning you can use **gparted** to add a partition in the unallocated drive space, or expand an existing partition to use the unallocated drive space.

It is a good idea to create a **data** partition (for example with the label 'data'), and keep your personal files in that partition. It will make backup of your personal files easy and separated from backup of the operating system.

[hr][/hr]
Otherwise (if the physical sector sizes are different) you should *not* clone, but use the method suggested by @TheFu.

This method, working at the file level works in both cases, but it is more complicated, if you want everything to work including bootloader in BIOS (legacy) mode and matching between /etc/fstab and the partition UUIDs.

[hr][/hr]
An alternative is to make a fresh installation, where you might keep /home and put it into a separate home partition, which you activate via 'Something else' in the partitioning window of the installer. The personal files in your home directory and several tweaks will survive, but you must install the programs (that you installed yourself) again.

---

### Post by sp40140 on 2018-05-02
@TheFU
I am not worried about data/backup. All the important stuff is on different physical drive.
I just don't want to go through the very time consuming hassle of re-installing and configuring all the applications I have.
The main concern here is that I have different capacity and types of drives. 
Source (entire drive) : 60 GB SSD
Destination : 250 GB Platter drive.

One example of why I prefer to clone over fresh install is: My All-in-one printer. I spent lots of time (and lots lost hairs due to pulling) to get the scanner working. And I don't have time nowadays to go through it again, nor can my scalp afford to lose additional hair. :)..
I know fresh install is always recommended, but would prefer it if I can just clone the drive and replace the ssd with new platter drive without much work.

---

### Post by sp40140 on 2018-05-02
@sudodus
Shouldn't the cloning app be able to sync the sector sizes?

---

### Post by TheFu on 2018-05-02
> **sp40140 said:**
> @sudodus
Shouldn't the cloning app be able to sync the sector sizes?

They don't.  Sector sizes are physical on storage devices.
You can try doing a clone. See if it works, but if the storage performance is 20-50% less than you expect, it is likely the sector alignment issue.

I would use 'dd' because I know how to use it and can leave it running overnight, so it doesn't take any of  my time. 
But I don't think that is the best answer.

---

### Post by sp40140 on 2018-05-02
Good to know about the sector size.
So you still recommend aptik or FSArchive? Which one is better suited for my job?
I don't know anything about either so will have to read up on both.

---

### Post by monkeybrain20122 on 2018-05-02
I would use fsarchiver. You just need to copy the file system actually. fsarchiver places no restriction on the size of the target as long as it is big enough for the data. but for clonezilla the target has to be as least as big as the source even if the source maybe mostly empty (so you would have to shrink the source partition with something like gparted first before cloning if you don't want to allocate a lot of empty space to the target) I have move my os from one machine to another  ad restore OSes with fsarchiver many times, it is quite easy to use and reliable.

I won't recommend dd for anything more complex than making a live usb, it is easy to mess up and especially if you have a lot to copy . It can destroy your disk (fsarchiver just copies files without intricate low level operations , no harm would be done even if the operation ends in error)  It is not 1995 anymore, there are better and safer tools around.

**Edited:** And my motto is, if you have to ask then definitely don't use dd.

---

### Post by HermanAB on 2018-05-02
Well, provided that the destination is >= the source then you can copy the disk with netcat over the network and afterwards adjust the partitions with gparted.

If you have gigabit ethernet, then you don't need to compress the data.  Otherwise, you can pipe it through gzip also.

On the destination:
nc -l -p 1234 > /dev/sda

On the source:
nc 192.168.x.y 1234 < /dev/sda

---

### Post by sudodus on 2018-05-03
> **sp40140 said:**
> @sudodus
Shouldn't the cloning app be able to sync the sector sizes?

@TheFu is right. The cloning app cannot fix it.

But it is easy to run a check to find out about the physical sector sizes on the source drive and target drive, and after that decide which method to use.

```

sudo parted -ls

```

---

### Post by sp40140 on 2018-05-03
OK, So Options are:
FSArchiver
aptik
netcat (nc) -New entry!
dd - least preferred due to complexity.

I am on home network. So, it's the connection stability concern more than speed.  I am not worried about speed at all.

I am leaning towards FSArchive. And I saw it has gui as well called qt5-archiver
What is preference? with GUI or without?

---

### Post by TheFu on 2018-05-03
dd isn't complex.  It is stupid.  It moved bytes, 1 at a time, from an input to an output.  Bonehead.  The danger comes when people don't understand the output and write to the wrong place.  dd can easily wipe an OS or clone a disk or clone a partition or copy input from almost anything to a file, partition, whole disk, or any output device like a video card, network card, serial port, or to /dev/null, if you don't want to see any output at all.  Bonehead.  

I've never used a GUI for these things. Can't say what does or doesn't work.  I use dd a few times a month, but the last time I used fsarchiver was over a year ago.  My daily backups are done using rdiff-backup.  About once a month, I need to restore something from those backups.

nc - netcat is mainly used as a hacker tool. It is bonehead and useful, but because it works over an unsecured network connection, might not be smart to leave on a system. Hackers love it when tools they need are pre-installed.

For all the time spent asking questions here, you could have tried all of these options already. Just sayin'.

---

### Post by sp40140 on 2018-05-03
@TheFU. 
I have settled on FSArchiver. Will update with verdict once done.
Thanks for your input.

---

### Post by sudodus on 2018-05-03
I think you lost the option Clonezilla, which is way better than dd.

Anyway, good luck with fsarchiver :-)

---

### Post by VMC on 2018-05-03
> **sp40140 said:**
> @TheFU. 
I have settled on FSArchiver. Will update with verdict once done.
Thanks for your input.
That's the one I now use all the time. I have a script using fsarchiver, to save all my linux distros.

One major drawback is: don't use fsarchiver on ntfs(windows) partition. There's a warning on fsarchier's web site about this subject.

Clonezilla to the rescue then. Regarding Windows clone.

---

### Post by rsteinmetz70112 on 2018-05-03
Since it is a new drive I'd use ddrescue to clone the drive. If it works you can then use gparted to make new partitions or expand the old ones. 
Note that if you use a Ubuntu Desktop Try or Install iso you will need to install ddrescue.

If ddrescue doesn't work or you want to change the filesystem type or partition scheme you can use gparted set up the partitions and filesystems then use rsync to copy all of the files.

If you use either I'd recommend running Ubuntu from a live DVD or USB especially for the root partition so they won't try to copy all of the tmpfs and other stuff.

---

### Post by HermanAB on 2018-05-03
Note that if you just want to copy a disk on a single machine, then there really isn't any difference between cat and dd.  Cat just has fewer confusing options and is usually used with no options at all, which makes it seem simpler than dd:

Good old kitty:
# cat < /dev/sda > /dev/sdb

versus:
# dd if=/dev/sda of=/dev/sdb bs=1M

This works, because on Linux, most devices behave similar to files, so any program that can read/write a file, can also read/write a block device.

Netcat is a kind of networked version of cat.  It also has many confusing options, but the defaults usually work fine, so it seems simple.  It is good when you want to copy a disk from one machine to another machine and it is on all Linux install images, so it is quite handy.

You could also copy a disk with many other programs, such as tar, head, or even with tail - or over a network with scp or ftp, but I'll leave that as an exercise to the reader!

---

### Post by sp40140 on 2018-05-03
> **HermanAB said:**
> 

Good old kitty:
# cat < /dev/sda > /dev/sdb

versus:
# dd if=/dev/sda of=/dev/sdb bs=1M

This works, because on Linux, most devices behave similar to files, so any program that can read/write a file, can also read/write a block device.


So what you are saying is to just plug in a new (destination HDD) on the same machine. And just run cat /dev/sda /dev/<mount point of dest drive>
**Shouldn't the active/live mount/os create confusion/problems?
Once this is successful, I can just remove the old (source) drive, plug in the new one (dest) and run the machine as if nothing changed?

---

### Post by TheFu on 2018-05-03
No. You must boot from a live-CD/Flash drive and then use whatever cloning method/fsarchive from that temporary environment. That's the only way to be certain.

But, yes, cloned disks can't be safely mounted inside the same running machine.

---

### Post by monkeybrain20122 on 2018-05-03
> **sp40140 said:**
> So what you are saying is to just plug in a new (destination HDD) on the same machine. And just run cat /dev/sda /dev/<mount point of dest drive>
**Shouldn't the active/live mount/os create confusion/problems?
Once this is successful, I can just remove the old (source) drive, plug in the new one (dest) and run the machine as if nothing changed?

To avoid the confusions caused by so many ways, this is your safest bet. Plugin a hd to hold the clone(a .fsa file) Fire up fsarchiver and clone your source into a .fsa file in the hd you just plugged in. Fsarhiver has the -a  -A options for the savefs command so you can clone in the background while still working on your computer. just don't do update or anything that would alter the configuration of the file system being cloned. To restore to same or different machine, boot off a liveusb, install fsarchiver,it works since there is no need to reboot the liveusb (or you can make a liveusb using the [systemrescue]("http://www.system-rescue-cd.org/") disk which has fsarchiver in it), attach the hd where you store your .fsa file (s) (the "clone") to the then restore the clone to the partition you want, that is it.

There are some very technically advanced people here who would tell you all kinds of low level techniques (i.e without extra software)  just because they can, but I will stick to something fast, easy and reliable to just get the job done.

And one more time, if you have to ask about it, then dd and friends are not for you. You can also clone with tar or whatever that copy files, that's true, but they are not as  straight forward as they seem and there are caveats about how the file system is organized and something like that iirc and you may have to edit some files before your clone is bootable, there used to be long tutorials somewhere in this forums. Also I don't know how long plain copying will take.

**Edited:**  [qt5-fsarchiver]("https://launchpad.net/~dieterbaum/+archive/ubuntu/qt5-fsarchiver") is not as flexible as the command line since you cannot exclude directories, but if you are cloning everything then this is the easiest idiot proof way. This is what I install for non tech friends in case they want to backup their systems. The method to restore is same as fsarchiver, you need to boot off a medium with qt5-fsarchiver installed, IIRC their sourceforge site has a restore iso (the ppa only provides the .deb) but it is basically just an old Ubuntu LTS .iso with persistence and qt5-fsarchiver preinstalled, also, you can restore the .fsa created by qt5-fsarchiver with plain fsarchiver with command line so a Ubuntu live usb with fsarchiver as above would work too.

---

### Post by sp40140 on 2018-05-04
Yes, I assumed so about the FSArchiver. Wasn't sure about 'cat'.
Anyway I burned "system-Rescue-disc" boot the live env with it and generated the back-up successfully.
It worked.

---

### Post by sp40140 on 2018-05-04
Thank you for your help.
I got to know about few more tools.

As always your input and help is greatly appreciated. 

Cheers

---

### Post by monkeybrain20122 on 2018-05-04
Good that you get it working. But two more things

1) try to restore the image, it is not good if you make a clone if it can't be restored. Here is how if you have a spare hard drive laying around (could be the same one that you store your .fsa file, as long as there is enough space).  Make an  ext4 partition (which doesn't contain the fsa file if you use the same drive), remove the internal hd, connect computer to this drive, boot from the Rescue usb, connect to the drive that contains the .fsa file, and restore it to the partition you made in the first hd. When complete, turn off computer, remove the rescue usb (and the hd that holds the .fsa file if it is a different drive from the one you restored to) then boot up off the restored system. If it works then you can be confident that the procedure works.

For this purpose I always make a minimal clone for testing before I really clone my system. This way the test .fas would be small. The minimalist clone would exclude all data files, so it is very small and can be restore to a small external hd. (that is what qt5-fsarchiver cannot do, can't exclude files)


2) For the cloning you don't need to boot from the Rescue usb. It is only needed for restoration. You can run savefs live with the -a -A options (sudo savefs -V -a -A ....) , i.e without turning off the computer and continue with your work, just no software installation, removal etc which change the configuration of the system.

---

### Post by sp40140 on 2018-05-05
@Monkeybrain (with your knowledge... maybe you should look into changing your userid.. :) or maybe you just know that monkeys have better brains)

1]I did restore it. Worked.
2]I knew about that (-A) option. But wasn't too confident running this command on live mount (also, as it was my first time). And I already had rescue-disc lying around.

Thank you again.

---

