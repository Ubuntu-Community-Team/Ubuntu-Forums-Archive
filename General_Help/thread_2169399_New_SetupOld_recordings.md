---
title: "New Setup/Old recordings"
date: 2013-08-21
forum: General Help
---

### Post by jim_collins2 on 2013-08-21
I had (created) some problems with my last mythbuntu installation.  I had a login loop that I could not correct.  I believe it was memory related (the computer's memory, not mine).  I got a shiny new 4TB hard drive and a new processor for the computer.  I am reinstalling mythbuntu on the new drive.  I disconnected the old drive for now until I get everything back to normal.  My question is, what is the best way to transfer my old recordings from the old hard drive to the new one?  This is a "newer" computer in that it does not have the ribbon that goes from hard drive to hard drive, it has smaller red cords.  Is there a way to make the old drive the "slave" or do you even do that anymore or ever in linux?  I also have puppy linux, so I could use that if necessary.  I said I have it, not know how to use it, so please tell me what steps are necessary.  I've been a Windows guy and trying to make the move slowly.  I appreciate all help!

---

### Post by r_avital on 2013-08-22
Hi Jim,

The drive with the narrower red cords is a SATA drive, and your old drive with the ribbon, that needs to be set as master/slave is an IDE drive.

You can buy an IDE/SATA adapter, it goes on the back of your old IDE drive.  It's very affordable (I don't want to say "cheap" but it is) usually, and it should come with a small power cord/adapter, because when you use it, BOTH the adapter AND the old IDE drive need their own power.  So, you'll need to split power from one of your available "molex" power connectors.  And you will probably need to set up the IDE drive jumper as Master.

With SATA drives, the master/slave/cable-select terminology is obsolete, you never have to worry about that again.

Here's a single-unit arrangement that should work well, as long as you understand I'm not advertizing, this is just to give you an idea (this one seems to not require any cables other than the SATA power and data connectors -- the red ones).
[http://www.newegg.com/Product/Product.aspx?Item=N82E16812240012](http://www.newegg.com/Product/Product.aspx?Item=N82E16812240012)

you'll be able to continue to use your old drive, if you wish.  Linux will recognize it.

---

### Post by jim_collins2 on 2013-08-22
I mislead you.  Both hard drives have the red cords.  I just installed the mythbuntu and it told me to restart.  Then it said verifying DMI Pool Data.......
[COLOR=#000000]error: out of disk.[/COLOR]
[COLOR=#000000]grub rescue>

When I restart the same thing happens.  I watched the boot sequence closely and went into the bios.  My computer sees the new drive as a slave and no master.  I assume that is the problem.  How do I correct this.  I have the old drive completely unplugged so let's just stay concerned with the new install and making it the master.[/COLOR]

---

### Post by jim_collins2 on 2013-08-22
Could it have anything to do with it being 4TB?  It is Seagate and it says to jumper the first two pins to limit data transfer to 1.5 Gbits per second if any of that helps.

---

### Post by jim_collins2 on 2013-08-22
I have the bios on the screen and now I realize it says the following:
IDE Channel 0 Master [ None]
IDE Channel 0 Slave   [DVD-RW IDE1004]
IDE Channel 2 Master [ None]
IDE Channel 3 Master [ST4000DM000-1F2168]
IDE Channel 4 Master [None]
IDE Channel 5 Master [None]

So the DVD is he only slave, but it has the new drive in Channel 3.  Does that make any difference?  Does this mean that it is trying to boot from the empty DVD drive?  How do I move the new drive above the DVD drive?  I tried to change the boot sequence but got the same result.

---

### Post by jim_collins2 on 2013-08-22
just to be sure I swapped the old drive back in and used the cords exactly as they were - It recognizes the old drive in the exact location as the new drive (IDE Channel 3 Master) and it seemed to boot fine (until I get to my original problem).  So the problem seems to be in the new drive.  There did not seem to be any problems reading or writing to it during installation.  I'm at a loss now.

---

### Post by jim_collins2 on 2013-08-22
I did some searching and found that the boot partition should not exceed 137GB. Found that info from this site [http://www.dudek.org/blog/220](http://www.dudek.org/blog/220)  Well I was going to try to change the partitions on my drive, but I really don't know how.  I was able to get the information of the current setup.  [COLOR=#000000]Here is the data:[/COLOR]
[COLOR=#000000]/dev/sda[/COLOR]
[COLOR=#000000]Device---------------------Size--------------Used[/COLOR]
[COLOR=#000000]free space----------------1 MB-------------[/COLOR]
[COLOR=#000000]/dev/sda1 biosgrub------1 MB-------------unknown[/COLOR]
[COLOR=#000000]/dev/sda2 ext4-----------3999713 MB----65465 MB[/COLOR]
[COLOR=#000000]/dev/sda3 swap----------1070MB---------[/COLOR]
[COLOR=#000000]device for bootloader installation:[/COLOR]
[COLOR=#000000]/dev/sda ATA ST4000DM000-1F21 (4.0 TB)[/COLOR]

[COLOR=#000000]I can double click on any of the lines above and then a new menu pops up with mount points and other vocabulary I am not familiar with.  It appears that I have just one very large partition and 4 small ones.  Comments????/[/COLOR]

---

### Post by r_avital on 2013-08-22
Okay, lots of info here, let's see if we can get what's relevant and what is not.

First, I want to understand correctly: How many drives do you have right now, including HDD, and CD/DVD?
Second, do they all connect exclusively via those smaller red cords?  They don't have to be red, it's just that they usually are.  If so, then you have only SATA drives.

With SATA drives, there is no master/slave relationship, as far as I know, but clearly your BIOS is showing you that your DVD is "slave."  Does your DVD connect with a wide, flat ribbon cable?  If so, it's not SATA, it's IDE, and there's a set of pins near the connector in the back, with one set holding a tiny jumper.  There should be a diagram, engraved on the top or bottom of the drive, near the connector, with markings such as "MA" for master, "SL" for slave, and "CS" for cable-select, and that should indicate where the jumper should be in order to make the drive a master drive.  However, that would be master on one particular channel, and will not affect any drive connected on any of the other channels, such as your HDD, which appears to be "ST4000DM000-1F2168"

Is this "ST4000DM000-1F2168" your 4TB drive?  Is this the one on which you've installed Mythubuntu?  Is this the one that fails to boot?

I've read the link you posted, it talks about computers with older BIOS, regarding that 137GB limit.  I have a 1TB drive, Ubuntu installed on a 300GB partition designated as Root, and 600GB partition designated as Home.  My motherboard is about 3 years old, so I suspect my BIOS is not newer than yours and probably older.

Let's go one step at a time.  At this point, the Operating system doesn't boot successfully, correct?  If you have no meaningful data on that, I would start with a reinstall of Mythubuntu, BUT: When you get to the point where the installation asks you how to install and how to divide your HDD, do the following:

1. Select the option labeled "Something else"

2. This will take you to a screen where you can divide up your disk into partitions.

3. On that screen, select the current partition, increase the size if you want, select to reformat into an EXT4 partition, and select to map it as "/" (which is root).  Do not select "/boot" -- I know it can be confusing, just select "/" for now.  This will put Xubuntu on a single partition, it's up to you how large you want to make it.  If, for instance, you later want to install another Operating System, like another flavor of Ubuntu, or Windows, you can do that on the remaining free space.  You will get a warning that all your existing data on the HDD will be lost.

Also, make sure there is one partition (usually quite small) set up as "Linux Swap" -- doesn't matter what it's called.

4. If at that point you have exactly one HDD installed in the system, the name of the HDD under linux will probably be "sda" and the first partition would be "sda1" (a second HDD would be "sdb" -- partition 1 on "sdb" would be "sdb1" and partition 2 would be "sdb2" etc.)  This is the naming scheme.  Don't be alarmed if you only see "sda4" or "sda2" on that map, what matters is that the combination of "sdX" and Y is unique, where X is a letter and Y is a number.

5. MAKE SURE, on that screen, at the bottom, there's a box to select the drive on which to install the "MBR" (Master Boot Record), make sure it shows "sda" - NOT "sda1" NOT "sda2" or anything after "sda" (again, assuming your HDD is recognized as "sda"

This is where GRUB will be installed, and this should give you a bootable Operating System.

I know this is a lot to digest, so take your time.

---

### Post by jim_collins2 on 2013-08-22
> **r_avital said:**
> Okay, lots of info here, let's see if we can get what's relevant and what is not.

First, I want to understand correctly: How many drives do you have right now, including HDD, and CD/DVD? 
**I only have the two drives hooked up.  One is the HDD and the other is the CD/DVD.  There are two red cords from the mother board.  One goes to the HDD, the other goes to the USB port located on the front of the computer (nothing is plugged into this drive - ever).  The CD/DVD has a separate cord (not red) to the mother board.**
Second, do they all connect exclusively via those smaller red cords?  They don't have to be red, it's just that they usually are.  If so, then you have only SATA drives.  
**I do not believe the CD/DVD is SATA.**

With SATA drives, there is no master/slave relationship, as far as I know, but clearly your BIOS is showing you that your DVD is "slave."  Does your DVD connect with a wide, flat ribbon cable?  
**YES. **
If so, it's not SATA, it's IDE, and there's a set of pins near the connector in the back, with one set holding a tiny jumper.  There should be a diagram, engraved on the top or bottom of the drive, near the connector, with markings such as "MA" for master, "SL" for slave, and "CS" for cable-select, and that should indicate where the jumper should be in order to make the drive a master drive.  However, that would be master on one particular channel, and will not affect any drive connected on any of the other channels, such as your HDD, which appears to be "ST4000DM000-1F2168"  
**I'm farmiliar with everything you said here and agree with it.  I have experience with older drives (making them Master and Slave).**

Is this "ST4000DM000-1F2168" your 4TB drive?
**YES **
Is this the one on which you've installed Mythubuntu? 
**YES**
Is this the one that fails to boot? 
**YES**

I've read the link you posted, it talks about computers with older BIOS, regarding that 137GB limit.  I have a 1TB drive, Ubuntu installed on a 300GB partition designated as Root, and 600GB partition designated as Home.  My motherboard is about 3 years old, so I suspect my BIOS is not newer than yours and probably older.

Let's go one step at a time.  At this point, the Operating system doesn't boot successfully, correct?  
**This is correct.**
If you have no meaningful data on that, I would start with a reinstall of Mythubuntu, BUT: When you get to the point where the installation asks you how to install and how to divide your HDD, do the following:

1. Select the option labeled "Something else"

2. This will take you to a screen where you can divide up your disk into partitions.

3. On that screen, select the current partition, 
**What is the current partition?  Is it the one that is considerably larger than the others or is it the first one listed?  **
increase the size if you want, select to reformat into an EXT4 partition, and select to map it as "/" (which is root).  Do not select "/boot" -- I know it can be confusing, just select "/" for now 
**I'm not home, but will do this when I get there**.  This will put Xubuntu on a single partition, it's up to you how large you want to make it.  If, for instance, you later want to install another Operating System, like another flavor of Ubuntu, or Windows, you can do that on the remaining free space.  You will get a warning that all your existing data on the HDD will be lost.  
**This computer is for mythbuntu only.  It will be my DVR for as long as I can keep it working so no other programs will necessarily be installed here.  If it makes sense, as I said earlier I have puppy Linux.  Should I save space to install something like that for troubleshooting purposes in the future?**

Also, make sure there is one partition (usually quite small) set up as "Linux Swap" -- doesn't matter what it's called.  
**I believe that is there already, but I will double check.  It looks like there is one labeled swap, but not Linux Swap.  Do I need to do anything to change this?  It looks to be 1070 MB in size, is that ok?**

4. If at that point you have exactly one HDD installed in the system, the name of the HDD under linux will probably be "sda" and the first partition would be "sda1" (a second HDD would be "sdb" -- partition 1 on "sdb" would be "sdb1" and partition 2 would be "sdb2" etc.)  This is the naming scheme.  Don't be alarmed if you only see "sda4" or "sda2" on that map, what matters is that the combination of "sdX" and Y is unique, where X is a letter and Y is a number.  
**Ok, I will only have the single HDD until EVERYTHING is working correctly, then I may get brave enough to try to copy the recordings from my old HDD to my new one.**

5. MAKE SURE, on that screen, at the bottom, there's a box to select the drive on which to install the "MBR" (Master Boot Record), make sure it shows "sda" - NOT "sda1" NOT "sda2" or anything after "sda" (again, assuming your HDD is recognized as "sda"

This is where GRUB will be installed, and this should give you a bootable Operating System.  
**It appears that this is already the case.  This is making much more sense now that it has been explained.**

I know this is a lot to digest, so take your time.  
I will work on it tonight.  The complete install took only about an hour total.  I was completely unsure about the partitioning.  How to change sizes, What is a mounting point, and what type.  The language in Windows may be a bit confusing, but usually it can be followed.  Perhaps in Linux there could be instructions as you hover your mouse over the different options?  Just a suggestion.  Thank you for taking the time to explain this, I am certainly more hopeful than I was at 2:00 a.m. last night.  I answered in blue and had a few questions of my own.  Hopefully you or someone else could shed a bit more light on those questions to give me even more confidence tonight.  Thanks again.

---

### Post by r_avital on 2013-08-22
Good feedback, Jim,

To address your questions (in blue):
**What is the current partition?  Is it the one that is considerably larger than the others or is it the first one listed?  **

The best way to explain this is to show you an image, but unfortunately, I can't post it here, probably because it's too large.  Instead, here's where you can look at it (and the whole process): [http://www.techspot.com/community/topics/step-by-step-beginners-guide-to-installing-ubuntu-11-10.172128/](http://www.techspot.com/community/topics/step-by-step-beginners-guide-to-installing-ubuntu-11-10.172128/)

This talks about Ubuntu, to the best of my knowledge it should be the same for Mythubuntu.  Look at the image in step 7-C, the window title should be "install type" - that's a graphic representation of the hard drive on which you are installing.  There are existing partitions, there is free space (not allocated, not partitioned).  If you select partition /dev/sda1 then click on the "change" button, you can change the size, change the mount-point, reformat, anything you want.  Or, you could simply click on the "New Partition Table" button and start fresh.  Either way, anything on that partition will be lost.  Take a good look at the steps you take to get to that screen.

[B]It looks like there is one labeled swap, but not  Linux Swap.  Do I need to do anything to change this?  It looks to be  1070 MB in size, is that ok?

[/B][COLOR=#000000]On this screen, swap=linux-swap. You can change the size if you want, it relates to the amount of RAM you have on the system, there are raging debates on how large to set it, I would go with 1.5 X your RAM, but I could be completely wrong.  With a 4 TB drive, you can hardly go wrong giving it too much space, so I'd start with that.[/COLOR][COLOR=#0000FF]
[/COLOR]
**If it makes sense, as I said earlier I have puppy  Linux.  Should I save space to install something like that for  troubleshooting purposes in the future?**

[COLOR=#000000]Absolutely, you might want to leave, say, 300MB free for a future install (I'm just guessing, you'd know better than me how much space puppy linux requires).  You wouldn't have to worry about allocating/partitioning that space right now, leaving it as free space should be good enough.[/COLOR][COLOR=#0000FF]  

[/COLOR][COLOR=#000000]I hope looking at that link and those images gives you a better understanding of the steps to follow.  Don't look for your DVD anywhere on that table, it won't show up, this is a screen for making partitions onto writeable media, which includes HDDs and USB drives/sticks/pendrives etc.

Throwing everything on one partition means that you would:
a - size the partition
b - format it
c - set it to the root mount-point, which on the drop-down list that shows up in the configuration window for that partition is represented by "/"

Do not forget -- the last item at the bottom of that screen, labeled "Device for Boot Loader installation" - this should be set to the HDD device itself, not any partition on it, and in the case in that image, it's /dev/sda (nothing, no number after sda) - again, could be "sdb" etc. on your system, but practically always "sda" on a system with a single HDD.[/COLOR]

Regarding your DVD:
**I only have the two drives hooked up.  One is the  HDD and the other is the CD/DVD.  There are two red cords from the  mother board.  One goes to the HDD, the other goes to the USB port  located on the front of the computer (nothing is plugged into this drive  - ever).  The CD/DVD has a separate cord (not red) to the mother board.**

[COLOR=#000000]Thanks, this explains it better.  The connection of this DVD to the motherboard -- is it a flat-ribbon cable?  If not, i.e. if it is the same width as the HDD red cord, then this is a SATA DVD drive, which is just fine.  Let's deal with partitioning the HDD first, but if you want to try and locate your DVD, you'll need to first insert a dvd/cd in it, and within a few seconds it should show up on the desktop.  If it does not, you could launch the file-manager, (let's say, nautilus), and clicking on "computer" following the path from root to /media/ -- your DVD should appear there.  It won't show up there if there's nothing in the drive.[/COLOR][COLOR=#0000FF]

[/COLOR][COLOR=#000000]It looks like I'm across the pond from you, with the attendant time-differences, but I'll keep looking here for your responses later today/tonight.[/COLOR][COLOR=#0000FF]
[/COLOR][COLOR=#ff0000][/COLOR][COLOR=#000000][/COLOR]

---

### Post by jim_collins2 on 2013-08-22
This guide is perfect and looks identical to my installation.  One wuick question.  If I get this going right then add my old HDD, how does the computer differentiate between the two - What I mean to say is how does it determine which one will be sda and which will be sdb?

---

### Post by r_avital on 2013-08-22
Hi again,

I expected things would be clearer if you could see a guide with graphic representations of your partitions.

As far as adding the second drive, you will only deal with device names such as sda and sdb and so on, when you run administrative programs/utilities that manage the devices and the partitions, like for instance gparted and parted (parted stands for "partition editor" and gparted is the graphical-front-end to that same application).  Normally, the HDD that was installed first will stay sda, and a second one should be sdb.

As far as how you see your drives on your desktop, Linux deals with drives and partitions differently from Windows.  Everything is one big directory.  A second drive will show up as a sub-directory within the top-level directory. It's a bit of a conceptual leap to make and get used to, but it really is no rocket-science To explain further:

When you run your file-manager, depending on which one you run, every directory you create, file you add, will be visible, of course, but the directory will have a single structure, regardless of how many physical drives or partitions you have.  Example:

In Windows, you could have two physical drives, and one of them could have two partitions, so you would see C:, D:, and E: and that they could mean is:

C: First and only partition on one physical drive
D: First of two partitions on a second physical drive
E: Second of two partitions on the same second physical drive

OR

C: First of two partitions on one physical drive
D: Second of two partitions on the same first physical drive
E: First and only partition on the second physical drive

Correct?  In my case, in ubuntu, I have the system installed on a 300GB partition, and the /home directory (which is where all your files, music, movies, photos etc. are located) in a separate 600+ GB partition (overkill, by the way, but deliberate).  The file manager "nautilus" shows me everything in one single structure.  A different file-manager (named dolphin) shows me the same structure, but also the two partitions as two separate drives, just like in windows.

To see the contents of the actual physical drive in a file-manager, you would open up the "media" directory, off the root (so it would be called /media), and within it, you will see your second physical drive.  If it has a label, say "recordings" then it will show it to you as /media/recordings/ and below that, all the directories on the "recordings" drive.  If it has no label, the OS will make up a name for it, like "disk" or "250GB-Filesystem" or something similar.  You will always be able to access it.

The DVD will not show up, until you put some media in it, then it will show, again, as /media/The Very Best of David Hasslehoff (assuming you inserted a CD titled "The very Best of David Hasslehoff" in the drive).  Remove it, and it will disappear from /media.  Plug in a USB drive, and again, it will show up under some name under /media/some name/ and you can access everything in it under that directory.

All variants of Linux deal with physical drives and partitions in the same way.  An installation has a fixed set of directories, and generally a non-root user has full read/write access to only /home (and everything below it), and /media/whatever writeable devices are mounted on the system at the time (this would include a blank CD/DVD as well).  The rest is read-only for a non-root user, and read-write to anyone with root privileges.

Apologies if you already knew that, but I wanted to make sure we're on the same page.

---

### Post by jim_collins2 on 2013-08-23
PARTIAL SUCCESS!!!!!!!  OK, I'm not up and running 100%, but mythbuntu is running the frontend.  I still need to setup the backend.  It just got too late last night.  So here is what happened.  I re-installed mythbuntu.  The partitions were the issue.  I had a heck of a time trying to change the size of the existing partition.  I kept reading posts on how to create new partitions in the available free space, but I had virtually no free space.  Finally (and this needs to be somewhere in the instructions - especially if you had a previous install) I DELETED the existing single partition.  That gave me the free space to make the new partitions.  I'm sure I made them larger than needed, but I never want to run into the problem of not enough disk space again.  The second issue I had was when installation completed and I removed the DVD and restarted the computer.  It made it past the point where I had the error previously, then the mythbuntu screen popped up (I did a fist pump at this point), but then it disappeared and the screen was blank for 10 minutes.  I restarted the computer with the same result.  At this point I was ready to pull my hair out and give up.  I re-installed again and this time the only change I made (and I think this is a mythbuntu only option) was to leave the TV output set to the default instead of calling out specifically my video card.  I am thinking that maybe the program was working correctly, but the output to the screen was corrupted?  Anyway after the re-install the frontend started and I watched the 480i and 1080p setup videos with no problems.  The backend setup is for the tuners and such, hoping I can get it tonight or tomorrow.  Going to ask this once again.  If I have my new HDD in now and running and I plug in my old HDD (that was once the only HDD) how does the system know which one to boot from if there is no master/slave?  I guess I'll find out this weekend.  Thank you for all your help - I am very appreciative!!!!!!!!!!

---

### Post by r_avital on 2013-08-23
Jim,

You're very welcome!  Good to hear about the progress.  

To address your question: When you made the installation, and configured your partitions, remember that setting at the bottom of the screen, "device for boot loader installation?"  If you selected sda on that, then that's the HDD where the boot record is installed, and that's where GRUB will find it an load the OS from.  Add any HDD you want, as long as they are in a format that Ubuntu supports, they'll be recognized.  

If your old HDD "was once the only HDD" it's possible that it might have its own boot loader or MBR, it's possible that your system may attempt to boot from it.  That's an easy fix, you simply set the boot order you want, in the BIOS (where you can easily recognize which HDD is which if only by the size difference).  Once that's set, and you recover your recordings from the old HDD, you can then reset the partitions on the old HDD, and never give it a boot-loader.

Note, that if you still want to install puppy-linux (or possibly Lubuntu, also very conservative on resources) as a way to get back into a broken system in case anything happens, I could be wrong, but I believe you could install it on either HDD, and GRUB should give you a choice, when you boot up, as to which OS you want to boot.  Either way, that's a wise precaution.

I am completely ignorant on the topic of your front-end and TV output.  I'd love to know more, but I won't bother you.  If you could point me to a few good sources of info and/or forums on that, that would be great.

Let me know if you have further questions, and good luck!

---

### Post by jim_collins2 on 2013-08-23
Well mythbuntu looked identical to the guide you gave me with that one exception for the TV output.  The computer needs to have a big hard drive (the bigger the better depending on how much you want to record and keep).  The best tuner (and I am no expert) is HD Homerun.  I have our over the air antenna plugged into this and this goes into the computer via USB.  I will only tell you the basics as I'm not even sure of some of the terminology.  The front end is what takes your information and drives it to the TV.  The backend is what records and manages shows.  I only have the one system set up with one TV, but you can have one master backend and multiple frontends and share common data.  Pretty much it is a poor man's DVR.  Since I do not have cable or satellite I pay about $40 a year to schedulesdirect.com and they populate the onscreen tv listing guides.  I pretty much can record any show that I could have watched on TV.  I'm sure it can do so much more than I use it for though.  I'm sure a google search for mythbuntu would answer any specific questions you might have and if you have anything that I might help with you can post it here or private message me.  I remember the first time I did it was pretty hard, but I had absolutely no exposure to Linux so I was doing it blind.  You have both Linux and general computer knowledge so it would be much easier for you.  Thanks again.

---

### Post by jim_collins2 on 2013-08-23
here is a really good site to find out about mythbuntu - I'm sure many on these forums know more though!

[http://www.techradar.com/us/news/software/applications/complete-guide-to-mythtv-947946](http://www.techradar.com/us/news/software/applications/complete-guide-to-mythtv-947946)

---

### Post by r_avital on 2013-08-23
Thank you Friend!  Enjoy the weekend!

---

### Post by jim_collins2 on 2013-08-27
Got my system up and running.  Have the new HDD doing everything - all is well with that.  I have my old HDD in the computer also.  I am using Puppy LInux to navigate and found the old recordings.  I would like to copy these to the new HDD so I can view them normally.  I cannot seem to find the location for the recordings.  [COLOR=#000000]The old recordings are in /mnt/sdb6/mythtv/recordings. I cannot locate the four recordings that I have recorded since I got the system back up and running. I cannot find a location for recordings to move the old ones into. I have he following folders on the new HDD:[/COLOR]
[COLOR=#000000]bin[/COLOR]
[COLOR=#000000]boot[/COLOR]
[COLOR=#000000]cdrom[/COLOR]
[COLOR=#000000]dev[/COLOR]
[COLOR=#000000]etc[/COLOR]
[COLOR=#000000]home[/COLOR]
[COLOR=#000000]lib[/COLOR]
[COLOR=#000000]lib64[/COLOR]
[COLOR=#000000]lost+found[/COLOR]
[COLOR=#000000]media[/COLOR]
[COLOR=#000000]mnt[/COLOR]
[COLOR=#000000]opt[/COLOR]
[COLOR=#000000]proc[/COLOR]
[COLOR=#000000]root[/COLOR]
[COLOR=#000000]run[/COLOR]
[COLOR=#000000]sbin[/COLOR]
[COLOR=#000000]selinux[/COLOR]
[COLOR=#000000]srv[/COLOR]
[COLOR=#000000]sys[/COLOR]
[COLOR=#000000]tmp[/COLOR]
[COLOR=#000000]usr[/COLOR]
[COLOR=#000000]var[/COLOR]
[COLOR=#000000]and the following files:[/COLOR]
[COLOR=#000000]initrd.img[/COLOR]
[COLOR=#000000]initrd.img.old[/COLOR]
[COLOR=#000000]vmlinuz[/COLOR]
[COLOR=#000000]vmniluz.ols[/COLOR]
[COLOR=#000000]I have looked for another directory labeled recordings so I can move them, but I cannot locate it!!![/COLOR]

---

### Post by Crusty Old Fart on 2013-08-28
look in ~/Music, which is the same as: /home/your_username/Music
```

ls -al ~/Music

```
~~~ or ~~~
```

ls -al ~/Videos

```
If you don't find what you're looking for, then just look in your home directory for another folder where they might have been saved:
```

ls -al ~

```

---

### Post by jim_collins2 on 2013-08-28
If I find my new recordings, can I just copy or move the old ones to that directory?  Will I be able to see them with my frontend and watch them normally?

---

### Post by Crusty Old Fart on 2013-08-28
> **jim_collins2 said:**
> If I find my new recordings, can I just copy or move the old ones to that directory?  Will I be able to see them with my frontend and watch them normally?
I can't think of any reason why that wouldn't work.
If you're unsure, the safest thing to do would be to copy them instead of moving them. Try to copy one of them and see if you can watch the new copy from its new location. If that works out okay, you can copy the rest of them and when you're sure the copies are where you want them and you're able to watch them, you can remove the files in the old location.

Just in case you need them, here are a few commands:

The copy command:
```

cp -p /old/location/filename.whatever /new/location/filename.whatever

```
The remove (delete) command:
```

rm /old/location/filename.whatever

```
The move command:
```

mv /old/location/filename.whatever /new/location/filename.whatever

```
Rather than using commands, you can accomplish any copying, deleting, and moving using your mouse in your file manager windows, which may be a method that is more familiar to you.

---

### Post by jim_collins2 on 2013-08-28
Yes, that is much more farmiliar to me.  I am trying to pick up on the Linux more and more, but some things in Windows are much easier.  Thank you for your help!

---

### Post by Crusty Old Fart on 2013-08-28
> **jim_collins2 said:**
> Yes, that is much more farmiliar to me.  I am trying to pick up on the Linux more and more, but some things in Windows are much easier.  Thank you for your help!

As time goes on, you may end up using the shell (terminal window) more and more. However, shell commands can be a bit intimidating for new users because they are rather cryptic. And, if you mangle a command, you may end up with unintended consequences that can be pretty disastrous. Unfortunately, there's no "undo" in the shell, so once you hit the [Enter] key, you're in for the ride you ordered, whether it was what you intended or not.

So, for now, and for the near future, your best bet is to use the applications that give you graphical user interfaces for tasks when you cannot risk making an erroneous command line entry. And gradually, over time, learn to appreciate the things you can do in the shell. Once you get some mastery of the shell, you'll discover that most things in Linux are much easier than they are in Windows. The real power of Linux is in the shell.

Best of luck to you.

Crusty

---

### Post by Petro Dawg on 2013-08-30
> **jim_collins2 said:**
> If I find my new recordings, can I just copy or move the old ones to that directory?  Will I be able to see them with my frontend and watch them normally?

Have you been able to locate your new recordings yet?

Try looking in the following file path [FONT=courier new]/var/lib/mythtv/recordings

[/FONT]I also found this link which may pertain to your situation... [http://www.mythpvr.com/mythtv/tips/migrate-recordings.html](http://www.mythpvr.com/mythtv/tips/migrate-recordings.html), step 2 seems to be where you are at the moment.

---

### Post by jim_collins2 on 2013-08-30
OK, moved the recordings (I moved everything in sdb1/mythtv/recordings to sda2/var/lib/mythtv/recordings.  I tried the link above and in step 1 after asking for password I got the following message after I entered my password: mysqldump: Got error: 1045: Access denied for user 'mythtv'@'localhose' (using password: YES) when trying to connect.
Tried to jump to step 3 as I have already copied the recordings and when I typed in : mysql -u mythtv -p mythconverg < recordings.sql I was asked for my password again and got the same error message as I just typed.

---

### Post by steeldriver on 2013-08-30
You should be able to find the default password to access the mythconverg database by looking in the /etc/mythtv/mysql.txt file, e.g.

```

grep ^DB /etc/mythtv/mysql.txt

```

I haven't followed the link HOWEVER I'm not sure that a mysqldump is what you need at this point - don't you need a script that examines the /var/lib/mythtv/recordings directory for new files, prompts you to supply the relevant metadata (series, title, etc.) and then updates the DB?

---

### Post by jim_collins2 on 2013-08-30
yes, i believe the recordings are in the correct location, but are not recognized by the front end.  What script do I need then?

---

### Post by jim_collins2 on 2013-08-31
does anyone know what script I may need to change or add?

---

### Post by jim_collins2 on 2013-09-04
Well I never got the recordings to be recognized by the frontend.  What I ended up doing was installing K3B and navigating to the directory and watching them with K3B.  It is certainly a pain in the rear, but the picture quality is good.  Doesn't have all the bells and whistles that Myth has and commercials are difficult, but I can watch them and delete them freeing up space.  I looked at quite a few threads and it seems that there are preliminary steps that need to be taken BEFORE moving the files.  I can sort the files by date and I know when the new ones start so I will be able to watch/delete the old ones.  Thanks to everyone who tried to help me.  In doing this I did find a bunch of cool software that can be installed.  Is there a thread that shows some cool things to do with Myth other than typical recording viewing??

---

### Post by jim_collins2 on 2013-09-04
Well I never got the recordings to be recognized by the frontend. What I ended up doing was installing K3B and navigating to the directory and watching them with K3B. It is certainly a pain in the rear, but the picture quality is good. Doesn't have all the bells and whistles that Myth has and commercials are difficult, but I can watch them and delete them freeing up space. I looked at quite a few threads and it seems that there are preliminary steps that need to be taken BEFORE moving the files. I can sort the files by date and I know when the new ones start so I will be able to watch/delete the old ones. Thanks to everyone who tried to help me. In doing this I did find a bunch of cool software that can be installed. Is there a thread that shows some cool things to do with Myth other than typical recording viewing??

---

### Post by steeldriver on 2013-09-04
Sorry I meant to get back to you before

The script I was referring to is called ***myth.rebuilddatabase.pl*** however it is apparently deprecated --> [http://www.mythtv.org/wiki/Myth.rebuilddatabase.pl](http://www.mythtv.org/wiki/Myth.rebuilddatabase.pl)

According to the link in that page, the 'new' way of doing things is via a Video **storage group** --> [http://www.mythtv.org/wiki/MythVideo](http://www.mythtv.org/wiki/MythVideo)

I have not tried it, so I can't really advise further

---

### Post by jim_collins2 on 2013-09-04
Thanks for the info.  Hopefully I won't have to go through it as I have a workaround.  Well actually now MY WIFE has the workaround.  I taught her how to do it this morning and she was happy.  Not sure I want to chance messing that up!  Thanks again - although it was quite frustrating I am learning and there are so many helpful people on here.

---

### Post by Bucky Ball on 2013-09-04
***Threads merged.***

A heads up. Please refrain from posting duplicate threads in future. It is against forum guidelines. Thanks.

---

