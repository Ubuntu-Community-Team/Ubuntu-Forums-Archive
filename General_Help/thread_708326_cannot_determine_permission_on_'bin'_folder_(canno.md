---
title: "cannot determine permission on 'bin' folder (cannot boot)"
date: 2008-02-26
forum: General Help
---

### Post by Tuxoid on 2008-02-26
my filesystem has been having a very rough time in the past few days. It's been bad enough that I cannot boot my system (I'm forced to boot my LiveCD). Recently I have been using the GParted LiveCD to fix (no luck).

It all started about a week ago where the filesystem had been mounted 39 times without being checked. About half way through the check it spews out several errors. Once the scan finishes, I'm left at a command line. I can either log in as root to fix it, or press Ctrl+D to reboot the machine. So, I open my CD ROM drive, plop in the GParted disk, and press Ctrl+D. Once I'm booted up into GParted, I perform a check on my drive. That check completes without a hitch. I reboot, my machine successfully loads and I go into GNOME. I unplug my laptop and start playing some flash games online. I get so caught up in the games, my laptop shuts down since it has run out of power. So I plug it in, boot it back up, it runs another filesystem check, and tells me there's journaling issues. I'm thinking to myself "&*^%, GParted can't fix journaling!". I run the GParted anyway out of desperation, and at the end of the scan it tells me something didn't go right (probably journaling). It tells me to save details, I press 'Save Details' and GParted locks up. So I manually power down my system and boot it back up. It loads up to the login screen, I log into GNOME, it's broken, log out, I log into KDE 3.5, it's broken, log out, then, out of desperation, I log into XFCE, it's fine. It took me a day and a half, but I get GNOME and KDE 3.5 back up and running. The next day, my filesystem's superblock is broken, so GRUB won't boot the system. somehow, by about 9:00pm, I'm able to get at least the loading screen to show as GRUB somehow loads my system. But it doesn't get much farther. It spews out a warning saying basically it cannot access /bin/bash.sh (Permission Denied). I frantically start up the GParted LiveCD, I see that it no longer says there is a damaged superblock, run a check on the filesystem. After half an hour, the scan cuts out with the same error I experienced with GParted the time I scanned due to journaling issues. I'm then thinking "Okay, something is seriously messed, I should mount my drive with the Gutsy LiveCD and take a look at /bin". I boot up my LiveCD, mount the drive, and looking at the properties for the 'bin' folder it's not recognizing it as a folder. The type is 'unknown type' and under Permissions, it says it cannot determine the permissions. so I try, chown, no luck, chmod, no luck, even gedit, no luck. I think, "But wait, that is some sort of interaction with the drive. I should try boot it", again, no luck.

I am sitting here with not a single clue as of how I can get the 'bin' folder uncorrupted. I almost feel like running 'sfdisk -V' but I am scared out of my bloody mind to do so. I have also thought copying the 'bin' folder from the LiveCD but that most likely won't work. I'd google something, but I don't even know what to search. The problem seems so specific.
I also do not want to reinstall Ubuntu, as I have a lot artwork that has taken me months to make.

Anyone have any ideas of how I can recover my 'bin' folder, without a reinstall.

I'm on Gutsy, I have never edited fstab, and I'm at wits end.

---

### Post by devosion on 2008-02-26
I am not all to familiar with the problem going on here but it looks like it may come down to doing a reinstall in the end. I'd take advantage of the fact that you can access your drive via live CD and begin backing up your information. 

If you have installed Ubuntu on a different partition than your personal information then you can get away with the reinstall without loosing everything. Just make sure you specify the correct partition, /, that you are reinstalling on while leaving your other partitions alone.

If this isn't the case then backing up is the best way to go, and then attempting a reinstall. This issue sounds very strange. Wish I could be of more help.

---

### Post by Tuxoid on 2008-02-26
I can only back up via DVDs. If I have the LiveCD in their, I've lost my only option. The only thing I can think of is installing Ubuntu using the 52GB free space left on my drive, boot into the new installation, back up the stuff i need from the old installation, and install Ubuntu a third time to use the entire disk. Anyone know if this will cause issues?

---

### Post by lswest on 2008-02-26
hmm, do you have a USB pendrive?  if you do you could either put your liveCD on the pendrive, or install something like BackTrack on it, so you can burn the backup to your DVD

about a second install on the free space, it should work, GRUB might be a little messed up, but you can't boot into your old partition anyways.  Once you copy it over, you could either re-install, or just delete the old partitions and re-size the new install off either the liveCD or the gparted LiveCD

---

### Post by Tuxoid on 2008-02-26
Thank you very much for your help. I will use the GParted CD and resize the partition

---

### Post by lswest on 2008-02-26
no problem, glad i could help^^

---

### Post by Tuxoid on 2008-02-26
I tried GParted. It won't resize the partition because it cannot resolve the issues on the partition. I have a USB pendrive but it's only 128MB, I can't fit the Ubuntu iso on it.

---

### Post by lswest on 2008-02-26
if i remember correctly 128MB is enough for something like Damn Small Linux, maybe give that a try?

---

### Post by Tuxoid on 2008-02-26
I never figured that out, but I found another way around backing up my data. The problem now, I can't get Gutsy to install (or even make a ext3 partition for that matter). I've deleted the broken partition, but I cannot for the life of me make a new ext3. I have also noticed 7GB of information not being factored as free space by the LiveCD GParted. I have a 100GB (according to my BIOS and the GParted LiveCD) drive but it says there's only 93.16GB of unallocated space). I have no idea what those 7GB could be or how the remove them. GParted doesn't list any 7GB partitions or anything of the sort.

---

### Post by Tuxoid on 2008-02-27
does the deletion of an ext3 partition delete the 5% super-user space on the partition. That may add up to some of the missing space (still nearly 3GB would remain). I am completely lost. If anyone knows anything about what I'm dealing with, I'd be glad to hear it. I've tried the, LiveCD installer, Alt CD, and I've tried to make an ext3 partition on the GParted LiveCD. I've tried changing the disk label. I have no idea what to google or what to look up on wikipedia. I have no idea what this all means having nearly 8GB unaccounted for. Hopefully it's not non-removable remnants of my old ext3 that died (which I did delete).

Update: despite deleting every partition (both the boot partition and swap), I still can see can see what I believe to be two extra partitions.
I'll post a screenshot pointing to such a problem:


[ATTACH]60959[/ATTACH]

---

### Post by Tuxoid on 2008-02-27
I am BMDMA errors on sda every time I boot the the Ubuntu LiveCD. It has also mentioned a "Buffer I/O error" on Logical Block 3 & 4 (no other blocks thankfully) Is it possible that my hardrive is totally busted? (hopefully not :( ) The LiveCD also cannot mount my Hard Drive Although it could see it before (GParted on the LiveCD also doesn't see my harddrive) I'll admit, I did some stupid things and forced the removal of some files in /dev on the Ubuntu CD (rm -rf) (I was so desperate). I just my 100GBs back and the chance to install Ubuntu 7.10 again. I'll do anything. No matter how hard it is to do, I'll learn how and do it. I just need some advice. Another thing, the GParted LiveCD still sees my hard drive But not the Ubuntu LiveCD. I also don't think the Alt CD can see my hard drive. I don't get this. I know this is an abnormally complex problem, but I have no where else to turn. When it comes to Google searches, I have no idea where to start. Wikipedia isn't much help, I can't understand the man pages that well. I'm out of options.

---

### Post by Nameless_one on 2008-02-27
The 7GB you are 'missing' are not missing at all. They weren't there in the first place. Read about it here: 

[http://en.wikipedia.org/wiki/Gigabyte#Consumer_confusion](http://en.wikipedia.org/wiki/Gigabyte#Consumer_confusion)

Although it is puzzling that GParted reports 100 GBs :-\ I might be wrong, but the numbers add up nicely.

---

### Post by Tuxoid on 2008-02-28
Okay, that seems to add up. But I am still very concerned that I cannot reinstall Ubuntu. I can't even get the GParted LiveCD to partition the drive correctly (not in FAT32, Ext2, or Ext3). The filesystem that GParted probably has the least trouble with is FAT32. After trying to partition the entire drive in FAT32, GParted tells me the contents of the filesystem are unreadable under the partition's information. When I try to format the drive as Ext2 or Ext3, it fails, giving me an error message saying I should save the details. Another odd thing, GParted is now telling me I have 93.16GB drive. Even worse yet, as I mentioned earlier, neither the Ubuntu AltCD or LiveCD mounts my drive anymore while GParted still does. I don't know if it has anything to do the "Buffer I/O Errors" on both Logical Block 3 and 4. The Ubuntu CDs were mount my drive a day and a half ago, but when I go into the Partition Editor on the Ubuntu LiveCD, it only sees my 1GB SD Card. Even when the Ubuntu CDs could mount my hard drive, they couldn't install Ubuntu because that required the drive to be formatted with a filesystem (which it fails at).

I've got a LiveCD for Debian Etch. Maybe I should put that in and see if it can mount my hard drive (I'm not going to install it though).

---

### Post by Nameless_one on 2008-02-28
I suggest you try changing things and seeing what happens. Maybe you could even borrow an HDD from someone and try wether you can mount and partition it on your machine. If you can, then your HDD is probably broken (or is the cause of the problem for some reason). There also must exist tools to check your HDD's health, but I don't know much about that.

---

### Post by Tuxoid on 2008-02-28
I'll try it on another HDD, but if the GParted LiveCD mounts my drive, why wouldn't the Ubuntu CDs? Does GParted work with drives differently?

Update: the Ubuntu LiveCD just mounted my hard drive. Although GParted on the Ubuntu LiveCD still doesn't see it.

---

### Post by Tuxoid on 2008-03-02
I checked my drive with SpinRite. SpinRite says it's nearly completely destroyed (reported to  SpinRite from my drive's SMART technology). I've taken my hard drive out of my laptop, and I have been booting off a self-customized LiveCD for about three days now. Anything that I need to save must be saved to my 1GB SD Card and eventually stored elsewhere. Looks like I'm buying a new hard drive :( .

---

### Post by Tuxoid on 2008-03-08
I'm still trying to patch things up. It may sound totally illogical, but something doesn't seem right. I didn't try another hard drive in my machine but I have noticed that the errors don't appear when I take my hard drive out of my machine. I have booted my Debian Etch LiveCD, and it complains about different logical blocks than the Ubuntu CDs. It mentions logical blocks 0, 3, and 5 having "Buffer I/O Errors". Is it not loading the same init system on Debian? I don't believe the GParted LiveCD mentions any "Buffer I/O Errors". I know that the GParted CD is based off Gentoo, which has some differences in its init system, but nonetheless, this seems very inconsistent. I looked up the stats on my hard drive and it definitely does not seem like I have done anything to make it fail. Here are the stats on my drive from the Manufacturer's website:

[http://www.fujitsu.com/global/services/computing/storage/hdd/mhdd/mhv2040at-mhv2120at.html]("http://www.fujitsu.com/global/services/computing/storage/hdd/mhdd/mhv2040at-mhv2120at.html")

I have ran badblocks on the GParted CD with startling results. It showed 2 million bad blocks. This cannot be accurate. It would seem that it would only be possible to have to 2 million bad blocks if there was a head crash on one of my platters. But then again, unlike a head crash, it's not getting any worse. Also, according to the stats on the manufacturer's website, it would be very hard to cause a head crash with regular use. Also, I've only had this laptop for a year and a half, so it doesn't seem that age has anything to do with it. I installed smartmontools (temporarily in RAM) last night while running the Ubuntu LiveCD. This was after making an Ext2 partition of 86GB on my hard drive on GParted LiveCD. It seems that making partitions not taking up the entire drive work (yet they won't grow). Anyway, Ubuntu was able to see the partition, but it had no listing of "sda" under the "/dev" folder as if it sees the partition but not the drive the partition is on. I ran smartctl on the partition, and my drive or partition (I have no idea which it's looking at) was marked as
passing the test on a run of "smartctl -H". I tried running "smartctl -a", but I can't make any sense out of the output (even after reading the man pages). If useful, I can post the output.

---

