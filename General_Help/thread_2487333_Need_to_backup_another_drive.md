---
title: "Need to backup another drive"
date: 2023-05-30
forum: General Help
---

### Post by jgw on 2023-05-30
I need to backup two separate drives.  One has some data I want to save and I would also like to backup my home directory as well.  I am already backing up the data but I see no way to backup a different drive.

Thank you............

---

### Post by ajgreeny on 2023-05-30
Are all these drives in the same machine and OS?
Is the backup disk external USB?
What backup software do you intend to use?

All you probably need to do is backup the separate drives' contents to either separate folders or separate partitions but tell us all the detail you can and we'll try to help.

---

### Post by jgw on 2023-05-31
separate drive - two need to backup to another.  I posted this in the hope that somebody knew of a program that had such a backup program.  Obviously, there isn't one.  Oh, well, I will figure something out.

Thanks for the replies!

---

### Post by ajgreeny on 2023-05-31
I think you are overcomplicating this.
I backup my own user files from mg home to a 2T USB external disk's first 1T partition and I also do a similar backup of my wife's own user files from her home to the second 1T partition on the same disk.

You just need to point the backup software app you use to the correct destination and it will work as you expect.

---

### Post by aljames2 on 2023-05-31
> **ajgreeny said:**
> Are all these drives in the same machine and OS?
Is the backup disk external USB?
What backup software do you intend to use.

As ajgreeny asked, this information can help us help you with options you have in terms of backup tools.  Knowing the type of file system(s) your data lives on matters, as well as the  OS you want to use the data on.

There are many tools.  I do nothing on Windows other than QuickBooks at my office, and a separate gaming rig at home for some PC steam games I still have.  So I do not have a use for any windows backup software.  So on the Linux machines I use rsync from the command line to create a second or third copy of folders or storage devices.  I do some other things when it comes to backing up system files, but that doesn’t appear to be what you were asking.  There are many many other copy or backup tools, so perhaps engage with us more and you may pick up on some good suggestions.

---

### Post by mIk3_08 on 2023-06-01
> **jgw said:**
> I need to backup two separate drives.  One has some  data I want to save and I would also like to backup my home directory as  well.  I am already backing up the data but I see no way to backup a  different drive.
Thank you............
Please run the command below and show us the results here in thread wrap with code. Regards and cheers
```
lsblk -e 7 -o name,fstype,size,fsused,partlabel,mountpoint
```

---

### Post by TheFu on 2023-06-01
> **jgw said:**
> I need to backup two separate drives.  One has some data I want to save and I would also like to backup my home directory as well.  I am already backing up the data but I see no way to backup a different drive.

Thank you............

Every backup tool that I know on UNIX can do this.  It reads like you have 2 places for source files and 1 place you'd like them backed up into.  That's pretty trivial if you only want 1 copy and no space-saving versioning involved.

Use 2 rsync commands (or grsync if you want a GUI), but why?

```
rsync -av {SOURCE1}/    {TARGET}/first-directory
rsync -av {SOURCE2}/    {TARGET}/second-directory
```

Pretty easy.  If there are different user ids involved or you want to exclude some areas in any part of the {source} areas, things can be more complex, but the general commands are like above.

For example, I have some media files on disks.  I can't afford enough storage to have more than 1 backup copy.  For normal office documents or OS files, I do have lots of versions (usually 120-180 days of versioned backups). Anyway, the exact command I use to copy media files is:
```
#!/bin/bash 

rsync="/usr/bin/rsync"

EXCLUDES="--exclude **/.Trash* --exclude lost+found --exclude ZCS-2012"

rm -rf /d/D[1-7]/.Trash-1000  # I don't want to copy trash

ionice $rsync -ar --stats --info=progress2 $EXCLUDES --delete-during   /d/D1/   /d/b-D1/
ionice $rsync -ar --stats --info=progress2 $EXCLUDES --delete-during   /d/D2/   /d/b-D2/
```

/d/D1 is {SOURCE1} and /d/D2 is {SOURCE2}  Because of the sizes involved, I have to TARGET disks, but if the data fit onto 1 disk, I'd just create a subdirectory for each source area on the target.
These drives are all directly connected to the same computer via SATA, eSATA or USB.  For network backups using rsync, I'd change the '-ar' to '-arz' so that compression is used.  Compression on local copies is useless.

Hope this helps.

---

### Post by jgw on 2023-06-01
Thanks for all the responses!

I guess I am not clear.  I have a system that has 4 separate hard drives.  Each drive has 4tb.  I want to copy specific files from two drives to two other drives.  I currently have the backup program that comes with ubuntu 22.04   I want to backup each drive to another.   Two of the drives are not full but neither drive has enough room to hold backups.  I started with just two drives but they both are now too full to hold any backup data.   So, I got myself two more drives to handle the backup.  I was hoping that somebody knew of a backup program that could do this.  If there is not anything that will do that I guess I could write one but am lazy and haven't written anything in quite a while.  All the drives are internal.

For the heck of it.  I can remember a time when a 10gb drive was around 400.00 - things have changed a bit and now ssd's seem to be be the memory of choice and hard drive prices, I think, are going down.  Things are changing!!

---

### Post by ajgreeny on 2023-06-01
I believe between us we have already told you exactly how to do what you want; TheFu even showed you some example commands using rsync but we can do no more as we don't know what your source and destination folder pathways are.

I still feel you are making this far more complicated than it is; at its simplest you can use rsync so have a look at ```
man rsync
``` and it should explain a lot more for you.

---

### Post by dragonfly41 on 2023-06-01
Since I have multiple HDD/SSD devices I invested in two of these with own power supply
[https://www.startech.com/en-gb/hdd/duplicators](https://www.startech.com/en-gb/hdd/duplicators)

But not cheap. You also need caddies so you just plug in the devices into bays.

And switching topic back to rsync and dry run .. try the GUI grsync and dry run.

---

### Post by jgw on 2023-06-02
Thanks for all the help!

Ran into a little problem.  Suddenly one of my drives was running at 158 degrees and failing.  I immediately started backing up the drive and it took me a night and almost another day and the thing was too hot to touch before it was done.  I still have to do more testing on the backup to see if I really got everything and have been at that most of the day (everything is fine so far).  Now I want to test the drive.  Its strange.  For instance, the Disk program can't access the disk smart stuff.  Trying to figure out just how to test it and have spent a lot of time just reading about testing and getting noplace.  I expect I will end up using rsync but have to study on it as it seems to do everything.  

The strange thing is that after it cooled down I took a look and everything seems to still be on that drive.  

I also ran fsck on the bad drive.:
greg@greg-HP-Compaq-8200-Elite-CMT-PC:~$ sudo fsck /media/greg/3tb
[sudo] password for greg: 
fsck from util-linux 2.37.2
e2fsck 1.46.5 (30-Dec-2021)
fsck.ext2: Is a directory while trying to open /media/greg/3tb

The superblock could not be read or does not describe a valid ext2/ext3/ext4
filesystem.  If the device is valid and it really contains an ext2/ext3/ext4
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
 or
    e2fsck -b 32768 <device>

Obviously things are not dandy.  I can't figure out if its a software or a hardware disaster but I suspect the hardware.  Can't figure out what I should do next with that one.  I have had it running fine for a while and just checked.  Disks no longer sees it nor does anything else.  Basically it warmed up and went away.  Suspect its done.

Then I read dragonfly41's thought and that set me off studying on stuff in ebay.  My wife uses windows and she has an automatic backup drive that works easily and well.  There are a lot of people selling a llot of stuff that just confuse.  Just saw gparted on sale, on a stick for 18.00  and I can't figure out why anybody would want that.  Oh well.......

Got to chatty, apologies - thanks to everybody...........

---

### Post by TheFu on 2023-06-02
fsck needs to be run on the file system device, not the mounted area.  Hint:  umount the file system, then use fsck on a partition under /dev/sdXY

Never run fsck on a mounted file system. Never.
I'll sell you a CDROM gparted distro for $17, plus S&H, probably $6.95 for USPS 2-day with tracking.  ;)

---

### Post by jgw on 2023-06-03
TheFu:

Thank you for the reply.  Hopefully I haven't wrecked anything.  I'm not sure why I would want a CDROM gparted as well as any number of other programs.

Oh, the drive I did that on is toast.  When it heats up it REALLY heats up and then dies.   That was the problem when I removed it so I don't think fsck is the culprit but could have been.  The operating system sent me a message that it was going bad.  I had barely enough time to back it up but, as far as I can tell, it got it done.

Thanks again!!

---

### Post by TheFu on 2023-06-03
Based on the heat numbers, I'm guessing it was an SSD without a heatsink?
Spinning HDDs don't get that hot - ever.

---

### Post by jgw on 2023-06-04
Nope, it was a 4tb sata 64mb cache md4000gsag472dvr surveillance Hard Drive. Its kinda interesting.  When its cold I can turn it on and see all the stuff on it, etc. but, after a little bit it just stops.  I still have it and am trying to figure out where to get a screwdriver that will fit the screws so I can take it apart and peer at it before I get the magnet (drives have really great magnets).  I give the magnets to friends who put them on the end of fishing lines and go looking for stuff off piers.  Its kinda fun and one can find some pretty interesting stuff that got lost in the water.  The local public pier is a good place to start.    

When I took it out of the computer  I waited about 20 minutes and it was still too hot to touch.  Pretty strange............

---

### Post by sudodus on 2023-06-04
158 degrees Celsius or Fahrenheit? (Even 158 degr Fahrenheit = 70 degr C (moderate sauna temperature) will burn the fingers).

Is there a problem with cooling? In that case, can you improve the cooling, at least temporarily?

Anyway, it seems you need to backup what can be saved and after that check if the drive is OK, for example with **[FONT=Courier New]smartctl[/FONT]**.

---

### Post by jgw on 2023-06-04
thanks for the reply.......

it was 158 fahrenheit and the computer told me along with telling me that the drive was failing bigtime.  The drive is toast.

---

### Post by jgw on 2023-06-05
dragonfly41

I have learned qujite a bit on this one and I appreciate everybody's effort.  Now I'm going to have to start messing with rsync.

Thanks again!

---

