---
title: "hdd size vs partition size"
date: 2020-10-09
forum: General Help
---

### Post by sukelis on 2020-10-09
My initial search didn't produce relevant results and I apologize for posting instead of searching more extensively.  I was in the midst of trying to switch from XP to Lubuntu a few years ago when I developed health issues.  I've come out of it with less cognitive ability than I had.  I find learning new things much harder than it used to be and sorting through search results is also difficult.  However, since my XP system is truly ancient at this point, and I don't really want to spend the rest of my life on Android, I am trying again to switch to Lubuntu.

But what I'm really stuck on is almost a philosophical question... when adding 2TB and 3TB hdds to ubuntu, do you partition them in to smaller chunks?  or just add the whole thing?  

Under XP I would always partition my hdds into smaller chunks since defragging a whole 2TB is a PIA.  But one of the advantages to this extended delay in switching is that much of my XP system's software, besides the OS, has aged into obsolescence.  So I am no longer looking at trying to preserve the 3TB of active XP files as is.  Instead, I'm just working with what I truly depend on.  

Which opens up possibilities as far as ubuntu goes.  I've got the root installed on an SSD and a blank 2TB just sitting there.  Do I just mount the whole thing under /home?  Or split it and mount some under /home and some under ... ?  Are there issues regarding number of files per partition/mount point?  What else will bite me?

Again, I apologize for just jumping in and asking but I've been stuck on this point and I'm hoping to get some help and/or suggestions.

Thanks,

sukelis

---

### Post by oldfred on 2020-10-09
It is your choice.

I did not think XP worked with 3TiB drives as you have to use gpt partitioning with drives over 2TIB.
Or did you use MBR(msdos) and in effect convert 3TB drive to 2TB?
MBR was designed in 1980's when GB was huge so they set a hard limit of 2TB as max that MBR would support.

I also prefer some additional partitions. But I like to add multiple 25 or 30GB partitions for test installs of Ubuntu or other systems and have all data in a data partition. Since /home then is tiny as really just the mostly hidden . configuration files, I keep /home inside my / (root) partition. I also do not want experiments in test install to modify main working install's /home but do want mount data, I find a shared data partition to work where sharing /home would not.

While with Linux you do not need to do a defrag, sometimes if system is abnormally shutdown (power failure) you may need to do a fsck. And worse case file recovery, if you were not backing up like you should. Then large partition(s) are a disadvantage.
Some like LVM - logical volumes as you can change sizes with mounted volumes, and do some advanced things, but again a bit more advanced.

---

### Post by TheFu on 2020-10-09
> **sukelis said:**
>  
But what I'm really stuck on is almost a philosophical question... when adding 2TB and 3TB hdds to ubuntu, do you partition them in to smaller chunks?  or just add the whole thing?  
 

This sort of question is a "why" question.  I love these because there are trade-offs and we each have different "why" answers. There is no wrong answer, except you must use GPT partitioning.  After that, it is just trade-offs.

When I'm partitioning, I consider a few other things:
[LIST]
[*]For what will the storage to be used?
[*]How will I back up that data?
[*]Do my backup storage partitions have any size limits?
[*]Do not feel like you must allocate all the storage today. It can wait. Increasing storage is 100x easier than reducing it.
[/LIST]

In my world, my backup storage is never larger than 4TB, so no partition is allowed to be over 4TB in size.  That is a hard limitation for me.  If I don't have a place to store the backups, then I won't bring the primary storage on-line either.  Backups are NOT optional for me.

I keep media (videos, music, photos) outside of HOME. The reason for this is those things tend not to change, so the way I back them up is different from the way I backup /home/ or the OS files.  

Files that change multiple times a year get versioned backups. Files that never change, get a mirror (rsync) backup.  Smaller backups means they are faster and it means that backup storage doesn't run out because I added and deleted recorded TV shows every week as the older versioned are kept until finally 90 days later. But then I have 90 days of newer TV recordings which have to work their way through the versioned backups.  Much easier to just keep media outside HOME and use rsync for backups of that data separately.

For /home/ how large could that possibly need?  History tells me that 25G is about all I will ever use for HOME.  I've created some larger HOME partitions and never used that storage.

[https://ubuntuforums.org/showthread.php?t=2425709&p=13883277#post13883277](https://ubuntuforums.org/showthread.php?t=2425709&p=13883277#post13883277) has a concrete example. Instead of using "partitions", I use 1 large partition and the "Logical Volume Manager" - for now, you can think of a partition as an "LV" - logical volume.  That's close enough for today.

---

### Post by sukelis on 2020-10-09
No, under XP I have many partitions, none larger than 750gb.  And data has always been separated from the XP system disk, as well as a few other directories I didn't like stuck where Windows wanted to put them. 

You make some good points.  Thank you!

---

### Post by sukelis on 2020-10-09
> **TheFu said:**
> This sort of question is a "why" question.  I love these because there are trade-offs and we each have different "why" answers. There is no wrong answer, except you must use GPT partitioning.  After that, it is just trade-offs.

When I'm partitioning, I consider a few other things:
[LIST]
[*]For what will the storage to be used? 
[*]How will I back up that data? 
[*]Do my backup storage partitions have any size limits? 
[*]Do not feel like you must allocate all the storage today. It can wait. Increasing storage is 100x easier than reducing it. 
[/LIST]

In my world, my backup storage is never larger than 4TB, so no partition is allowed to be over 4TB in size.  That is a hard limitation for me.  If I don't have a place to store the backups, then I won't bring the primary storage on-line either.  Backups are NOT optional for me.

I keep media (videos, music, photos) outside of HOME. The reason for this is those things tend not to change, so the way I back them up is different from the way I backup /home/ or the OS files.  

Files that change multiple times a year get versioned backups. Files that never change, get a mirror (rsync) backup.  Smaller backups means they are faster and it means that backup storage doesn't run out because I added and deleted recorded TV shows every week as the older versioned are kept until finally 90 days later. But then I have 90 days of newer TV recordings which have to work their way through the versioned backups.  Much easier to just keep media outside HOME and use rsync for backups of that data separately.

For /home/ how large could that possibly need?  History tells me that 25G is about all I will ever use for HOME.  I've created some larger HOME partitions and never used that storage.

[https://ubuntuforums.org/showthread.php?t=2425709&p=13883277#post13883277](https://ubuntuforums.org/showthread.php?t=2425709&p=13883277#post13883277) has a concrete example. Instead of using "partitions", I use 1 large partition and the "Logical Volume Manager" - for now, you can think of a partition as an "LV" - logical volume.  That's close enough for today.

You've made some excellent points.  Especially about not needing to put it all in to play at once.  A few years ago - well, actually, "last century"! - I used LVM on AIX.  Assuming LVMs are conceptually similar across *nix's, that may be a possibility.  

I guess my biggest take-away and challenge is remembering that Linux is much better at adapting to changing needs.  I don't need to worry so much about not knowing everything in advance.

Thank you very much!

---

### Post by TheFu on 2020-10-09
Since you are an AIX person, I'll jump a little deeper with volume management.  I did AIX admin for about 10 yrs and architectures for about 15 yrs before leaving enterprise work for Linux stuff.

LVM concepts are the same between Linux, Solaris, AIX, HP-UX, Irix, and others.  The only terminology difference is that PE = PV.  But ... as with LVM on other platforms, LVM has to be setup BEFORE any file systems are laid down.

Linux LVM sits between the HDD partitions and the file systems. For data-only disks, I'd create 1 partition of the entire disk, yes, create a partition, then make that partition the PV and that PV a new VG.  Then create LVs as needed out of that VG.  I don't cross physical disks with LVM anymore.  I did long ago and lost 80% of my data when 1 of the disks failed. That was before I had backup religion.

---

### Post by grahammechanical on 2020-10-09
There is one change that you need to be aware of (I assume it is the same for Lubuntu as for Ubuntu) with the latest versions we do not need a swap partition. Ubuntu uses a swap file. That will make partitioning a little easier.

It seems you are heading in the direction of having a / (root) partition; a /home partition; and a /Data partition. They do not need to be on the same drive. Do you want to breakdown your data into different categories? You can have the categories in their own partitions or in folders in the Data partition.

> Again, I apologize for just jumping in and asking but I've been stuck on  this point and I'm hoping to get some help and/or suggestions.

If people did not do that we would not have an opportunity to show off our expertise or lack of it :)  This forum is a user forum not a developer/programmer forum. You are not jumping in and there are no silly questions. Answers are a different matter. 

I wish you well. Regards

---

### Post by sukelis on 2020-10-10
I've started reading the documentation on lvm.  And the reference to having lvm on an ssd threw me... is this common?  advised?  While I still have an essentially virgin fresh install, would it be worthwhile to re-install and put lvm on my ssd (250gb)?  At present the ssd has a tiny EFI partition, two 54gb partitions for distros with only 1 installed, and 142gb unallocated.  

Questions:

Can you mix regular partitions and lvm on the same hard drive (in this case the ssd)?
Do you still need an EFI partition?  Is the EFI inside the lvm or external?

My first thought is to setup lvm on the 2gb hdd, make a backup of the installed root, and then wipe and setup the ssd with lvm and either re-install or restore from backup.  Doable?


Edit:

Posted that too fast.  Found this [https://ubuntuforums.org/showthread.php?t=2322512](https://ubuntuforums.org/showthread.php?t=2322512) and this [https://askubuntu.com/questions/847739/ubuntu-installation-on-ssd-steps](https://askubuntu.com/questions/847739/ubuntu-installation-on-ssd-steps) so more reading to do.

---

### Post by oldfred on 2020-10-10
UEFI only reads FAT32 so the ESP - efi system partition must be outside the LVM.

I do not use nor really know LVM.
But if I was going to install LVM, I would do a google search of TheFu and LVM.
Forum's search really on good on one term, so I use google or other search engine.
Just append site:ubuntuforums.org to your search term
Since he is posting here already, he then can respond to specific questions.

---

### Post by TheFu on 2020-10-10
> **sukelis said:**
> I've started reading the documentation on lvm.  And the reference to having lvm on an ssd threw me... is this common?  advised?  While I still have an essentially virgin fresh install, would it be worthwhile to re-install and put lvm on my ssd (250gb)?  At present the ssd has a tiny EFI partition, two 54gb partitions for distros with only 1 installed, and 142gb unallocated.  

Modern SSDs work just like HDDs for LVM.  You can put LVM on any partition you like.  If the OS runs from that SSD, you'll probably want to setup LVM during the installation process. Otherwise, one of the best things about LVM, snapshots, isn't available.
You can always put LVM on other disks before you add file systems. Unless you really know what you are doing, don't allow the same VG to cross physical disk boundaries. That can lead to data loss, unless the purpose is to use RAID1 that is controlled by LVM.

Questions:
> **sukelis said:**
> 
Can you mix regular partitions and lvm on the same hard drive (in this case the ssd)?
Do you still need an EFI partition?  Is the EFI inside the lvm or external?
Yes, you can, but why?
EFI has mandated standards to be cross platform. This means LVM cannot be used for the EFI partition and that it must be FAT32. The installer will set that up correctly.

> **sukelis said:**
> My first thought is to setup lvm on the 2gb hdd, make a backup of the installed root, and then wipe and setup the ssd with lvm and either re-install or restore from backup.  Doable?

Sure.  If your backups are file based (not disk/partition images), then this is a good time to test the restore process. Expect hiccups. There always are the 1st few restore attempts.  Beware that how Linux boots has many moving parts, so for anyone who isn't dealt with each over the years, it will be difficult.

> **sukelis said:**
> 
Edit:

Posted that too fast.  Found this [https://ubuntuforums.org/showthread.php?t=2322512](https://ubuntuforums.org/showthread.php?t=2322512) and this [https://askubuntu.com/questions/847739/ubuntu-installation-on-ssd-steps](https://askubuntu.com/questions/847739/ubuntu-installation-on-ssd-steps) so more reading to do.
Reading stuff is great, but no substitute for creating a play area and trying LVM stuff there.   I use virtual machines for this play area.  The size of the storage really doesn't matter.  A 100 MB LVM setup is just as good for learning as a 5TB storage area. With virtualization, you can keep 1 HDD or have 50 tiny HDDs to try stuff out.  

Test stuff first or be 100% certain you have everything you cannot lose backed up to storage and removed to a different room of the house. Somehow, people commonly wipe partitions during installs because they get in a hurry or get into a rhythm that leads them to answer partitioning/storage questions wrong.  Another good technique is to physically disconnect the storage you do not want to install onto during the installation process.  Later, you can reconnect it and add it to the system where you like. That's a good skill to have as well.

The granddaddy of all LVM documents: [https://tldp.org/HOWTO/LVM-HOWTO/](https://tldp.org/HOWTO/LVM-HOWTO/)
Don't worry how old it is. LVM is LVM across different distros and has been basically the same for all common needs over 15 yrs.  A guide created for Redhat is valid for Ubuntu or Debian too.

People always ask for a GUI tool to help manage LVM.  For a few years, there was one, but support for it died off.  LVM is used mainly by IT professionals and mainly for servers, which don't have GUIs.

All the old-school commands, like lvdisplay, vgdisplay, pvdisplay still exist, but are seldom used. Now we use lvs, vgs, pvs which produce tabular output in a easy to understand format. I can't remember the last time any of the *display commands was used - maybe 3 yrs ago?

My goal in life is to convince Oldfred to use LVM on all his systems. We each need to have a dream, right? ;)

---

### Post by Dennis N on 2020-10-10
You could create an new partition in your unallocated space and format it as an LVM physical volume with gparted. Then you are ready to try out LVM and not disturb your previous OS installation. That's how I began. I use LVM all the time now.

The first thing I followed to learn LVM for ordinary users was this:

[http://www.tutonics.com/2012/11/ubuntu-lvm-guide-part-1.html](http://www.tutonics.com/2012/11/ubuntu-lvm-guide-part-1.html)

The commands introduced there are still good but the GUI tool they mention doesn't exist anymore.

---

### Post by sukelis on 2020-10-11
> **oldfred said:**
> Forum's search really on good on one term, so I use google or other search engine.
Just append site:ubuntuforums.org to your search term

Brilliant!  I was pretty frustrated trying to search in the forums tool, but google does much better.  And I never knew about appending the site.  Great stuff!  Thanks!

---

### Post by sukelis on 2020-10-11
> **TheFu said:**
> Unless you really know what you are doing, don't allow the same VG to cross physical disk boundaries. That can lead to data loss, unless the purpose is to use RAID1 that is controlled by LVM.
Totally agree with the advice to not cross boundaries.  One isn't likely to have too many VGs on a PC even at 1 per physical disk.


> **TheFu said:**
> Reading stuff is great, but no substitute for creating a play area and trying LVM stuff there. I use virtual machines for this play area. The size of the storage really doesn't matter. A 100 MB LVM setup is just as good for learning as a 5TB storage area. With virtualization, you can keep 1 HDD or have 50 tiny HDDs to try stuff out.
Great idea.  I definitely need to start using virtualization.  I've always just kept an old system around... but it takes up space and isn't always convenient so a VM would be much better.  Tonight I made a list of the few files I need to preserve from this install, but the install is so new that it's a very short list.  So re-installing now will be super easy.


> **TheFu said:**
> People always ask for a GUI tool to help manage LVM. For a few years, there was one, but support for it died off. LVM is used mainly by IT professionals and mainly for servers, which don't have GUIs.I never like NOT having non-GUI access to the OS.  But I started out on mainframes in the 80's... everything was a terminal. My biggest complaint with iOS is that you can't do ****.  And the newer Windows seem to be heading that way.  

> **TheFu said:**
> My goal in life is to convince Oldfred to use LVM on all his systems. We each need to have a dream, right? You bet!

Thank you for all your help!

---

### Post by TheFu on 2020-10-11
> **sukelis said:**
> Brilliant!  I was pretty frustrated trying to search in the forums tool, but google does much better.  And I never knew about appending the site.  Great stuff!  Thanks!

_**Google-Fu is important.**_

Most search engines use a similar query language.  I only use a few advanced options but almost always find what I need quickly.
[LIST]
[*]**+term**  must include that term
[*]**-term** cannot include that term
[*]**-site:[www.xyz.com](www.xyz.com)**  cannot be from that site, the **+** can be used w/ site:, but it is redundant since site: 
[*] ....there's a way to limit the type of documents/files found - like pdfs or xls or help or images. I always have to look this up.  This is good for tools like Shodan (a specialized search engine).
[/LIST]
There are boolean operators, but those are seldom necessary.

For Ubuntu search, I would use "ubuntu +18.04 +{whatever}" for most things GUI related with 18.04 ubuntu.

---

### Post by oldfred on 2020-10-11
> My goal in life is to convince Oldfred to use LVM on all his systems. We each need to have a dream, right?

I am still working on converting some of my rsync backup to TheFu's suggestions (for years) of using rdiff-backup. I currently use rsync to multiple flash drives and sneakernet from old home in Illinois to condo in Florida. Does make for offsite backup every few months without using Internet which I prefer to avoid.

But as an old Engineer I believe in the Pareto Principle usually known as the 80/20 rule. And only need some 20% ? of my data encrypted. Most of my data (80%) is my music only from DVDs and photos. They do not need to be encrypted. 
I may then use LVM on one partition for encrypted data.

---

### Post by sukelis on 2020-10-13
Ok I am officially ready to give up on this.  I've spent way too much time trying to get lubuntu installed with LVM and I just can't get it to work.  This is a desktop not a laptop so I'm not even trying to use encryption, just lvm.  But the lubuntu installer doesn't offer it as an option and I just haven't been able to work around it.  I can get as far as getting a pv and vg setup and recognized by the installer, but then there is no option for creating lv's and the NEXT button is greyed out.  I can sit there and admire my nice disk layout, but that's pretty useless.  

I finally tried doing some searching specifically on lubuntu and it seems that the installer is known to have issues with LVM.  Examples [here]("https://unix.stackexchange.com/questions/502534/are-these-two-ways-of-installing-lubuntu-with-lvm-both-feasible-and-equivalent"), [here]("https://unix.stackexchange.com/questions/524009/lubuntu-19-04-calamares-installation-does-not-provide-full-disk-encryption") and [here]("https://ubuntuforums.org/showthread.php?t=2252907").  I suppose I should have done that searching earlier but I was just so sure the problem was that I didn't know what I was doing, so I just kept working at it.  What's that old saying... of all the things I've lost I miss my mind the most?  Sadly true for me.

So the new plan is to install lubuntu in a regular partition and then setup lvm on the rest of the SSD.  And then just learn to live with it that way.  I do have lvm setup on the HDD, so that's all set.

Thanks everyone for the help!

---

### Post by TheFu on 2020-10-14
Just install Ubuntu-Mate, then add the LXQt environment later, if you like. Adding another DE is about 5 minutes for the packages to download and install. It is a single command, then logout, pick the other DE and login.

I bet you'll like Mate. I know 20.04 Ubuntu-Mate installer supports LVM.  I'm using it.  I just accept the defaults for "Use LVM on whole disk", then, post-install, I reduce the "root" LV to 25-35G, create a "swap" LV of 4.1G, and create a "home" LV of whatever I need, usually start with 25-50G, if I have the space.

Anyway, that's an option.

---

