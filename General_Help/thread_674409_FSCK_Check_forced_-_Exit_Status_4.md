---
title: "FSCK Check forced - Exit Status 4"
date: 2008-01-21
forum: General Help
---

### Post by zaffod on 2008-01-21
Hi everyone.

I need an opinion on a file system issue I experienced using Ubuntu Feisty.

Been running Feisty as the main family desktop for almost a year and it's been mostly plain sailing.

I have noticed that on boot up, it forces a file system check every 38 boots. This takes ages but has always completed without issue and the system comes up fine.

A few days ago though, the file system check exited with error code 4, dropped me into a shell with instructions to run fsck manually. I did this and developed some apprehension at what I saw:

* Thousands of issues were found and I was asked to 'clear' or 'repair' indoes? etc.. I held down the 'y' key for 10-20secs to answer yes to these questions.

* Then hundreds screen fulls of numbers scrolled up my screen. At this point I thought my machine was in a melt down.

* But then it asked to 'clear' or 'repair' more inodes, to which I answered yes again.

Eventually fsck exited and I rebooted to Feisty with no issues.
Having backed up my data, I've been using the machine for several days and have not noticed any problems.

My questions:

Why were there so many errors on my drive?

Is this indicative of a fault with the drive?

Should I replace the drive?

Should I be concerned?

Should I use tunefs to force a check more often?

During install, I opted for the default partition scheme.
Should I have partitioned the drive differently?


Thanks for any comments,
karl

Hardware:
AMDx2 Dual Core 4800+
200GB Sata Seagate Drive
3GB RAM
Mobo ASUS M2N-MX

---

### Post by Herman on 2008-01-24
:) Hello zaffod,
>  During install, I opted for the default partition scheme. Should I have partitioned the drive differently? No, that shouldn't make any difference, I always use the default partition scheme too. 
>  Should I use tunefs to force a check more often?
 If your file systems are checked more frequently, like around 28 or 30 boots or so, it might find problems while they are still small, and the old saying 'a stitch in time saves nine', seems to apply well to file system checking.

A better idea is to use either an up to date version of Ubuntu LiveCD or an up to date version of [GParted -- LiveCD]("http://gparted.sourceforge.net/") and use GParted to run a proper e2fsck with. 
It's GUI, you just open GParted and right-click on the partition you'd like to have checked and repaired, and click 'check' from the right-click menu. Then you hit 'Apply' on the toolbar, and 'Apply' again in the confirmation Window.
That will run a much more effective file system check than just the normal start-up fsck, and should keep your ext3 file system in top shape.
 You can run that as often as you like.
>  Why were there so many errors on my drive?
Is this indicative of a fault with the drive?
Should I replace the drive?
Should I be concerned? I don't know, I can't really answer any of those questions. It could quite possibly have been caused by temporary  environmental factors. Can you remember anything unusual?

You might want to take a look at your hard drive with smartmontools. That might shed some light on it for you with a little luck, Here is a web page that explains how, [Check On Your Hard Disks With Smartmontools]("http://users.bigpond.net.au/hermanzone/p20.html#Check_On_Your_Hard_Disks_With"). 
Smartmontools can be installed in Ubuntu, with 'sudo apt-get install smartmontools'. ```
sudo apt-get install smartmontools
```

---

### Post by zaffod on 2008-02-02
Hi Herman, 

Thanks for you suggestion. I will look into smartmontools. 
I have some more details regarding what happened to my system, that I need some answers for. 

My lost+found contains 457 items totaling 1.2gb.

100% of the files there are from my mp3 colelction, names like nomad.mp3, one drop east.mp3 etc..... Some of the files have mutated with other files and are no longer mp3s. Example, "Blood Suagr Sex Magik" appears as an executable file in lost+found. Another appears as a txt doc. All the files are in folders called #24756632 etc with only the last 3 digits changing.

There were also hashed up files that ended up having their names mixed with other file names. Real mess.

All the files in there have been lost from my mp3 collection. They all seem to be bands starting with "r" or "s". Like REM, Red Hot Chillis .... There are some remnants in the original location. Like the folder REM is now an executable.

I forced an fsck -y on the next reboot and a few errors were found, with files I'd restored from lost+found. The whole check was quite quick, but I had to run it manually after being dropped into a shell.

Something has failed somewhere, either in software or hardware.
I just need to know where so I can fix it. 

Since then I have set fsck to run every 4 boots and things have been stable.

---

### Post by Herman on 2008-02-02
Wow! That really was a spectacular event then.
What method did you use for restoring your files from /lost+found, if you don't mind?

This type of thing is quite rare and I'm interested to learn more about it too.

An improper (sudden) shutdown is probably the leading cause of file system problems.
Some people shut the computer down wrong if their operating system freezes up on them for some reason (hardware driver issues maybe).
[                To find and 'kill' a runaway process]("http://users.bigpond.net.au/hermanzone/p10.htm#To_find_and_kill_a_runaway_process:")  |   [                 Proper techniques (in the event of a frozen system ) to prevent filesystem damage]("http://users.bigpond.net.au/hermanzone/p10.htm#to_prevent_filesystem_damage")
                          A blown household fuse or thrown circuit breaker or a power blackout can be the cause of having the computer shut down suddenly.   
A faulty power supply unit can cause the computer to shut down and reboot unexpectedly.   
A good quality power supply unit probably would shut down suddenly if it couldn't supply the right electricity to the motherboard and hard disks for any reason, rather than supply the wrong voltages.
 The electricity we get from our household or office electrical supply authority isn't perfect either. 
Lightning strikes are a frequent cause of out of spec electricity. 
I use a UPS units to try to help protect my PCs from power interruptions and out of spec electricity which we often get where we live.

Can you remember if your computer has ever been shut down suddenly or has ever rebooted on it's own unexpectedly?

Then you have thermal issues. Something as simple as a stray piece of paper blocking a vent or the PC case being pushed too close to a wall for a while or something like that can cause parts of a PC to overheat and that can cause problems too. 
Hard drives need adequate cooling the same as many other parts of the PC.

If your hard drive supports S.M.A.R.T. then is a good chance that the error was logged in the hard disk's firmware and a record of it still exists in the hard disk's memory. You may be able to use smartmontools to see what happened and then you might know how to prevent the same thing happening again, or if it can be prevented.

The best thing to do is to make regular backups of all data we want to keep safe. 

Here's a link to a website with a lot of interesting information on hard disks, [Brief History of the Hard Disk Drive | StorageReview.com]("http://www.storagereview.com/guide/hist.html").  

Hard disks are made a little bigger than their advertised usable size. There is an area of space held in reserve. When the hard disk is low level formatted, there are already some bad sectors and those are swapped out electronically and replaced with sectors from the reserved area. As the hard drive is used, bad sectors show up over the hard disk's life time and are silently swapped out and traded for another sector from the reserved area without the user being aware of it. It's handled automatically by the hard drive's firmware. When the hard drive is nearing the end of its useful life, the reserve area of spare sectors are all used up, and bad blocks will begin to show up when we run a bad blocks check. [                        Running a check for bad blocks on your hard disk]("http://users.bigpond.net.au/hermanzone/p10.htm#bad_blocks_check").

Regards, Herman :)

---

### Post by zaffod on 2008-02-03
Hi Herman, 

Thanks for the links. 

To restore the files I just did:
find /lost+found -type f exec mv --target-directory /var/mp3s/FOUND {} \;
(that's from meory, not sure of the exact syntax I used)

I ended up trashing the 'found' files and restoring from a pc I have dedicated for media stuff (runs Windows). 

My main concern at the moment is determining if this is a linux file system related issue, hardware failure of just bad luck. 

Data loss is unforgivable of any computer system, particularly an OS.
I have previously been a Windows user and have been much more brutal with Windows. Cold reboots galore. Lockups, blue screens (even in XP)... etc.
**Never ever lost data.**

No, my machine has never rebooted on its own, and I have not had to do very many cold reboots on Feisty. I only experienced crashes when I enabled "Desktop Effects". Never done so again.

All my hardware is brand new. I built the system from scratch in a [g4 case]("http://webfusion.net.nz/g4pc").

I love linux and have 'played' with it since RH6.
But I am left wondering if my recent data loss experience is more related to the OS rather the very few crashes I have experienced with it.

Is ext3 really better than NTFS or fat32?
Could this be a linux issue *perish the thought*? 

Cheers, 

Karl

---

### Post by Herman on 2008-02-04
>  All my hardware is brand new. I built the system from scratch in a [g4 case]("http://webfusion.net.nz/g4pc"). Hey, wow! I read through that link and looked at all the pictures, that's way cool there, zaffod, I like it! :)
```
 find /lost+found -type f exec mv --target-directory /var/mp3s/FOUND {} \;

```Thanks for sharing.

Your file system catastrophe seems very mysterious, no-one else has reported anything like it that around here that I'm aware of. 
I have participated in threads where the Windows ext3 driver has damaged ext3 file systems, and I have helped with ext3 file systems on failing hard disks. I even experienced that first hand myself one time. I have also helped repair many ext3 file systems that just needed a good file system check. This is the first time I have ever heard of the idea that the Linux kernel or the ext3 file system itself might not be reliable.
Apart from trying out smartmontools to see if that tells any stories I don't know what else to suggest.
I guess just back up your data and see if anything like that ever happens again. Maybe it won't happen again for the rest of your life.

Regards, Herman :)

---

### Post by zaffod on 2008-02-04
Thanks Herman, 

yeh I kinda betting on that too:
"Maybe it won't happen again for the rest of your life." 
Hopefully it was a freak incident, a very strange one at that. My machine has been very stable since. Running an fsck every four boots has not found any errors so far. 

But I take data loss quite seriously. I don't think it was linux issue per se but I hoped to hear from people who might set my mind at ease... 

There have been a few posts on other forums about data loss in ext3, but no more than for any other OS. 

The incident I experienced has got me interested in linux filesystems vs windows file systems. 

I will check out smarttools in the near future. And i will run badblock when I have read up on it. Your page was veryuseful actually, but I only skimmed it at work. 

I'll post results here for those that may stumble upon this thread.

---

### Post by Herman on 2008-02-04
Cool! :)

Hey here are a few of my favorite links in case you'd like to learn more about the ext3 file system too,
 [5.10. ]("http://www.tldp.org/LDP/sag/html/disk-usage.html")[Filesystems]("http://www.tldp.org/LDP/sag/html/filesystems.html")

[Design and Implementation of the Second Extended Filesystem]("http://web.mit.edu/tytso/www/linux/ext2intro.html") 

 [EXT3, Journaling Filesystem]("http://olstrans.sourceforge.net/release/OLS2000-ext3/OLS2000-ext3.html")

 **[Linux ext3 FAQ]("http://batleth.sapienti-sat.org/projects/FAQs/ext3-faq.html")**

I don't know much about NTFS.

Regards, Herman :)

---

