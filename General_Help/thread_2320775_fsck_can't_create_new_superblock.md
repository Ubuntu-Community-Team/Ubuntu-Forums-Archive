---
title: "fsck can't create new superblock"
date: 2016-04-17
forum: General Help
---

### Post by oldefoxx on 2016-04-17
I'm having a host of problems, but lets deal with 1 per post.  According to other tools suggested, my internal drive is good, but 401 days 7 hours ago it apparently got shut off or lost power when it tried to do a READ from Queued.  Since then it has reported this same problem 15 times.  That was by its history, as I didn't even know it had a history or how to find it until last night

But there are no instructions on getting rid of whatever is wrong, and while with repeated efforts using gparted with gpart installed, I can do a Data Rescue (under Device), and even have Partition do a delete, new, and then format it back as it was, then another Data Rescue,  It will seem to get back the 2nd partition, but not the 3rd..  Surprisingly the new, format, and data rescue brought back the folders and file originally there.  So the copy, which took hours, apparently did little or nothing.  I had also attempted to copy the 2nd partition's contents to the 3rd at one point, yet most of the original folders and files remained intact.  I used sudo cp -rfp /m*/*/2nd/ /m*/*/3rd/ for this effort.

I  But gparted keeps telling me when I go back to it after some time that one or more partitions have errors, and even that the partitions overlap, so the obvious thing to do is start with a new partition table and effectively strip the drive, right?  But before I do that, I need to get the contents off all three partitions, but I need another 1TB drive to hold that much data.  I don't have it, but might have to order it.  But what else can I try first?  The contents are all good, but the drive structure has gone haywire. so bad that  the following problems are now plaguing me:

Can't bring back 3rd completely, as gparted reports errors.

Got 2nd back and used it to copy to 3rd, which only brought original folders and files back for the most part.

lost use of gparted on 1st part. sp tried to use sudo apt-get remove gparted gpart parted, thinking I would just reinstall them.  But they stripped tons of other packages when I did this, and I had an unbelievable number of unused dependencies left, which I was encouraged to use sudo apt-get -y autoremove to get rid of.

Instead I decided just to copy the system folders from 2nd part over to 1st, but that turned out to be a bum idea.  I had to use sudo cp -rfp /<folder> /m*/*/1st/ it, gpart for each one. as cp will not let me exclude the /home folder and copy everything else -- at least not to my knowledge.  Which meant doing one folder at a time.  So to reduce the burden on me, I opened 3 more terminal windows and started 3 more copies of folders at once.  Bad mistake.  They collectively brought performance down to nothing.

But that was not the worse of it.  I began a text of which folders to copy, as some like /dev, /proc, /tmp and /home can be excluded.  Then without warning, I was out of disk space on 2nd part.  I had forgotten about Trash.  Now I had zero bytes left.  I could empty the Trash still, or get into terminal mode mode and do rm ~/.local/share/Trash/*,  but either it did not happen or the disk space did not free up.

With three hammered partitions now, I booted up a LiveDVD of 15.10.  I went to Try, started a terminal, and did sudo -i to become super user.  As I had deleted the swap partition as well earlier on, since it bordered 3rd and I wanted yp make sure it was not part of 3rd's problems, I now decided I needed swapat back, so started gparted. 

If I could get 3rd part back,  it was still intact, then I could boot from it.  But the LiveDVD does not include gpart,  and you cannot install it even on a temporary bases, so no efforts at data rescue can be done from  LiveDVD using gparted.  There is oly about 1.7GB used on a Ubuntu LiveDVD, so why don't they packe the rest with deb packages in case you need them.  And why do you need a network connection just to install basic ubuntu?.  You can connect to a live bot that makes it look like a network connection exists, but you need something there or the install won't fly.  

As my earlier efforts from 1st and 2nd had gotten gparted to recognize the existing partitions, and gpart had accessed them in Read Only view, I could provisionally access 3rd already in terms of copying it out, had I a place to copy it to.. It even got the format structure right (ext4), the UUID, the label, and the size.  And gpart showsd the right folders and folder names.  So I don't know why it did not go the added steps or correcting the partition table, correcting the MBR if need be, and generating a good superblock.

As it was, from the LiveDVD, I could only run the programs that came as part of the Try.  I could not load and use other packages from the LiveDVD as they were not there, nor could I find a good way to run what was already on the existing partitiond.  I tried to use chroot, but that is not allowed.  It seemed the only thing I could do was recreate the ddeleted swap partition, which I did.

I would have to get gpart after I got one of the original partitions working again.  Or maybe I xould just boot a recent install that I did to a USB thumb drive.  I had with forethought put grub2 on it.  Only it would not boot.

It apparently did not register in as a boot device.  So now all I had was the LiveDVD, and it did not have all the tools I needed on board to deal with drive problems.  It had some, which was good, but not enough.  I had alreadily learned some of the limitations in boot-drive-disk, so did not even venture to go there.

I found many instructions online as the night wore on as to what might fix the superblock peoblem and what should free up disk space on 2nd part, and nothig takes.  I find nothing that reaches out to rebuild the partition tablr based on what gparted and other utilities can unravel from the contents, is either it isn't done or people don't know what tool to use for the job.

That's when I realised I had to come online for answers, and there are few better places to ask them than here.  What do I need to try now?

As to splitting the problems up into multiple threads, that is yet to be done.  To me this is just one big problem of healing over my internal drive.  What do I have to do to make that happen, short of just starting from scratch with it?  Or is that the only route to go, in which case I will have to order a 1TB drive to connect externally.

A 1TB can be had for under $60, but I just had another laptop, modem, router all go bad on me, and ordered a digital telephone upgrade to my setup, and I need new glasses (lost my old ones), my wife needs a printer and hearing aids, so it all adds up. 

Oh yeah, an estimated $4,000 in car repairs comes into play as well, and my wife wants to travel to visit kids twice this year, and since it is her 80th birthday, it is important that she be able to.  She nearly died this year from a sudden blackout and fall, and her heart is weak, only beats 45 times a second, not the normal 60.

I'm not complaining abd I am not asking for help financially.  This is something we have to deal with ourselves.  I just want free advice on curing some problems with my hard drive.

What really concerns me with Linux is that one user can overload the partition that has /home on it by doing nothing more than copying over existing files or deleting them, and that the all the Trash or trash folders just build up content, either on the root partition or the /home partition, and both at once if they share a partition,   What is bad in my case was that deleted drives on other partitions were crowded into the user's Trash folder in two subfolders, meaning I was opening up space on the other partitions or my own (dependng on which way the copy is going), but I was adding more storage needs than I was releasing.  even on the /home partition.  There needs to be better control here as to what to trash and what to delete fo sure.

And there is no way to extend the trash to another partition or designate an alternate partition just for trash.  You ever heard of a dumpster?  Or a trash dump or land fill?  Linux needs that.  As to the ~/.local/share/Trash folder. maybe a part of every .bashrc or .profile should include a rm -rf command for anything in there that is more than a certain number of days old, unless the partition free space falls below a certain minimum, at which point the oldest trash gets tossed regardless.

A final bit of advice is don't buy hp ENVY laptops.  Great specs, nice exterior, terrible keyboard and trackpad layout. ports too close, power and LAN ports on opposite sides. ports crowded together, insufficient cooling and underpowered AC Adapter, power cord pass the adapter too short by about 2 feet so that the adapter dangles in the air. and repair shops hat to get one in because they are a nightmare to work on.  Nothing ia easy to get at, you have to take it completely apart to get to the RAM, and to remove the bottom plate on the K073ca takes 15 screws being unscrewed.  A good laptop design can get you to anything in 5 screws or less because they have separate openings for hard drive, RAM, optical drive, and battery.  Ths K073ca has 2 latches for the battery, but they are flimsy, hard to catch, not marked as to which way to lock/unlock, and the spring on the one broke in less than 10 releases and reinserts.  I've struggled for up to a half hour to get the battery to seat. pmly to have it fall out when I turned the laptop upright.

In just 4 months, during normal use as I was typing, a big POP! was heard inside and it went completely dead.  After removing the battery and checking to make sure the AC Adapter was puting out -19.5 vdc, I tried to run it just on the adapter.  It wasstill dead.  I sent it to a repair shop, and it fired up and worked for them.  I had them run it overnight and even emailed them some scripts I wrote to make it work during that time, but it was still working the next day, so I had i picked up.  Got it hooked up, and it was dead as burnt toast, but there was never any burnt smell.

So tomorrow it goes back in for another look-see.  This was one heck of a bad deal.  I bought it online through Amazon at half price as a Certified Reconditioned machine with a limited warranty, so there is no hope there.  Great specs though, but they sometimes don't tell the whole story.  Worst piece of crap I've seem in 56 years of computer technology, and I have seen some bad things before

So why include this in this post?  Because I told HP is was going to let the world know what lousy machines they are making now, and I am living up to that promise.  This is one you DON'T want, and if others fit into this category, you don't want them either.  This is like he original Ford Edsel on sterods and then some.  As least that ran, or so I heard.
,

---

### Post by dragonfly41 on 2016-04-17
Quite a long story. I've picked out a few clues.

"one or more partitions have errors, and even that the partitions overlap"

"as to what might fix the superblock problem"

"Worst piece of crap I've seem in 56 years of computer technology"

I often find myself in the position of having to repair ageing laptops for my family members. 

If your budget is very, very tight (as I read from your post) I would investigate buying just a USB container for a hard drive so that you can run Ubuntu as a USB drive.   But first check that your PC BIOS can boot up from USB port.

I would avoid repair shops which might overcharge you and instead you can invest your time in understanding how free utilities such as testdisk might help in recovering disks.

Although it is always better to use new drives I sometimes scour recycling shops to pickup older drives to be reformatted and perhaps squeeze out another year of life.

 For example research where your local government computers go to be scrapped/recycled.   You might pickup some old PC's or drives at low cost.   Or look at local auctions of company assets.  Always risky of course (caveat emptor) but you can get them at knock down prices.

Now to return to your problem let us try to fix superblock problem.

Search by google .. "repair ubuntu superblock"

[https://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/](https://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/)

You will read from that article (and others) that there are multiple backups of superblocks 

e.g. Superblock backups stored on blocks:
32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208

and you will have to run through each of  these until you hit lucky.

And in Ubuntu Software Centre install testdisk and learn how this might help you.

There is another tool .. Boot Repair .. which will help you and others in this forum to analyse your installation.

It can be also be installed from Ubuntu Software Centre.

Run this and copy here the pastebin URL which is created.

---

