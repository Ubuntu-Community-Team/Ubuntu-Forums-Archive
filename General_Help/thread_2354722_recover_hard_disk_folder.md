---
title: "recover hard disk folder"
date: 2017-03-05
forum: General Help
---

### Post by jgw on 2017-03-05
I have two hard drives.  I have lost a folder from one of these drives.  The drive is used for storage and does not hold my home directory.  I have no idea what happened but suddenly my system just started deleting everything from a folder and then the folder went away as well and now I am in serious trouble. 

When it was deleting stuff it first deleted all the folders in the folder that is now gone and then it deleted the folder itself (now empty)  At the time I was simply browsing the drive and suddenly stuff started happening.  This tends to make me think I may have to recover individual files.  We are talking, here, about over a terabyte of data and hundreds of files.  I just checked the drive again.  Whilst files tells me stuff is there, when I click on anything the folder is empty - it would seem that my entire drive has been deleted (when I check the properties of the drive it tells me, under contents, "nothing").  This is very strange.  I should also mention that when it was going on (I tried to stop it but failed) stuff was going away VERY quickly.  If I get the properties of the drive it tells me that 1.7gb is available. which tells me a lot of the drive is used (with the stuff that got deleted)

I installed testdisk but it thinks (I think) that its an unknown partition.  Below are photos of gparted and terminal on this.  I also have another photo of how discs sees the drive.  Couldn't figure out how to attach to this in edit so i put it into a reply:
[ATTACH=CONFIG]274008[/ATTACH][ATTACH=CONFIG]274009[/ATTACH]

I notice that there are no replies to this.  When this happens it usually means that I should look something up.  I spent a lot of time researching this and came to the conclusion that there seems to be a LOT of answers which tend to confuse me.  Just wanted to say that I have tried to find an answer and just found waaay too many to try without getting advise.

I need to know my next move.  How about using gparted to rescue.  

Thank you....................

---

### Post by jgw on 2017-03-05
here is a photo of discs, and files for the drive:
[ATTACH=CONFIG]274013[/ATTACH][ATTACH=CONFIG]274014[/ATTACH]

---

### Post by jgw on 2017-03-06
is there anyway to list all the files on a drive that has had all files deleted?

thank you................

---

### Post by Bucky Ball on 2017-03-06
Please give a full explanation of what you are trying to do, how you are trying to do it and the details of the disk, what you have tried and the current situation and we have a better chance of helping.

---

### Post by lisati on 2017-03-06
Is this related to your questions in your [other thread]("https://ubuntuforums.org/showthread.php?t=2354722")?

---

### Post by oldos2er on 2017-03-06
If they have been soft-deleted; in other words, moved to Trash, then ```
ll -R .local/share/Trash/
``` Otherwise no such list exists unless you keep one manually.

---

### Post by jgw on 2017-03-06
This is related to another of my posts.  I decided to take a look at the drive.  I used ls to take a look with, if I remember right -lha * which listed all the existing folders and what was in them that got deleted.  I did not find, however, one of the folders that held a 'LOT of data which is why I asked this question.  I want to undelete or save the deleted files so I am trying to get all the info I can before I attack (hopefully somebody will get back to me on saving deleted files).

When the files were deleted I have absolutely no idea what happened.  I looked up and found it displaying, very fast, every file on the drive.  What was happening is that every file on the disk was being erased.  Now, when I look at the drive properties/contents it says "nothing" although I know there is stuff there.  This is a 3tb drive and it says there is 1.7tb free.

Thanks for the response.

---

### Post by lisati on 2017-03-06
Threads merged.

---

### Post by jgw on 2017-03-07
Thank you for merging this and thanks for any responses.  

I removed the drive in question from the machine.  Then I couldn't boot the machine.  I got that kinda fixed and then I spent the rest of the day putting out fires on the main drive.  I tried to install a new copy of ubuntu on the drive and that went just fine until it told me it couldn't install grub.  I gave up on that one and, hopefully I can get my program setup stuff off that drive and put it on the new one.  I still need to know the best way to get deleted files off a drive.  There are a LOT of thoughts on this one and everybody seems to have a favorite but some are older than others so I thought I would ask the question:  What is the best way to recover deleted files?

Thank you....................

---

### Post by Bucky Ball on 2017-03-07
testdisk and photorec. Test disk is in the repos or with a bunch of other extremely useful stuff on the [SystemRescueCD]("http://www.sysresccd.org/SystemRescueCd_Homepage").

---

### Post by jgw on 2017-03-08
Thanks for the replies

I tried testdisk/photorec  That program did not recognize my partition.  Since I tried to reinstall a new copy of ubuntu my partition type, according to gparted is msdos and disks say the partition is master boot record.  I will give it another whirl.  I also downloaded, and created, a systemrescueCD.  I will see how it goes.  I am currently working with another drive so now all I have to do is transfer the stuff I need off of that and then I will repartition and install.

---

### Post by jgw on 2017-03-10
Thank you for the reply.......

I now have the drive attached to a computer by usb.  I have booted the rescue disk and chose testdisk.  It seemed to find the drive although it was not turned on, at the time (button on the external box)  Anyway, its the only 3tb (3000gb) disk so I guess its looking at the right drive.  My problem is that I choose analyze first and it started to do just that.  the results are a bit confusing in that it reports on three separate things, separated by a comma and I have no idea what I am looking at but it look like its finding an error on everything its looking at.  I choose to create a log but have no idea where it might be.  I am also reading the documentation and it says it can recover files on an ext2 drive and the drive, with the problem, has an ext4 file system.  I also notice that if it does recover it needs someplace to put the recovered.  This means I have to have another drive (ordered as most recovery things need this)

I have to go away until Monday by order of wife.  I should have the new drive when I get back.  I am also thinking of opening up the system I have the usb drive plugged into, remove the system drive and replace it with the drive to be recovered as well as the new drive.  This also means I am going to have to know whether the offending drive should be mounted or not (in my reading its sometimes yes and sometimes no)

I would also appreciate any other recovery programs that I might use if testdisk fails. 

Thanks again!

---

### Post by jgw on 2017-03-14
I am currently running the rescue cd.  I tried the testdisk program and got stuck on what kind/type of partition.  The partition on the drive is GPT and the list in testdisk seems to be everything but that and tells me that the type is unknown which, I guess, means that it can't do anything.  The file system is ext4 .  I think the problem is the file system ext4.  Here an exerpt from the testdisk documentation:
ext2 is a Linux filesystem. It has been superceeded by ext3 and ext4, so it&#8217;s not found often now. with ext3 and ext4,
it&#8217;s possible to find the names of the deleted files but the location of the deleted data isn&#8217;t available anymore, so even
if ext3/ext4 is similar to ext2, it&#8217;s not possible to recover lost files using TestDisk.

 After I choose advanced the partition (there is only 1) is highlighted but my option is to create an image - not recover anything.  I fear that if I do that it will create an image over the problem drive which would delete all the deleted files.  

gparted, however, has "attempt to rescue data" and I wonder if that would work.

---

### Post by Bucky Ball on 2017-03-14
Might, might not. Have you also tried Photorec (on same SystemRescueCD) to recover individual files to see if that identifies things? Testdisk and Photorec are not the same program, as you have probably figured out.

---

### Post by jgw on 2017-03-15
Thanks for the reply!

I think the quote from the testdisk site applied to both of them.  I could have made a run at it anyway but I found a program called ext4magic that may do the job for me.  In any case I am currently copying the drive to another so I don't screw it up and then I will have at it.  I have also installed testdisk in the computer so I can get to Photorec

---

