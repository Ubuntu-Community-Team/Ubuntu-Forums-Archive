---
title: "Can i resize my partition without loosing data?"
date: 2005-05-25
forum: General Help
---

### Post by byen on 2005-05-25
Hey guys,
First of all thank you everyone for helping me out in the last month... In the last 30 days I switched from 100 % windoze to 100% Ubuntu and its only fair that I credit you guys for helping me see the light!!!
 
That being said... I have a Question. When i reformatted my HDD I broke it down into 3 parts... C(15GB Ntfs), D(10gbfat32) and E(5gb linux ext3) and since i was a complete noob I thought id use the 5gb to check out distros... and after i hit ubuntu..I never turned back. Now the Question is is there anyway I can add some extra space to my Linux partition without having to format and reinstall the whole thing? It took me a lott time and effort to get my Ubuntu to where it is now and I just dont wanna go  through all that again... Please suggest!
PS- I know some might say I can mount my fat32 and use it too... which i am doing right now..but id rather have a fair chunk added to linux drive.

thanks guys! GO UBUNTU!

---

### Post by dataw0lf on 2005-05-25
qtparted is the gui de facto standard for this sorta thing.  I suggest you install it and look through it's featureset, and if you have any questions afterward, let us know.
Good luck!

---

### Post by dmccarney on 2005-05-25
I have a little bit of experiance with qtparted but unfortunately I wasn't that impressed but it was probably just because of my situation before trying to repartition. 

I had a 40 gig hard-drive all formatted in NTFS with Windows XP installed, and it had been installed for about a year and in heavy use, I defragmented the drive and booted a semi-old copy of Knoppix I had laying around to use qtparted. It all booted and ran great and it spotted my NTFS drive but the problem was that the majority of my data was at the start of the partition but a small little chunk was very close to the end. 

Qtparted would not let me resize the drive to anything bigger than the little chunk of free space left after the lonely chunk of NTFS. This of course was unacceptable because it ended up being like 2 gigs :(. I tried defragging my drive a few more times but to no avail. 

Needless to say I ended up just backing stuff up to an external drive, formatting the NTFS and reformatting 20 gigs NTFS 20 gigs for Ubuntu. I installed Ubuntu and loved it so much I've yet to actually get around to installing XP again.

Perhaps there was a more elegant solution to my problem, I couldn't find one, but then again, I wasn't smart enough to ask here.  ;-)

---

### Post by gratefulfrog on 2005-05-25
[QUOTE=byen]Hey guys,
First of all thank you everyone for helping me out in the last month... In the last 30 days I switched from 100 % windoze to 100% Ubuntu and its only fair that I credit you guys for helping me see the light!!!
 
That being said... I have a Question. When i reformatted my HDD I broke it down into 3 parts... C(15GB Ntfs), D(10gbfat32) and E(5gb linux ext3) and since i was a complete noob I thought id use the 5gb to check out distros... and after i hit ubuntu..I never turned back. Now the Question is is there anyway I can add some extra space to my Linux partition without having to format and reinstall the whole thing? It took me a lott time and effort to get my Ubuntu to where it is now and I just dont wanna go  through all that again... Please suggest!
PS- I know some might say I can mount my fat32 and use it too... which i am doing right now..but id rather have a fair chunk added to linux drive.

thanks guys! GO UBUNTU![/QUOTE]
 Resizing is not the best choice, in my opinion.  It would be safer to simply configure the file system on your "free" paritition as ext3, then mount it under / or /home or elsewhere. Of course, you could cut up your free partition and keep some FAT32, or whatever. But the key is to not touch your working Linux partitions. The chances are very high that if you do, you'll have to start over from scratch. Others may say that they have managed to resize ok, but you certainly can't be sure that it will work!

Good Luck.

---

