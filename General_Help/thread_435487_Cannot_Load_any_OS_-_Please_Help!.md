---
title: "Cannot Load any OS - Please Help!"
date: 2007-05-06
forum: General Help
---

### Post by haargerman on 2007-05-06
I'm in desperate need of some guidance.

So I accidently aborted my installation of Ubuntu, and now I can't load Windows XP.It only gives me an ATA Error or will go into the Ubuntu CD startup where I can install Ubuntu.

I have a feeling my partitions are messed up - but I KNOW my data is still there. Can anyone help me out here? I don't really care about installing linux right now - I just want to get into Windows.

Thanks,
Aaron

---

### Post by kaede on 2007-05-07
try to restore your MBR . using your bootable windows cd. enter repair console. and type fixmbr. :D

---

### Post by haargerman on 2007-05-07
How do I enter repair console?

Sorry, I'm a complete linux noob. "Resuce a broken system"..is this what I want?

EDIT: I typed that into the console and it brought me to the install again...

---

### Post by confused57 on 2007-05-07
Here's several methods to restore your Window's IPL code to the mbr:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

For Window's XP recovery console method, you need an XP install cd(not a recovery cd)...the other methods are downloading a Win98SE oem boot disk...or the Super Grub Disk.

You could always try to reinstall Ubuntu again.

---

### Post by haargerman on 2007-05-07
Thanks,

I've been trying to install linux, but I keep getting snagged on my partitions - nothing I do is working. Right now this is what I have:

#1 primary 49.3MB K Fat16 /media/sda1 --- Dont know what this is.
#2 primary 70.0GB K ntfs /media/sda2 ---- This is where Windows is installed - I don't want to touch this partition.
#3 primary 10.0GB K ntfs /media/sda3 -- I formatted a partition to get this..
unusable 13.3GB unusable -- What is going on here? I can't do anything with this, I would like to use this for Ubuntu.
#4 primary 5.1GB K fat32 /media/sda3

..If I try to delete #3 Primary, and save changes (So I can create 23GB of free space for Ubuntu) - it tells me I have no root defined.
..If I try to use the guide to use the most continuous free space - it tells me I have too many primary drives.

ugh. this is annoying.

---

### Post by confused57 on 2007-05-07
> **haargerman said:**
> Thanks,

I've been trying to install linux, but I keep getting snagged on my partitions - nothing I do is working. Right now this is what I have:

#1 primary 49.3MB K Fat16 /media/sda1 --- Dont know what this is.
#2 primary 70.0GB K ntfs /media/sda2 ---- This is where Windows is installed - I don't want to touch this partition.
#3 primary 10.0GB K ntfs /media/sda3 -- I formatted a partition to get this..
unusable 13.3GB unusable -- What is going on here? I can't do anything with this, I would like to use this for Ubuntu.
#4 primary 5.1GB K fat32 /media/sda3

..If I try to delete #3 Primary, and save changes (So I can create 23GB of free space for Ubuntu) - it tells me I have no root defined.
..If I try to use the guide to use the most continuous free space - it tells me I have too many primary drives.

ugh. this is annoying.
You can only have 4 primary partitions, so you can't create another partition...but you should be able to install over the primary #3 partition.  I believe in your other thread that you were using the alternate cd...what you can try is to select to install on your primary #3 partition.  Format ext3, set mountpoint as root (/), make it a logical partition, set the bootflag on, when you resize maybe it'll let you add your unusuable space?  If it doesn't, for now you could resize the partition to something like 9.5 Gb...then in the remaining space you could set up a swap partition, set as a logical partition,  format as swap, mountpoint as swap.
You might then be able to select your other unallocated space as /home,  select to format as ext3, set the mountpoint as /home, select as a logical partition.
Here's an excellent guide to installing with the alternate cd:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)
there's some excellent screenshots...see the section installing on NTFS with Feisty Fawn.

Added:  You'll need to select "Manual Partitioning" in order to install using the above method.

---

### Post by haargerman on 2007-05-07
So I deleted #3 primary and made this:

logical  10GB  B  ext3 /(root)
logical  1GB     ext3 /swap
logical 12.3GB  ext /home

Will this work? What about my Windows partition, does the bootflag need to be on if I want to Dual-Boot?

---

### Post by confused57 on 2007-05-07
> **haargerman said:**
> So I deleted #3 primary and made this:

logical  10GB  B  ext3 /(root)
logical  1GB     ext3 /swap
logical 12.3GB  ext /home

Will this work? What about my Windows partition, does the bootflag need to be on if I want to Dual-Boot?

This should work...I don't think you need to manually set the bootflag "on" for your Window's partition, I believe if you do, it will turn it "off" on your Ubuntu root partition...I could be wrong.  Set your root partition bootflag to "on" and I think you'll be OK.  At least you should be able to get your system bootable.

Added:  In other words, you shouldn't have to do anything to your Window's bootflag option.

---

### Post by haargerman on 2007-05-07
Okay..

Unfortunately now I am getting a message that says:

"File system does not have expected sizes for Windows to like it. 
"Cluster size is 2k (1k expected): number of clusters is 24026 (47959 expected): size of FATs is 94 sectors (188 expected)"

I'm given an option to Ignore or Go Back...

Will this effect me greatly?

---

### Post by confused57 on 2007-05-07
> **haargerman said:**
> Okay..

Unfortunately now I am getting a message that says:

"File system does not have expected sizes for Windows to like it. 
"Cluster size is 2k (1k expected): number of clusters is 24026 (47959 expected): size of FATs is 94 sectors (188 expected)"

I'm given an option to Ignore or Go Back...

Will this effect me greatly?

I'm sorry, but I don't know what to advise you to do, I'm not familiar with this error.  You could wait until someone else who might know...I can't tell you one way or the other.

---

### Post by haargerman on 2007-05-07
I ran a search and didn't find anything which would scare me from pressing "ignore".

I'm currently installing Ubuntu 7 - let's cross our fingers. :-p

EDIT - I have the WORST luck in the world.

Halfway through the installation I get a: "No installable kernal was found in the defined APT sources".....now what? Bad ISO?

---

### Post by confused57 on 2007-05-07
> **haargerman said:**
> I ran a search and didn't find anything which would scare me from pressing "ignore".

I'm currently installing Ubuntu 7 - let's cross our fingers. :-p
Good luck...my fingers are crossed.  Sure hope everything works OK.

---

### Post by haargerman on 2007-05-07
I think I might just throw it out the window. That'll solve everything.

The install failed, and I still can't get into Windows.  :confused:

---

### Post by confused57 on 2007-05-07
> **haargerman said:**
> I ran a search and didn't find anything which would scare me from pressing "ignore".

I'm currently installing Ubuntu 7 - let's cross our fingers. :-p

EDIT - I have the WORST luck in the world.

Halfway through the installation I get a: "No installable kernal was found in the defined APT sources".....now what? Bad ISO?

That could possibly be the problem...did you run an md5sum check on your iso, after you downloaded it?  See this guide:
[http://www.psychocats.net/ubuntu/iso#checksum](http://www.psychocats.net/ubuntu/iso#checksum)

and burn it at a low speed...8x or less?

Sorry it didn't work...you might still consider restoring your Window's IPL code to the mbr to see if you can boot Windows.  If you have access to another computer, the Super Grub Disk can restore it(see my other reply for alternate methods).
It's getting late here, so I won't be able to help any more tonight...good luck with finding a solution.  I'll check back in tomorrow(or later today).

Added:  Before I retire for the night, which version of the alternate cd did you download?...the 32-bit(i386) should work OK on your system.

---

### Post by haargerman on 2007-05-07
It was the 32bit.

EDIT - Is it possible to to boot Super Grub Disk from USB Flash Drive? The website says it is, but I'm confused on how I could do this?

---

### Post by confused57 on 2007-05-07
> **haargerman said:**
> It was the 32bit.

EDIT - Is it possible to to boot Super Grub Disk from USB Flash Drive? The website says it is, but I'm confused on how I could do this?
About the only thing I could suggest is to get access to another computer and burn a copy of the Super Grub Disk...I didn't really understand either, how to install SGD to a USB disk without an OS.

Do you have anybody you could borrow a Windows XP installation disk from?  If you do, you could boot it, press "r", then run the command FIXMBR(see the link I gave you previously).  If you have a floppy drive, there are instructions in the link for burn a Win98SE oem boot floppy.

Sorry, but other than that, I don't really know what else to suggest.

---

### Post by haargerman on 2007-05-07
Yeah, I've asked around and can't find a Windows Installation disk - only a reinstallation and that won't work.

I might either download Super Grub Disk or i've also downloaded another copy of the iso and re-burn it and try to install ubuntu again.

Thanks for your help - I will keep you updated.

EDIT: Is it possible to burn the iso to a DVD and it will still work? The reason I ask is because I just realized I've run out of CD-R's but I have plenty of DVD's laying around.

---

### Post by confused57 on 2007-05-07
> **haargerman said:**
> Yeah, I've asked around and can't find a Windows Installation disk - only a reinstallation and that won't work.

I might either download Super Grub Disk or i've also downloaded another copy of the iso and re-burn it and try to install ubuntu again.

Thanks for your help - I will keep you updated.

EDIT: Is it possible to burn the iso to a DVD and it will still work? The reason I ask is because I just realized I've run out of CD-R's but I have plenty of DVD's laying around.
A DVD "should" work, but be sure to check the md5sum after you download the iso.

Do you have a floppy drive on your pc?  If you do, you could make a Win98SE oem boot floppy which could restore your Window's IPL code to the mbr:
[http://www.users.bigpond.net.au/hermanzone/p18.htm#Windows_98_Floppy_Disk_Method](http://www.users.bigpond.net.au/hermanzone/p18.htm#Windows_98_Floppy_Disk_Method)

Again, good luck...wish I could help you more.

---

### Post by haargerman on 2007-05-07
I don't have a floppy on the laptop, unfortunately.

---

### Post by haargerman on 2007-05-08
Just thought I would let you know that I was able to succesfully install Ubuntu, update my video card drivers and now I am enjoy my dual-booting laptop :)

(I still havent tried to load Windows yet, but I'm sure it's fine.)

Thank you so much for all of your help!

---

### Post by confused57 on 2007-05-08
Thanks for the update...I'm certainly glad you were able to get Ubuntu installed.  I know you'll enjoy using Linux, it's been fun & educational for me.  I suppose your original install may have been a bad iso or bad burn?
Anyhow, glad it's working now.

---

