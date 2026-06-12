---
title: "constant errors file system"
date: 2013-05-18
forum: General Help
---

### Post by mrajdl on 2013-05-18
I don't know why, I don't use the cpu that much, but every day I have to reboot to recovery mode, go to root shell and run fsck.  It fixes a bunch of errors, then every thing is fine for a day or 10 minutes.  I'm a idiot when it's linux don't know what to do?

Mike

---

### Post by mrajdl on 2013-05-19
Had to do so the same this morning to get it running.  It acts like the power is being cut off, but its not cause I always shutdown.  When I get it running and launch Chromium it says didn't close properly, and gives an option to open tabs???  That's a bunch of bull I always exit my browser and shutdown or suspend the system.  

Ubuntu 13.04, however it started with 12.10.  In 12.10 symptoms were the same, but errors were a little different it would tell me the drive for /tmp was not ready or not present.

---

### Post by mcduck on 2013-05-19
Check the SMART status of the hard drive with the Disks tool, the errors could be caused by the drive being close to failing.

...also knowing the exact error you are getting would be helpful.

---

### Post by mrajdl on 2013-05-19
> **mcduck said:**
> Check the SMART status of the hard drive with the Disks tool, the errors could be caused by the drive being close to failing.

...also knowing the exact error you are getting would be helpful.

My first thought was the hard drive failing, but I never get any errors to hardware failure. Not sure how to check SMART status of hd with Disks tool, does that need to be installed?

Tried to get the errors when at root, with "fsck > errors.txt" , but says root is read only.


Been married to a red head for 13 years!  Don't mess with the red or the root!!!

---

### Post by mcduck on 2013-05-19
Disks is installed by default, just search for it in the Dash.

Once opened, select your hard drive, and then in the upper right corner you'll find a small button (with a gear icon), click that and select "SMART Data and Tests".

---

### Post by mrajdl on 2013-05-19
> **mcduck said:**
> Disks is installed by default, just search for it in the Dash.

Once opened, select your hard drive, and then in the upper right corner you'll find a small button (with a gear icon), click that and select "SMART Data and Tests".

Ok did that, I could click every option but the SMART Data and tests.

I'm to starting think I should just to low level format the hard drive, and start fresh.

---

### Post by redmk2 on 2013-05-19
> **mrajdl said:**
> 
I'm to starting think I should just to low level format the hard drive, and start fresh.
You don't really mean this do you?  You can't align the heads correctly.  Modern HDD's don't need low level formatting.

---

### Post by mcduck on 2013-05-19
How old is the drive & system? It's quite uncommon for any even recently modern hard drive to not support SMART.

Also, most hard drive manufacturers provide a bootable SMART test tool specific for their drives, so if you can find out the manufacturer of the drive, that might be worth a try.

---

### Post by mrajdl on 2013-05-19
> **redmk2 said:**
> You don't really mean this do you?  You can't align the heads correctly.  Modern HDD's don't need low level formatting.

OK, now what?

---

### Post by redmk2 on 2013-05-19
> **mrajdl said:**
> OK, now what?

What are the errors?  From memory what fsck messages are you geting?  What does it cure?

What state is the drive in when you have the OS failure?  Usually when the drive gets to a state where it has failed it is mounted read only (ro).  Could this be what is happening?

Is this the only disk (HDD) in the system?  When it fails, what do you get with this CLI command:```
mount 
```

How old is the disk?  How old is the hardware?

---

### Post by mrajdl on 2013-05-20
> **mcduck said:**
> Disks is installed by default, just search for it in the Dash.

Once opened, select your hard drive, and then in the upper right corner you'll find a small button (with a gear icon), click that and select "SMART Data and Tests".

Ok figured out the SMART stuff it was not enabled in the BIOS.

SMART Data and Tests tells me that there are 763 sectors failing.  763 in a 2 gig drive is not that many.  the hdd is close to 4 yrs old.

Are there utils I could run to map out those sectors, or should I just start shopping for a new hdd, oh is it backed up, of course not, and I'm out of blank CD's stupid idiot.

---

### Post by mrajdl on 2013-05-20
> **redmk2 said:**
> What are the errors?  From memory what fsck messages are you geting?  What does it cure?

What state is the drive in when you have the OS failure?  Usually when the drive gets to a state where it has failed it is mounted read only (ro).  Could this be what is happening?

Is this the only disk (HDD) in the system?  When it fails, what do you get with this CLI command:```
mount 
```

How old is the disk?  How old is the hardware?

I think I'm getting somewhere, I think the hdd is dying, it's 3yrs 9months 18 days old.  I'm just hoping for couple of days of use before it takes a total crap

---

### Post by redmk2 on 2013-05-20
> **mrajdl said:**
> Ok figured out the SMART stuff it was not enabled in the BIOS.

SMART Data and Tests tells me that there are 763 sectors failing.  763 in a ***2 gig drive*** is not that many.  the hdd is close to 4 yrs old.

Are there utils I could run to map out those sectors, or should I just start shopping for a new hdd, oh is it backed up, of course not, and I'm out of blank CD's stupid idiot.

Really; a 2 gig drive?  Are you sure that the drive is that small?  If so, I'd get a USB  flash drive of 4GB or 8GB ( it's cheaper than CD's or DVD's) and backup the data to that.  Then buy a new drive, reinstall Ubuntu and move the data back to the new drive.  I wouldn't take the time to try and save the old drive.

---

### Post by binaryhermit on 2013-05-20
Have they even made 2 GB hard drives in the last 4 years?  Heck, the company my mom used to work for was deploying computers with 4 GB hard drives in 1998.

---

### Post by mcduck on 2013-05-20
4 years is not that old, but it doesn't really matter, bad sectors are pretty much a sign that the drive is reaching it's end of life. So better make sure you have up-to-date backups of everything important. And yes, you will probably have to replace the drive soon. (Actually if you can afford it, replacing it right now would more than likely fix your problem with filesystem corruption.)

Any modern drive will automatically map out bad sectors, so there's nothing you can do about it. And anyway the fact that they start to appear is a sign that the disc surface is deteriorating.

(And I agree wit others that 2GiB sound way too small for a drive that's not at least 15 years old :D)

---

### Post by mrajdl on 2013-05-20
> **mcduck said:**
> 4 years is not that old, but it doesn't really matter, bad sectors are pretty much a sign that the drive is reaching it's end of life. So better make sure you have up-to-date backups of everything important. And yes, you will probably have to replace the drive soon. (Actually if you can afford it, replacing it right now would more than likely fix your problem with filesystem corruption.)

Any modern drive will automatically map out bad sectors, so there's nothing you can do about it. And anyway the fact that they start to appear is a sign that the disc surface is deteriorating.

(And I agree wit others that 2GiB sound way too small for a drive that's not at least 15 years old :D)

Agreed, but that doesn't mean I can't have fun with it. this hdd going to get formatted, llformated, then formatted again, if that doesn't help it gets the plasma cutter!.

---

### Post by efflandt on 2013-05-20
Usually the symptoms of a bad drive are that you (even with sudo) do not have permission to write anything to the hard drive because, as redmk2 says, it automatically remounts read-only. One problem with that is that there is no permanent log that anything went wrong (and could be why apps think they have not shut down properly).  The only way to check for such errors is to look at dmesg when something strange happens "before" shutting the computer down.

My Linux partition is at the far end of a 1 TB drive, which seems to have started going bad months ago when I started having write permission (read-only) issues. Although, e2fsck with the switch to mark out badblocks from Ubuntu on another drive (SSD) helped for a few months, eventually it started getting more errors. So I used Acronis to image Win7 partitions (which had not gone bad yet) and recreated them on a new drive.  And I reinstalled Ubuntu 12.04.2 and copied my old home partition to that.

A hard drive reserves some space to transparently replace (remap) good sectors in place of bad sectors.  But once all the error sites are used up, it is never going to get any better, just worse.  And it should not be trusted for anything essential.

---

### Post by mrajdl on 2013-05-20
> **efflandt said:**
> Usually the symptoms of a bad drive are that you (even with sudo) do not have permission to write anything to the hard drive because, as redmk2 says, it automatically remounts read-only. One problem with that is that there is no permanent log that anything went wrong (and could be why apps think they have not shut down properly).  The only way to check for such errors is to look at dmesg when something strange happens "before" shutting the computer down.

My Linux partition is at the far end of a 1 TB drive, which seems to have started going bad months ago when I started having write permission (read-only) issues. Although, e2fsck with the switch to mark out badblocks from Ubuntu on another drive (SSD) helped for a few months, eventually it started getting more errors. So I used Acronis to image Win7 partitions (which had not gone bad yet) and recreated them on a new drive.  And I reinstalled Ubuntu 12.04.2 and copied my old home partition to that.

A hard drive reserves some space to transparently replace (remap) good sectors in place of bad sectors.  But once all the error sites are used up, it is never going to get any better, just worse.  And it should not be trusted for anything essential.

Ok my hard drive has is going south, thanks for who helped redmk2d, efflandt, and mcduck

---

### Post by 3rdalbum on 2013-05-20
Back up your data NOW.

The next fsck might completely ruin the filesystem and make your files irretrievable.

---

### Post by mrajdl on 2013-05-21
Oops the drive is 200g not 2, anyway I have a new 320g on the way that's all I need.

but what is this:
mike@ubuntu:~$ uptime
 19:34:07 up 10:00,  2 users,  load average: 0.07, 0.03, 0.06

I'm the only user????

I do have a ghost in the house, John and he does sit at the computer, cause one night my dog wound not stop barking at the chair until the cpu was turned off.  crazy

---

### Post by binaryhermit on 2013-05-21
> **mrajdl said:**
> Oops the drive is 200g not 2, anyway I have a new 320g on the way that's all I need.

but what is this:
mike@ubuntu:~$ uptime
 19:34:07 up 10:00,  2 users,  load average: 0.07, 0.03, 0.06

I'm the only user????
There's probably multiple instances of you logged in (i.e. you in X and you in the terminal you typed "uptime" into).

---

### Post by redmk2 on 2013-05-21
> **binaryhermit said:**
> There's probably multiple instances of you logged in (i.e. you in X and you in the terminal you typed "uptime" into).
Exactly.  There is the login user and the terminal user.  You can see that using the command *who*```
$who

red    tty7         2013-05-21 18:53
red    pts/0        2013-05-21 19:00 (:0.0)

```

---

### Post by mrajdl on 2013-05-21
> **redmk2 said:**
> Exactly.  There is the login user and the terminal user.  You can see that using the command *who*```
$who

red    tty7         2013-05-21 18:53
red    pts/0        2013-05-21 19:00 (:0.0)

```

Thanks again in terminal who:

mike@ubuntu:~$ who
mike     tty7         2013-05-21 20:36 (:0)
mike     pts/1        2013-05-21 21:12 (:0)

I guess I have to visit this forum more often, I might learn something, been using ubuntu since v6.04, great OS, beets the heck of that Windows DOS crap I grew up on. Only problem I just don't know enough, but I'm learning.

---

### Post by mrajdl on 2013-05-25
My replacement hd will be here today, I downloaded the .iso 64 bit version of Ubuntu 13.04, I'm currently 32 bit.

If I use the 64 bit version to prep the new hd, will I be able to copy my home folder from the 32 to the 64 without causing problems?

---

### Post by redmk2 on 2013-05-25
> **mrajdl said:**
> My replacement hd will be here today, I downloaded the .iso 64 bit version of Ubuntu 13.04, I'm currently 32 bit.

If I use the 64 bit version to prep the new hd, will I be able to copy my home folder from the 32 to the 64 without causing problems?

The files are not particular to either 64 or 32 bit.  Where are the files stored?

More important is whether your CPU understands 64bit instructions.  Are you going to put ***/home*** on its own partition on the new disk?

---

### Post by mrajdl on 2013-05-25
> **redmk2 said:**
> The files are not particular to either 64 or 32 bit.  Where are the files stored?

More important is whether your CPU understands 64bit instructions.  Are you going to put ***/home*** on its own partition on the new disk?

Yes the CPU nows 64 bit was using it, but went back to 32 when I started having problems don't know why.  I thing you answered my ?.

My plan is to burn a cd with the 64 bit .iso.
reconfigure the failing HD to the 2nd
Install the new HD.
Use the CD to install 13.04 64 bit, and letting it use the whole drive.
Then copy the /home files from the old HD to the new drive.

Is this possible?

Of course it all depends on the failing HD, the CDs won't be here til Monday, got my fingers crossed.

---

### Post by redmk2 on 2013-05-25
> **mrajdl said:**
> Yes the CPU nows 64 bit was using it, but went back to 32 when I started having problems don't know why.  I thing you answered my ?.

My plan is to burn a cd with the 64 bit .iso.
reconfigure the failing HD to the 2nd
Install the new HD.
Use the CD to install 13.04 64 bit, and letting it use the whole drive.
Then copy the /home files from the old HD to the new drive.

Is this possible?

Of course it all depends on the failing HD, the CDs won't be here til Monday, got my fingers crossed.

Yes that will work.

---

### Post by mrajdl on 2013-05-25
> **redmk2 said:**
> Yes that will work.

Thanks

---

### Post by mrajdl on 2013-05-26
Ok new plan, I forgot about Monday being a holiday so no CDs until Tuesday.  I have a 4 gig HD  of the 40 pin connector type, set it up as a slave and hook it up to the CD-ROM cable.  The BIOS identifies it correctly, but it gets mounted read only.  All I want to do is wipe it clean and use it for backup.  Can this be done at the root shell?

---

### Post by mrajdl on 2013-05-28
I thought I would be done with this problem today, but the .iso is to big for the the CD-R, so I ordered 1 DVD-R, I only ordered 1 cause I never done dvds with this drive.  I feel so stupid I worked for the creators of CD technology, Philips the first CD-Rs on the market were $40 a CD.  I just bought a 100 for $20.

---

### Post by redmk2 on 2013-05-29
> **mrajdl said:**
> Ok new plan, I forgot about Monday being a holiday so no CDs until Tuesday.  I have a 4 gig HD  of the 40 pin connector type, set it up as a slave and hook it up to the CD-ROM cable.  The BIOS identifies it correctly, but it gets mounted read only.  All I want to do is wipe it clean and use it for backup.  Can this be done at the root shell?

Does this machine have a USB port?  I would by a 8GB or better yet a 16GB flash drive to backup the data.  A 16GB flash stick is under $20.

---

### Post by redmk2 on 2013-05-29
> **mrajdl said:**
> I thought I would be done with this problem today, but the .iso is to big for the the CD-R, so I ordered 1 DVD-R, I only ordered 1 cause I never done dvds with this drive.  I feel so stupid I worked for the creators of CD technology, Philips the first CD-Rs on the market were $40 a CD.  I just bought a 100 for $20.

You can use a flash drive to install the OS as well if you want to.  The technology has changed a lot.  The first hard drive I owned was a "hard card" 20MB device.  I believe it was $200.  Things have changed a lot.  :D

---

### Post by mrajdl on 2013-05-29
> **redmk2 said:**
> Does this machine have a USB port?  I would by a 8GB or better yet a 16GB flash drive to backup the data.  A 16GB flash stick is under $20.

Yes it has a USB ports, never used flash drives, don't even know what they look like, sucks getting old

---

### Post by redmk2 on 2013-05-29
> **mrajdl said:**
> Yes it has a USB ports, never used flash drives, don't even know what they look like, sucks getting old

I know what you mean.  I'm retired myself.  I just have to keep up with the latest trends.  Flash drives have been around since 2000.  It looks like we may see 1TB drives this year.  See [[COLOR="#FF8C00"]**here**[/COLOR]]("http://en.wikipedia.org/wiki/USB_flash_drive") for some background and pictures.

---

### Post by mrajdl on 2013-05-29
> **redmk2 said:**
> I know what you mean.  I'm retired myself.  I just have to keep up with the latest trends.  Flash drives have been around since 2000.  It looks like we may see 1TB drives this year.  See [[COLOR="#FF8C00"]**here**[/COLOR]]("http://en.wikipedia.org/wiki/USB_flash_drive") for some background and pictures.

Also have a flash drive on order, just went with a 2 gig for $3.99.  I remember reading an article way back on Windows NT, the author wrote "NT has support for a ridiculously large hard drive 4 gig", of course in those days a 1 gig was about a $1,000 bucks, crap have things changed....

---

### Post by mrajdl on 2013-06-03
Ok got my flash drive today, it's recognized, but why is not empty???? Not sure what to do, can I erase what's on it? Then create a startup disk?  Never used one before, amazed how small it is!!!!

Mike

---

### Post by redmk2 on 2013-06-03
> **mrajdl said:**
> Ok got my flash drive today, it's recognized, but why is not empty???? Not sure what to do, can I erase what's on it? Then create a startup disk?  Never used one before, amazed how small it is!!!!

Mike
I can't say for sure, but some of the flash drive manufactures provide value added software.  Usually it's for Windows users.  FYI:  The drive is most likely formated FAT32 (vFAT).  Most OS's recognize this file system.

There are 2 ways to make Ubuntu bootable flash drives.  One is most likely already on your Ubuntu system  It is called "Startup Disk Creator".  The other one is "Unetbootin".  It is available in the repos.

---

### Post by mrajdl on 2013-06-04
> **redmk2 said:**
> I can't say for sure, but some of the flash drive manufactures provide value added software.  Usually it's for Windows users.  FYI:  The drive is most likely formated FAT32 (vFAT).  Most OS's recognize this file system.

There are 2 ways to make Ubuntu bootable flash drives.  One is most likely already on your Ubuntu system  It is called "Startup Disk Creator".  The other one is "Unetbootin".  It is available in the repos.

Thanks, the flash drive worked great, new hd installed all looks good.

---

