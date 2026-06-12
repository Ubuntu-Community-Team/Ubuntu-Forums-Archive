---
title: "Installing Ubunto on a partition w/ windows on another"
date: 2008-02-10
forum: General Help
---

### Post by carress on 2008-02-10
This is probably a basic issue, but  I'm stuck.  I'm trying to install windows and ubuntu on my new 120GB hd. I put windows XP on already, and I'm working on getting ubuntu on.


I have installed windows xp, and was able to partition my HD. Now in ubuntu, i think i see 2 partitions, and in windows, I see 1 C drive at 58GB, and unallocated space at 53GB.  am trying to install ubuntu now, and I'm not sure what to do. It's asking me to partition the disk, but I've already done that, and it seems to see tht it's partitioned b/c the slider for 'new partition size' is at 58.1GB- that part is orange, and everything to the right is gray. I get an error when I try the guided partition, and it brings me to the manual partition window. In the manual window, I think I see the two partitions. the first one says /dev/sda1 (or l-I'm not sure) - its type is ntfs (which makes me think it's the 'c' drive from windows), the mount point is /media/sda1 (or l?) the Format box is unchecked and uncheckable, the size is 62915MB, and 7500MB.  The second partition says free space, nothing for type and mount point, uncheckable Format box, 57116mb as size, and no used space.


I'm thinking I need to create a new partition within the free space..actually create 3 partitions...but I'm utterly lost at this point.  I don't know the difference between a primary and extended partition. I'm not sure how to create the right type of formatting (ext3, fat32), I'm not sure which formatting is for which partition. I did see a document on that, but can't find it now. I'm unsure how much space to leave for the 2 smaller partitions. Do they go in a particular order? 


I can't seem to find my situation in any documentation, and I have read a bunch of stuff in the last few days...  Is anyone willing to do some hand-holding??

---

### Post by vahnx on 2008-02-10
When I reformat, I install Windows XP first. Then right after I install XP, I boot into the Ubuntu 7.10 install disk and once it's up and running, I partition using Ubuntu's tools or whatever guide I followed online, and installed from there. I never partition from inside Windows.

EDIT: Just found this video. Haven't watched it but sounds promising. 14 minute tutorial.
[http://video.google.com/videoplay?docid=-6104490811311898236]("http://video.google.com/videoplay?docid=-6104490811311898236")

---

### Post by carress on 2008-02-10
thank you

---

### Post by vahnx on 2008-02-10
Also don't forget to create a Linux Swap partition. It should be about the same size or double the amount of your RAM from what I read. Just did some Googling and found this text guide, incase the video seems too long: [http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty]("http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty")

---

### Post by src2206 on 2008-02-10
Hello friend, a warm welcome to Ubuntu community :)

There are two solutions of your case. But before that please understand that to install and run Ubuntu you you need two partitions:

**1**. The main partition at least of **8GB in Size** partitioned with **ext3** file system. While installing you need to choose this partition to mount "**Root File System**" or "**/**"

**2**. Another partition of about twice the size of your installed RAM or 500MB, whichever is higher is required. This has to be your **SWAP** space (equivalent to pagefiles in Windows).

Now to do things:

I would suggest that you should download GParted and burn the ISO on a blank CD/DVD. This program comes free and its a great utility to create, modify or delete partition. Its about 50MB in size.

Now boot with GParted CD. And it will show you your HDD. Choose the unpartitioned space of your HDD and create two partition there, **one formatted as ext3 file system and the other as SWAP**. 

You can do the same as above with Ubuntu installation disc, during installation, but it will not as easy as GPrted and moreover as you already have Windows installed, chances are there that you are going to mess up your Windows partition (it happened with me while trying to install the latest in one of the PCs). GParted is far easier to use.

Now restart your PC with Ubuntu installation disc in your drive bay and proceed to page where you need to choose Prtition etc. Choose **Manual Partitioning**. Here look for the two partitions, one will be ext3 and the other will be SWAP. Just choose the ext3 partition to mount the "**/**" ie, **root** and the and the smaller SWAP partition to be used as a SWAP space. Now continue with your installation as usual. :)

BTW, **you can get pictorial guides on the use of GParted and Dual Booting Linux with Windows in my signature**.

---

### Post by carress on 2008-02-11
Thank you for the welcome and the guidance.

As I understood it, there were to be four partitions. 
One for windows.
One for ubuntu
One for swap which is double  the ram
and one other for....I'm not sure

What is the ext3 partition that you told me to put in for??


Also, GParted seems to be part of my ubuntu installation disk..is this different form the gparted you're telling me about??

I'm off to check out your signatures and the riches they provide...

Thanks.

---

### Post by src2206 on 2008-02-11
The GParted that I have suggested is a kind of stand alone full fledged Partition Editor and you need to boot with this to change its partition. As its primary job is partitioning, the partitioning job can be done better and with more flexible options. So using GPARTED you can ready your HDD before installing any OS.

Every partition needs to be formatted in a specific file system to facilitate the installation of a OS. Linux (at present) requires ext3 for the OS and SWAP for the swap partition.

The fourth partition is optional. You can keep it for data important for your work, so that you do not have to worry about those in case Windows crash (which is expected to be a far more frequent affair in comparison to Linux).

---

### Post by carress on 2008-02-12
ok.. I read that I needed to make ubuntu mount from  /   so I tried to change it, but then it said that the drive was not formatted... 

Anyhoo... I tried to check to see if I could still boot into windows, and the computer won't boot from the hd at all... ** changed the  flag back to boot for the first partition...can boot to windows now... not sure how to change the mountpoint...

I am going to try to unpartition the drive...  ***nevermind 

I'm realatively clueless...but adventurous and daring... ****still daring.

---

### Post by src2206 on 2008-02-13
Sorry to say, but it seems that you messed up your partitions :(

Did you use GParted to format the installation partition for Ubuntu to ext3 file format?

---

### Post by geebob on 2008-02-13
Greetings,
I am very new to the linux scene and I am considering installation of umbutu on my computer.

Do I understand correctly that if I use this Gparted program, I can make partitions without touching windows?  What I mean is I want to install umbutu without having to erase and reinstall windows to have them both on my computer.  I want to leave windows and all my other files as they are.

---

### Post by froy02 on 2008-02-13
> **geebob said:**
> Greetings,
I am very new to the linux scene and I am considering installation of umbutu on my computer.

Do I understand correctly that if I use this Gparted program, I can make partitions without touching windows?  What I mean is I want to install umbutu without having to erase and reinstall windows to have them both on my computer.  I want to leave windows and all my other files as they are.

You don't have to use Gparted at all if you are using Alternate CD install disk.  
If you already have windows installed just tell the installation program to resize the windows partition when it gets to section on where to install it and you choose how much space to allocate to Ubuntu.  It will do the rest for you, resize then partition.   It will make the ext3 partition (where Ubuntu will install) and the swap partition.  About 20 to 40 gb for Ubuntu is good.

---

### Post by geebob on 2008-02-13
I don't have the alternate CD but rather, I have the live DVD.  I'd rather not download an entirely new disc image.  The other thing is that I've heard that some people lost the ability to boot after repartitioning with ubuto's repartitioner (apart from this thread).

---

### Post by geebob on 2008-02-13
Also, for some reason, windows didn't want to shrink the OS disc more than 18 MB and I'd be afraid to shrink it more than windows allowed.

---

### Post by geebob on 2008-02-14
Okay, well, I'm going to take the plunge.  It seems implicit to me from this thread that if I repartition with Gparted, it will not affect windows.  I was hoping for an explicit affirmation but I geuss I will just risk it.  I will do it later this evening unless someone comes screaming into the thread "No geebob, don't do it, think of the children!"

---

### Post by ubuntu27 on 2008-02-14
> **geebob said:**
> Okay, well, I'm going to take the plunge.  It seems implicit to me from this thread that if I repartition with Gparted, it will not affect windows.  I was hoping for an explicit affirmation but I geuss I will just risk it.  I will do it later this evening unless someone comes screaming into the thread "No geebob, don't do it, think of the children!"

Before you partition your harddrirve. DEFRAGMENT your Windows partition first. 
You can use any application you want to defragment, the default in WIndows "Disk Defragmenter", or you can use JKDefrag: [http://www.kessels.com/JkDefrag/](http://www.kessels.com/JkDefrag/)

---

### Post by geebob on 2008-02-14
thanks for the advice.  I did earlier today (or yesterday) but I think I'll do it once more to be on the safe side.

---

### Post by geebob on 2008-02-15
Well, I got it the hard drive partitioned and feisty installed.  IT was not fun but of course in gathering the information and moving cautiously, I probably was more cautious than most as I really didn't want to lose windows.  I haven't booted windows since I've gotten ubuntu going though.  I probably should check that out.  Thanks to all for the advice.

---

### Post by ubuntu27 on 2008-02-15
> **geebob said:**
> Well, I got it the hard drive partitioned and feisty installed.  IT was not fun but of course in gathering the information and moving cautiously, I probably was more cautious than most as I really didn't want to lose windows.  I haven't booted windows since I've gotten ubuntu going though.  I probably should check that out.  Thanks to all for the advice.

Good job! :) Being cautious is a good quality.

I have a question for you. Why did you choose to install Ubuntu 7.04 (Feisty Fawn) instead of Ubuntu 7.10 (Gutsy Gibbon)?

*****

Mark This thread as "[Solved"]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads").  When a thread is marked as solved, it show us forum users that the problem presented in this thread was solved.

How to mark a thread as "Solved":
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

