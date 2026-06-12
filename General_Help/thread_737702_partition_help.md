---
title: "partition help"
date: 2008-03-27
forum: General Help
---

### Post by flugo on 2008-03-27
I am in no way as experienced with computers as most on this forum and am a total noob when it comes to linux. That being said:
                                  I have recently set up a dual boot of win xp and ubuntu from the live cd  on a 200 gig hd. All is going well, i even changed the boot order so xp boots first ( a request  from my family). So I have been fairly pleased with myself having accomplished all this with out totally screwing up my computer. My problem is that the first attempt at installing ubuntu did not work; it looked like it was booting in ubuntu - orange screen,ubuntu logo and progress bar- but then the screen would just go black and i would get nothing. long story short i deleted ( i thought) that partition and created another for a new install, which worked. but now i have , i believe , 3 partitions: 1-xp, 2-ubuntu, 3- the one i thought i deleted but is still there.
                                    That partition is 23.7 gb in size and i would like to free that up for the xp partition because i only have 4gb of free space left there.  Not surprisingly im sure, i have no idea how to accomplish this and i really don't want to mess up anything i've done so far because like i said,  both OS's are booting and running just fine. I would just like to reallocate the disk space back to xp. 
                                     Thanks in advance for any instruction on how to do this  and again , sorry for the noobness of it all .:lolflag:

---

### Post by forrestcupp on 2008-03-27
Try out the [GParted Live CD](http://gparted-livecd.tuxfamily.org/).  It's a great free partitioner, and it is made to move partitions around and resize them.  You'll be able to delete that partition, move it where it needs to go, and resize your XP partition to use that space. 

Warning: if you have to *move* partitions, it may take several hours.

---

### Post by Rocket2DMn on 2008-03-27
First, always backup your data before fiddling with partitions.
Now, you can boot either from the LiveCD or the GParted LiveCD - [http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/) .  If you use your normal LiveCD, go to System->Administration->Partition Editor to get to GParted.  From here you can delete your old partition, then grow your new linux partition to use that space.  Make sure you know which partition you are doing this with, though, otherwise you might delete your good partition.
As far as that black screen goes, it was because of video drivers, here is how to fix that if it comes up again - [http://ubuntuforums.org/showthread.php?t=690760](http://ubuntuforums.org/showthread.php?t=690760)

---

### Post by flugo on 2008-03-27
Thanks for the replies. I just downloaded the gparted iso and will burn it shortly. BTW I am really liking ubuntu and everyone on the forums. Thanks again for the links and I'll let you know how it turns out.

---

