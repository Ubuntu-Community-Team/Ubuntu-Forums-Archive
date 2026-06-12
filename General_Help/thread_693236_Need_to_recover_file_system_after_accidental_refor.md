---
title: "Need to recover file system after accidental reformat."
date: 2008-02-10
forum: General Help
---

### Post by Athanasius on 2008-02-10
I totally messed up!  I was installing windows 2000 on my windows partition but instead of just reformatting the windows partition it reformatted my whole hard drive :shock: :mad: ](*,):

I have been frantically searching about for a recovery solution that doesn't involve thousands of dollars... or for that matter any dollars.  I ran something from the live disk called "testdisk" and it found  some ext3 file systems but I was not able to get any further.  

Can someone please help me? :cry:

---

### Post by will103 on 2008-02-11
Hi,

I feel your pain, as I've just done something similar. There is a free live CD called "Recovery is possible" (seach Google and you will find it). This will not reconstruct the drive but it will find files and recover them. Unfortunately all of your file names and folder structure will still be lost. However it does work as a last resort. The application that you are looking for (on the live cd) is "photorec". You would need to have another drive to copy the recovered files onto. Does anyone else know of a better solution - I sure need one.

All my best

Will103

---

### Post by Athanasius on 2008-02-11
Thank you for your suggestion. 

 I was able to rescue the partitions with "testdisk" using the Ubuntu LiveCD (available in the universe repository)  and a reinstall with the partitioning set to "manual".  I simply marked the root partition for format and flagged my /home directory.  Once installed everything rebooted wonderfully so that I could back up everything.   

I hope this will be able to help others who were in my spot.

\\:D/

---

### Post by will103 on 2008-03-28
For anyone reading this, and in a similar situation, the app mentioned by Athanasius has helped me out twice now in the space of two months (first because of a stupid formating error and second because of a corrupted MBR). Everyone should have a copy of this hanging around in case of similar problems. 

Happy to give advice to anyone in this situation.

will103

---

### Post by Tews on 2008-03-28
There is a program called Quick-Start that was developed just for a situation like this.  Im a "tweak junky" and have lost count of how many times my "tweaking" actually hurt/hosed my system. With Quick-Start and the use of a live CD I was able to restore my system perfectly to my backed up state.  This is the closest thing to a restore point function that I have come across yet. I can recover all my apps/documents etc now in about 35 minutes.  Get it here .
.  
[http://ubuntuforums.org/showthread.php?t=613462]("http://ubuntuforums.org/showthread.php?t=613462")

---

### Post by Herman on 2008-03-28
+1 for TestDisk ( I haven't tried Quickstart out yet).

I like TestDisk so much I made a web page illustrating its use, to try to help those who have never needed to use anything like this before see what they might need to do. [TestDisk Page]("http://www.users.bigpond.net.au/hermanzone/p21.html")
If a user has time and happens to have an old hard disk kicking around, it's a good idea to play with TestDisk a little when you don't really need it and are in an unstressed mood, so you'll know what to do in an emergency. You don't need to practice it like a fire drill, but at least if you can be a little familiar with it you'll make things a lot easier for yourself if the worst ever does happen.

Photorec is great too, and can be used even in situations where the start sectors of partitions have already been overwritten so TestDisk can't do the job for you. Someone can still get most of their files back with Photorec.

TestDisk and Photorec now have excellent illustrated step by steps and other documentation of their own, [TestDisk Step by Step]("http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step"), and [PhotoRec Step By Step]("http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step"). Those should be a great help to anyone who is new to these great programs.

Regards, Herman :)

---

