---
title: "partimage - confusing app?"
date: 2008-02-15
forum: General Help
---

### Post by msjones on 2008-02-15
Hello,

I now have my dream ubuntu box setup. All drivers and apps installed.

What I want know is to make a dvd image of my root partition so if anything goes wrong I can always restore back to this current state.

I have installed partimage. When I went to load it up I went through the on screen instructions but it says I cannot image the / partition as it is busy.... How am I able to image this without being logged it?

Is there a better option than partimage?

Thanks

---

### Post by drs305 on 2008-02-15
Are you doing the following?  
(in parentheses is an example)
Booting from rescue CD or Live CD
Creating a mount point (/mnt/t)
Mounting a partition on which you will make a backup image 
( mount /dev/hda3 /mnt/t)
Starting partimage 
Tabbing to the partition you want to copy ( sda1, hda1, etc)
Making the name for the image you wish to create start with your mount point (mnt/t/hda-backup) Your mounted partition can't be the same one you are imaging.

Added note: Before booting, make sure you know the partition which you want to save (hda1, hda2, sda1, etc) and the location of the partition on which you are going to save the image (/dev/hda2, /dev/sda2, etc).

---

### Post by msjones on 2008-02-15
Sorry dude im abit new with this whole thing.

Could you clarify the guide abit more?

Thanks

---

### Post by 50words on 2008-02-15
Just use the PING LiveCD ([http://ping.windowsdream.com/](http://ping.windowsdream.com/)).

---

### Post by drs305 on 2008-02-15
Basically, you run partimage from the command line before booting into ubuntu. You don't make a root image at the same time you are using it. So you insert a system rescue CD or get to partimage via the Live CD without running ubuntu. Root is on one partition, so you need another partition on which to copy it (it can't copy itself onto itself). The other thin that has to be accomplished before running partimage is to mount the partition on which you are going to make the copy. Until you do that, the computer doesn't know where to write the information. 
Here's a link to using partimage. It looks intimidating but the really long part (steps 1-4) are one timers and after that it is pretty short.
[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)

I know it sounds confusing but after you've done it a few times it becomes (almost) second nature. Keep asking questions if you need to. Good luck.

---

### Post by msjones on 2008-02-16
drs305, thanks for the reply.

I managed to get partimage to backup my / partition. So if anything goes wrong I can no restore my system without going through the whole process.

Just one query..... if my system does fail, how do I restore the image?

Thanks

---

### Post by drs305 on 2008-02-16
I'm glad you got partimage to work. 

If you need to restore that image, you would boot to a prompt with the LiveCD or RescueCD.
I'd highly recommend burning a system rescue CD while your system is working. In addition to partimage, it has other utilities that may come in handy. If you have a copy of the rescue cd, you would simply reboot your computer with the CD inserted. If your computer will boot from a CD it will automatically take you to a prompt. Then you would make a mount point for the partition with the backup, mount that partition and then run partimage. 
You can get it here: [http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page) 

Before running partimage, you will need to remember the name and location of your backup image and the name of the root partition. It's easiest to write them down now rather than have to dig them out of a faultly computer. So just write down, for example, root is on hda1 or whatever and the backup is located on /dev/hda3, which is the partition you would mount before starting partimage.

When you run partimage to restore a partition, the first thing it will ask for is the partition to restore. You would tab to the first name you wrote down. Then it will ask for the file to restore. You type in the name of the backup image preceded by where you mounted it ( for example, /mnt/temp/myrootbackup.000

The only real danger with restoring a partition with partimage is that you get the correct partitions entered. Make sure you are restoring a root image to the root partition, or another image to it's correct location, because you will be overwriting all the data on that partition (which is the purpose in the first place). 

If you have any other questions, we'll be here.

---

### Post by msjones on 2008-02-16
Thanks for that :) hopefully I wont have to be restoring anytime soon.

If I run into any problems down the line ill be back!

Thanks again!

---

