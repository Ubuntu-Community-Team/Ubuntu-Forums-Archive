---
title: "Suggestions anyone? Should I partition?"
date: 2008-01-22
forum: General Help
---

### Post by Chessmaster on 2008-01-22
Hi all,

I have two hard drives. One with Gutsy (40GB) and the other with Windows XP (80GB). 

I am currently loading up my CD collection onto my gutsy drive. But, seeing as I don't use the XP drive much (if at all!) and have a load of free space on it, I was thinking about loading all my music onto that drive. 

Couple of questions to which suggestions / comments / advice would be good. 

a) will storing music on another drive other than that which the player is on cause any problems / delays etc. Is it advisable to keep music and music player on same drive?

b) I do not want to remove the windows XP installation, but have lots of room on that drive. If I am going to keep my music on that (the windows) drive is it worth partitioning that drive so the music will be effectively on a seperate drive. I wonder this because (in the rare event) if I have have to use XP will it play havoc with my music files that have been loaded up through Ubuntu? Say I defrag etc. 

Any suggestions would be great. What do you do?

Cheers

---

### Post by LaRoza on 2008-01-22
Separating your data from your OS is a good idea. I do it. 

I used to have a setup like yours, and I shrunk the Windows partition (with GParted) and created a new partition for my files. It is worth it.

When you make the partition, I recommend you don't format it with GParted. Let Windows format it as NTFS.

You will have to add it to fstab for Ubuntu [http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

>a) will storing music on another drive other than that which the player is on cause any problems / delays etc. Is it advisable to keep music and music player on same drive?

No, it will be fine. It may speed things up. 

>b)If I am going to keep my music on that (the windows) drive is it worth partitioning that drive so the music will be effectively on a seperate drive. I wonder this because (in the rare event) if I have have to use XP will it play havoc with my music files that have been loaded up through Ubuntu? Say I defrag etc.

It is worth partitioning it for the data. Defragging just moves the files around, and is no threat to data.

---

### Post by erpo on 2008-01-22
> **Chessmaster said:**
> Hi all,

I have two hard drives. One with Gutsy (40GB) and the other with Windows XP (80GB). 

I am currently loading up my CD collection onto my gutsy drive. But, seeing as I don't use the XP drive much (if at all!) and have a load of free space on it, I was thinking about loading all my music onto that drive. 

Couple of questions to which suggestions / comments / advice would be good. 

a) will storing music on another drive other than that which the player is on cause any problems / delays etc. Is it advisable to keep music and music player on same drive?

b) I do not want to remove the windows XP installation, but have lots of room on that drive. If I am going to keep my music on that (the windows) drive is it worth partitioning that drive so the music will be effectively on a seperate drive. I wonder this because (in the rare event) if I have have to use XP will it play havoc with my music files that have been loaded up through Ubuntu? Say I defrag etc. 

Any suggestions would be great. What do you do?

Cheers

a) No and no.

b) No and no.

---

### Post by housam on 2008-01-22
A separate partition ( FAT 32 ) for your all data including music will ease importing them by both OS  to any music player.

---

### Post by LaRoza on 2008-01-22
> **housam said:**
> A separate partition ( FAT 32 ) for your all data including music will ease importing them by both OS  to any music player.

NTFS would be better, if the OP is using 7.10.

FAT32 is a very portable file system, but fragments horribly and isn't very secure.

---

### Post by housam on 2008-01-22
> **LaRoza said:**
> NTFS would be better, if the OP is using 7.10.

FAT32 is a very portable file system, but fragments horribly and isn't very secure.

You are right. I agree with you.

---

### Post by LaRoza on 2008-01-22
> **housam said:**
> You are right. I agree with you.

FAT32 is what I used to use pre 7.10, for data sharing, so NTFS being easily used is new in Ubuntu.

---

### Post by Chessmaster on 2008-01-22
Thanks for the advice.

Looks like I will partition then. 

Also, seeing as XP does not recognise my Ubuntu drive and contents, should I ever (on the off chance) want to play music in XP it would be very hard indeed! (I am guess there is a fix for this in Windows). 

LaRoza, just checked out your "learn to program" website - looks cool, and will definitely give it go! :)

Cheers

---

### Post by LaRoza on 2008-01-22
> **Chessmaster said:**
> Thanks for the advice.

Looks like I will partition then. 

Also, seeing as XP does not recognise my Ubuntu drive and contents, should I ever (on the off chance) want to play music in XP it would be very hard indeed! (I am guess there is a fix for this in Windows). 

LaRoza, just checked out your "learn to program" website - looks cool, and will definitely give it go! :)

Cheers

You can get a driver for XP to read EXT3 partitions, however, I wouldn't use it. Create a new partition for the data. Logical and safe.

Thanks for visiting my wiki, I try to make it useful. (It is useful to me, so I imagine others find it useful)

---

### Post by housam on 2008-01-22
You can also make your XP recognizing ubuntu drives if you install the fs-driver from [[COLOR="Red"]this link [/COLOR]]("http://www.fs-driver.org/").

---

### Post by LaRoza on 2008-01-22
> **housam said:**
> You can also make your XP recognizing ubuntu drives if you install the fs-driver from [[COLOR="Red"]this link [/COLOR]]("http://www.fs-driver.org/").

In my opinion, that is a bad idea. As far as I know, that allows Windows to access Linux system files, not a good arrangement.

(I don't allow Linux to acces Windows system files either)

---

### Post by housam on 2008-01-22
> **LaRoza said:**
> In my opinion, that is a bad idea. As far as I know, that allows Windows to access Linux system files, not a good arrangement.

(I don't allow Linux to acces Windows system files either)

I used to access both systems since Dapper till Gutsy without any problems.

---

### Post by Chessmaster on 2008-01-23
Ok, so I have a couple of questions about repartitioning my Windows Hard Drive. 

At the moment, windows takes up the whole drive space - and only about 7GB of the 80GB drive. 

If I want to reduce the windows partition to say 15GB so I can use the other 65Gb for data/music storage what do I have to do? 

As a guess: Do I resize the windows partition to 15GB (which will free up 65GB as empty space)? Then do I install a new partition from 15GB through to 65GB? Should this new partition be logical or primary? What is the difference? 

Any suggestions as to what freeware I can use? Is Partition Logic any good? I want to keep that drive NTSF (so windows can also read the files on it) but am I correct in saying that Partition Logic can resize NTSF partitions but cannot create them - or have I interpreted the website incorrectly? [http://partitionlogic.org.uk/about/index.html](http://partitionlogic.org.uk/about/index.html)

Sorry about all the questions (especially about Windows drives! - but I do want to access them with Ubuntu so it is kinda relevant :)) - and I am a relative newcomer to ubuntu and here seems like the best place to find this stuff out. So far responses to questions have been great! 

Cheers

---

### Post by housam on 2008-01-23
- First of all you have to back-up your data - just in case.
- Do defrage your HDD 2-3 times and notice the position of the green sector ( windows file system ) . let say at 40% from the left side.
- This means that you cann't resize windows partition to less than that size of the HDD or you'll damage it.
- Use Gparted tool ( on the live CD ) to do the partitioning task.
- You can create up to only 4 primary partitions on single HDD.
-I suggest to create 3 primary partitions and make the 4th one as extended which can be devided to many logical partitions.
- You'll devide the extended partition to 2 partitions : one EXT3  ( 20 GB is a good space ) for installing ubuntu as a root partition  ( / ). and the other one as a swap ( only 1 GB ).
- During the installation process when it comes to the partitioning choice choose the manual way and assine the EXT3 as a root ( / ) .

GOOD LUCK

---

### Post by Chessmaster on 2008-01-23
Thanks for the quick response.

I defraged last night (I will again before I partition) and you are right, the green line is about 40% of the way. So, I assume that I should probably resize the windows partition to about 50% (giving me 40GB for windows - what a waste of space! :) and 40GB for the rest). 

I already have Ubuntu on another drive (I am dual booting on two different drives) so I am assuming I only need to make one new primary partition then as I really only want it for music and data backups etc. 

If I use GParted will the new partition be NTSF and will I be able to access it through windows? (I ask because I have no problem accessing my windows drives through ubuntu but not visa versa - I downloaded "Ext2 Installable File System for Windows" and I can now see my Ubuntu drives from Windows but not look inside them (i.e. they now appear in explorer but when I double click on them windows asks if I want to format them! - I will run the Ext2 Diagnostic tool tonight to see why this is the case).

Cheers

---

### Post by housam on 2008-01-23
> **Chessmaster said:**
> 

If I use GParted will the new partition be NTSF and will I be able to access it through windows? 
Cheers

Yes Gparted can create a NTFS partitions and you'll be able to access them from windows.

---

### Post by Chessmaster on 2008-01-24
Hey all, thanks for the help! :):)

GParted was nice and easy to use and I successfully partitioned the drive as desired. 

I mounted the drive / partition and when I boot up it is there and I (and importantly Amarok!) can read it just fine.  

Great step-by-step guide for mounting partitions here: [http://www.stchman.com/part.html](http://www.stchman.com/part.html)


Thanks!

---

