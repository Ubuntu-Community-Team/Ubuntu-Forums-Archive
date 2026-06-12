---
title: "When Installing I screwed up the partition"
date: 2007-07-06
forum: General Help
---

### Post by slayer04 on 2007-07-06
ok First my computer, 2.8 GHz intel. 1950 radion pro, 1.5 GB DDR2 ram, a 80GB hard drive and a 160GB hard drive.

Ok now my problem I have xp installed on my 80GB hard dive, so I bought a 160GB and wanted to install ubuntu on it  so I hooked everything up set it as the slave drive and went about installing when I got to the part about partitioning it I wanted to give ubuntu 25GB and leave the rest for xp to use because I am a heavy gamer so I need the space to put all my games. now once done installing everything checked out fine until when I rebooted and went into xp I saw that the partition some how got switched xp got 25GB and ubuntu has 117 and somehow  there was a third partition containing 5GB I tried using the partition editor that ubuntu has but I can only edit the 25GB partion not any of the others which does me no good so I need alot of help!
This is how the partition ended out as-
-> section 1 is / 25Gb (what xp is reading) / section 2 is / 117GB of free space xp does not see this / section 3 is / 4.5GB and this is where Ubuntu was installed /

p.s. I have almost no knowledge about how ubuntu works so I see I dove head in without doing my homework so now I am lost and clueless on what to do](*,)

---

### Post by loserboy on 2007-07-06
I'm not really sure if I understand, but if you need to repartition stuff, boot to the Livecd and use gparted from there because you don't want to edit partitions when drives are mounted (lthough i don't think it will allow you to)

I think to run gparted in the livecd just go to a terminal and type
> 
sudo gparted

---

### Post by slayer04 on 2007-07-06
I did boot from the live cd and like I said I could only edit the 25GB so it didn't help what I am trying to find out is if I can merge the partions into one big one like it was before installing ubuntu or if I can make xp read the 117GB partition and Ubuntu on the 25GB partition

---

### Post by avik on 2007-07-06
Using GParted, what you can do is resize the partitions so the Ubuntu partition is 25GB and the Windows partition is 117GB.

---

### Post by slayer04 on 2007-07-06
ok I will say it again the 25GB partition is resize able but the rest are not for some reason so it isno good because the is no way to increase the size of it without making the rest small which I can't do because the partition editor won't let me change them ONLY THE 25GB one can I re size or delete but if I delete it I still can't make the other one larger I CAN ONLY CHANGE THE 25GB partition

---

### Post by loserboy on 2007-07-06
when you say you can't change the others, do you mean that the edit button is greyed out, or there is no button, or you finger is broke so you can't push it.... that's what we are trying to figure out

---

### Post by slayer04 on 2007-07-06
> **loserboy said:**
> when you say you can't change the others, do you mean that the edit button is greyed out, or there is no button, or you finger is broke so you can't push it.... that's what we are trying to figure out

it is grayed out

---

### Post by smiley2billion on 2007-07-06
What I would recommend is just to start over.  Make sure to backup anything you need from either the Ubuntu install or the WinXP install.

After that, take your Windows disc and boot off of it again and when it prompts, delete all the existing partitions and create what you need for the Windows partition (117GB in your case)  and install it to there.  After Windows has finished take your Ubuntu disc and go through the install process again and take the remaining space and install Ubuntu to it (Use largest continuous free space).

It sounds like extra hassle, but I've tried the whole resize this partition and change that partition and I always end up doing a clean install to get the results I want.

Just remember, install Windows first, then Ubuntu and dual booting shouldn't be a problem.

---

### Post by loserboy on 2007-07-06
you could start over like smiley said and that may be the easiest way, but the reason the buttons are greyed out is because the drives are mounted, I forget the command but isnt it something like "umount -a" ?

```
sudo umount -a
```

---

### Post by slayer04 on 2007-07-06
> **smiley2billion said:**
> What I would recommend is just to start over.  Make sure to backup anything you need from either the Ubuntu install or the WinXP install.

It sounds like extra hassle, but I've tried the whole resize this partition and change that partition and I always end up doing a clean install to get the results I want.

Just remember, install Windows first, then Ubuntu and dual booting shouldn't be a problem.

I have xp on a different hard drive so reinstalling that would be pointless  but being able to start over with the hard dive that is partitioned inncorrectly would be of help but for some reason I can't/don't know to  format it I tryied to format it in xp but I  couln't plus I could only get it to format the 25GB section it reads which doesn't help lastly since I just started using Ubuntu I feel lost when doing things and have no clue how to format with it.

..this reminds me of another question I forgot to ask: would it be possible to even have xp on one hard drive and Ubuntu on the slave drive and then be able to boot off either on on my choosing.

---

### Post by slayer04 on 2007-07-06
> **loserboy said:**
> you could start over like smiley said and that may be the easiest way, but the reason the buttons are greyed out is because the drives are mounted, I forget the command but isnt it something like "umount -a" ?

```
sudo umount -a
```

ok I am sorry for all the posting and for the lack of my knowledge but how do I enter the command like I said I feel lost when using Ubuntu just because I have never used something like this before or linux

---

### Post by splintercellguy on 2007-07-06
In Ubuntu, go to Applications -> Accessories -> Terminal.

---

### Post by loserboy on 2007-07-07
oh yea sorry, ^ what splinter said

---

### Post by longlegs on 2007-07-07
Hi <
Do not use windows to partition drives! It throws away 5-10%. (your extra partition?)
Since you have nothing to save on the 160g drive, insert your live linux cd and delete all the partitions (ON THAT DRIVE ONLY) and reinstall linux. Be sure to use "manual" partitioning!
Note that 1g is enough for the swap partition, 2g is plenty.
Note also that if you format the 117g partition as fat32, linux can also rw to it
If you get an error 'no root drive' be sure to select '/' as mount point in the partitioner.
Have a good day!
longlegs

---

### Post by catnappist on 2007-07-07
Personally, I haven't found any partitioning stuff I can't do with gparted on a live cd, but I can't do sheesh if that live cd is Ubuntu.  Get it on the system rescue cd from 

[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

If there's stuff in the partition, it moves it around while it's working, and nothing gets grayed out.  I know your frustration well.

Good luck.

---

