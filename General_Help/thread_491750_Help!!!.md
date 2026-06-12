---
title: "Help!!!"
date: 2007-07-04
forum: General Help
---

### Post by fraterchaos on 2007-07-04
Recently, I temporarily lost my interent access. Out of boredom, I decided to install Ubuntu Linux on my Windows XP computer (I had had Ubuntu installed before, on another machine running Win2000 Pro) 

When I began the installation, I was presented with the disk partitioning screen, I chose the "manually edit partition table" option. My system has two Hard drives, the first (C: under win) is a 13 gig drive that holds windows and most of the installed programs, the second drive (D: under win) is a 60 gig Maxtor, which I was using to hold about 30 gigs of movies, tv shows and other video files (mostly, there were also some program downloads, and Poser and Bryce content files) Also, the volume was NTFS and compressed.

Ubuntu had no trouble recognizing the first drives partiton, which is also NYFS and compressed, but when I switched to the D: drive (where I wanted to repartition to give Ubuntu about 10 gigs to live in) it would not recognize that there were ANY partitions on the D: drive, listing it as "unallocated". I immediatedly aborted the whole installation, and rebooted to WinXP. And to my dismay, winXP was also reporting that the second drive was unformatted and empty. I do not believe that Ubuntu actually erased any data, as it took absolutely NO time at all to show the drivve as empty, and if it HAD actually erased the data, it should have taken a measurable amount of time to do so.

What I need to know is this: what did Ubuntu do to my drive? Is there any way I can restore the data?

I have tried a couple of "partition table rebuilding" programs I downloaded, and either they require a fee and registration (which I simply cannot afford at this time) or they report no restorable partitions. I would guess that all that needs done is to rebuild the partition table, but I'm not enogh of a Geek to do this manually. Anybody know of any FREE program that will actually rescue this drive?

I can't use a file by file restore since I don't have enough space on C: to save the restored files. I need a program that can restore the entire drive. I have tried WinXP's "Restore" function, and that does not work either.

PLEASE PLEASE PLEASE, somebody tell me what Ubuntu did to my drive and how I can get it back, as I don't relsih the thought of trying to re-download 30 gigs of data, providing I can even find all of it.

If you can, I'd prefer you email your responses to me directly at [email]fraterchaos@yaoo.com[/email]. Often, I don't receive notifications that I have forum responses (maybe yahoo thinks they are spam, I don't know, but if I turn the spam filter off I get thousands of spams a day)

Thanks

---

### Post by Das Oracle on 2007-07-04
First of all, I don't mean to sound negative but Ubuntu Live CD used gparted or gpartd. It does not ensure that the information stays in the partition when you change it. (I found this out after loosing everything on my storage drive.

Second, aborting does not save from what a partition change does, especially if you don't let it finish. It was making modifications to the partition tables and you told it to stop so it could not properly finish. Chances are you are stuck with what you have.

I am not a partition guru, but this was my experience. There may be someone else here who can save the day but hold that with a grain of salt.

**Edit**

please make sure that if you value information on a drive when you go to play with it's partitions, that you back everything you care to save up. Since my mistake I have bought a bundle of dvd-rw's for such instance. Haven't used them yet, but just in case.

---

