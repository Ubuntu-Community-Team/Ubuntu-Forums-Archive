---
title: "lost my entire hard drive + windows installing ubuntu"
date: 2007-11-08
forum: General Help
---

### Post by charles_316 on 2007-11-08
i was running windows xp professional and decided to try and install ubuntu 7.10 on my thinkpad t60...

when i got into the ubuntu setup (after some vga problem blue screens - error display server etc) it said i had 120gb free which i thought was wierd because that is my entire hard drive and i had windows installed on a separate partition...

anyways i decided to backup some files and then try again.... i created a partition of 10g within the ubuntu setup and then went on to install ubuntu...

now i dont have windows anymore and when i try to install windows, the cd complains there are no hard drives... i guess ubuntu somehow made the entire hard disk EXT3 and windows cannot see it?

is there any way to check the hard drive for my previous files from windows? looking from ubuntu, i can only see the 10gb partition i gave it and nothing else..

thanks

---

### Post by knowledge_is_power on 2007-11-08
hmmm, im no pro, but i know that even if the whole disk was EXT3, the windows installer would be able to see it and attempt to reformat it in NTFS.  Try booting with the live CD and running gparted (System->admin->partition editing) and see what it tells you.

---

### Post by Ub1476 on 2007-11-08
Well, the Ubuntu setup allows you to use the entire HD, use free space available (if you created a 10gb partition it would show that option) and custom. 

If Windows is still on your HD, its partition should show up in "Computer". You can also boot up the live cd and check your partitions with gparted. 

If Windows is gone, then your files are lost. The reason Windows says it can't find any HDs is because it doesn't have drivers for your SATA/Raid HD.

---

### Post by charles_316 on 2007-11-08
I think it is prolly best to start fresh now...

What is the recommended allocations and number of partitions to dual boot windows and linux?

how many partitions are needed for ubuntu - one for swap and one main? 

I was thinking out of 120gb....  20gb for windows os
20gb for ubuntu main
2gb for swap or 1gb?
and the rest for data 

any advice would be appreciated

---

### Post by charles_316 on 2007-11-08
Can that partition editor within ubuntu create a ntfs or fat32 drive so i can reinstall windows?

What's the best way to start fresh now? 

Format the entire hard drive somehow.. then install windows... allocate appropriate drives... then install ubuntu ?

---

### Post by djrobthaman on 2007-11-08
I don't think that ubuntu can do anything to hide a hard drive from any os install cd.  What might be the problem is your hard drives could be on a different bridge (I think that's what it's called) than your cdrom drives.  When I bought my desktop, I had the same message from the xp pro install cd (no hds detected) for at least 3 days before I realized that was my problem.  If it's something that simple, then along with the windows cd you probably got a driver disk (yeah... a floppy disk, the latest and greatest in technology) or at least that's what I got.  When the xp cd starts, there's a point where at the bottom it says if you want to install this driver press F1, that driver press F2... and so forth.  I think it's F6 you want to press.  Nothing will happen for a while, the cd will load up as usual until it's almost all the way done and a message will come up prompting you to install the driver.

Once you get this done with you WILL see the hard drive.  If like you think it's all ext, then it will just say it's an unknown format.

Another thing that happened to me recently was I tried to install ubuntu on an extended partition instead of a primary partition.  Big mistake (at least it was for me... maybe some linux guru could have gotten it working).  When I restarted, like you I could not load up either windows or linux.  Even when I loaded up the ubuntu livecd, gparted (the partition editor) saw the extended partition but could not delete it).  What I had to do was load up the windows installer (yes...windows software actually did what the ubuntu software could not... scandalous) and delete every partition that I saw there that I knew was not there I messed up with that extended partition rubbish.  Once I did this, everything was back to normal.

Anyway, one or both of these could be your problem.  I hope that if it is, it's as easy as doing what I did to fix it, if not I wish you all the best in your troubleshooting endeavours.

---

### Post by dabl on 2007-11-08
Probably djrob is correct, regarding the "driver diskette" that is needed to install Win Xp on that particular machine.

Here's the general sequence of events that you need to follow:

1. Partitioning -- I use the GParted Live CD, available as an ISO download [[COLOR="Magenta"]**here**[/COLOR]](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)

You can do what you want to do with 4 primary partitions:

20GB for windows
10GB for Ubuntu "/" including "/home" (assuming you won't have a lot of Linux-specific data)
0.5GB for Ubuntu swap
the rest of it for shared data

2. Install Win XP _first_

3. Install Ubuntu last, and let it write Grub to the MBR. This will get you a boot menu that includes Win XP as a bootable OS.

HTH!  :)

---

### Post by Yarbo on 2007-11-08
This sounds like something that happened to me when I first tried to reinstall Windows on my Dell.
 
In the BIOS under the drive settings, there were a few different settings for SATA drives.
 
The choices were something like AHCI or something, and then RAID.
 
My computer had been set to RAID for some reason, and windows could not find the raid controller or drivers, so it was not finding any hard drives.  As soon as I switched it to AHCI mode it detected all of my hard drivers without any problems.
 
I suggest you check your BIOS configuration utility. It is usually accessed by pressing a specific key during the initial boot sequence.  
 
For example on my Dell I have to hit F2 when the Dell logo is on the screen.
 
Hope this helps.

---

### Post by charles_316 on 2007-11-08
thanks a lot for the advice guys..

i am going to try the Gparted live cd... boot from that and try to partition my entire hard drive correctly...

somehow even my recovery mode hidden files from ibm are gone.... ubuntu completely took out everything somehow.... so now my ThinkVantage blue button that goes to rescue and recovery doesnt work lol

---

### Post by charles_316 on 2007-11-08
Thanks so much guys! 

Everything works now... I couldn't have done it without ur advice

---

### Post by Xandan on 2008-03-10
i know that this topic is quite old but, i also have not been able to reinstall vista after installing ubuntu. Now windows is unable to detect my hard drive. can someone please help?

---

