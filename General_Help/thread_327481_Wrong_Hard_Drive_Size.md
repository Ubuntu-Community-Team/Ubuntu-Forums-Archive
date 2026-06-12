---
title: "Wrong Hard Drive Size"
date: 2006-12-29
forum: General Help
---

### Post by Steve S. on 2006-12-29
I'll try to keep this brief.

After a recent upgrade to Edgy.  I have an internal backup drive that I decided to upgrade from 40 gigs to 300 gigs.

The same mount points seem to work.  I'm no expert with fstab, but it looks like hdb1 is the mount point that I am using.

I formated the new drive using gparted.  Worked great.  I can look at the drives with qtparted (preferred) since there is no disk-admin (disk manager) in Edgy (isn't that nice?!).  Oh, and everyone says that pysdm works, but it says I have the drives but won't give me any information on them.  qtparted seems to be the best alternative.

Anyway, I went to save stuff from my primary drive, and it tells me there isn't enough disk space to save on the new drive.  ??  I saved about 14 gigs of stuff on the new drive anyway, but it says in nautilus that I can't save much more.  No indication of a limit on disk size in qtparted, though.

So what's the deal? ** Why can't I save as much as I want from my 50 gig primary to my 300 gig backup?**

Edit: Oh, and when I click on "Computer," nautilus doesn't see the new drive.  I can access it from the mount point just fine, though.

---

### Post by Steve S. on 2006-12-29
Ok, I'm still not able to see the hard drive in the "Computer" area of nautilus, but I have figured out some of it.

According to some other threads, now Edgy doesn't do /etc/fstab like it did in the past, but it instead goes by UUID numbers (missed that memo ;) ).

I ran this to find out the UUID numbers of the drives:
```
ls -l /dev/disk/by-uuid/
```

Sure enough, in sudo gedit /etc/fstab there was not the correct UUID number listed for hdb1, so I changed it.

Now I have my 300 g hard drive to be able to save stuff on.  Don't know if this is the "correct" solution, but it seems to have worked for me now to have the backup that I want.

But, I would like to see it in the "Computer" area and am wondering if anyone has a solution for that.

---

### Post by Steve S. on 2007-02-01
Still answering myself, but that's ok.

For the record, for Edgy, instead of the infamous disk-admin that is sadly absent, I installed gparted and qtparted, both of which have their perks.

Granted, I am not mounting a drive, just trying to get info, but they seem to work for mounting drives as well.

I also installed some KDE ap. that showed VERY well everything on the drive(pretty sure it's KDE), but I can't remember the name of it (not on the Ubuntu box right now).  It showed via a great graphical interface EXACTLY where,using a colored visual representation, everything was on the drive (e.g. /home/stephen/documents is this red area...)  If anyone knows the name of that app would you please post so that others can see another good alternative to disk-admin?  Thanks.

Anyway, would love to have disk-admin on edgy, but these alternatives worked pretty well.

---

### Post by Steve S. on 2007-02-02
Found it.  The program is called "filelight."  Launch is: gksu filelight.

Here is a screen shot:

Although this thread is essentially my ramblings, if it helped in anyway, please post back.  Thanks! :D

Edit: Oh, I should mention, with filelight, when you move the cursor over a section of the hard-drive, it tells you what is on there.  Pretty cool.

---

### Post by Unterseeboot_234 on 2007-02-03
Pretty cool ramblings, my friend. Since Dec. I have re-installed Dapper for the fouth time on a brand new AMD64 box.  The last crash was I tried to install XP 64-bit on top of a ubuntu install. I learned XP install is all or nothing. It failed at the product key number so MBR was locked. No GRUB, no rescue, nothing, would get me back to /dev/sda6. And, the XP was from a sealed package that has been around our organization for some time and never used. MS said maybe we have a defective disc. They see we own the serial number.

I don't mind. I learned to build software for a 64-bit box and cleared  out un-needed packages, libs and junk software after each build. However, I've got a wacky hard drive by now. Disks Manager doesn't do anything on my machine now. I want to know more info about my hard drive before backing up this clean install and trying to clean up the mounting points.

So, thanks. And, if I ever try XP install again, I WILL have my ubuntu already backed up and put the XP on there first.

---

### Post by Steve S. on 2007-02-03
> **Unterseeboot_234 said:**
> Pretty cool ramblings, my friend. Since Dec. I have re-installed Dapper for the fouth time on a brand new AMD64 box.  The last crash was I tried to install XP 64-bit on top of a ubuntu install. I learned XP install is all or nothing. It failed at the product key number so MBR was locked. No GRUB, no rescue, nothing, would get me back to /dev/sda6. And, the XP was from a sealed package that has been around our organization for some time and never used. MS said maybe we have a defective disc. They see we own the serial number.

I don't mind. I learned to build software for a 64-bit box and cleared  out un-needed packages, libs and junk software after each build. However, I've got a wacky hard drive by now. Disks Manager doesn't do anything on my machine now. I want to know more info about my hard drive before backing up this clean install and trying to clean up the mounting points.

So, thanks. And, if I ever try XP install again, I WILL have my ubuntu already backed up and put the XP on there first.

Wow!  Don't envy you that install!  Yeah, Windows tends to do stuff like that...kid gloves are definitely required!  God's speed on getting it cleaned up!  and glad my rambling entertained. :)

---

