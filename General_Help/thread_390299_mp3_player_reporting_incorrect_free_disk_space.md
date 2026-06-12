---
title: "mp3 player reporting incorrect free disk space"
date: 2007-03-21
forum: General Help
---

### Post by danmonkey on 2007-03-21
Hi, I hope someone can help me with this...  I bought an iAUDIO U3 a couple of weeks ago - it all works fine in that Kubuntu knows what it is when I plug it in, and I can put stuff on and take it off ok...

Except a couple of days ago it stopped letting me put more music onto it, saying that it was full - except there was about 1GB still free!  At the moment, when I right-click the device and select properties, it shows: Size 1.9 (1,993,732,751) and Free disk space: 380.2 MB out of 3.8 GB (91% used).

Now my maths might not be great, but 3.8 - 1.9 is certainly not .38!

I've emailed COWON (who make the device), who suggested it could be the recycle bin - but I've emptied that and it's still the same.

The device itself is reporting the correct amount of Free disk space, and even Windows is calculating it properly.....  So why not Kubuntu?  Any ideas would be much appreciated as I don't want to downgrade to my Windows partition every time I want to put more music on it!

---

### Post by hikaricore on 2007-03-21
Are you sure you understand how much space is actually on your device?

3.8gb is not the same as 3,800mb

[http://en.wikipedia.org/wiki/Gigabyte](http://en.wikipedia.org/wiki/Gigabyte)

I still can't get the numbers to come out correctly on your free space so it's possible you're missing something, but a better understanding of how filespace is used may help.

Also in most file systems, the files themselves take up extra space by just existing, which may or may not be shown by disk space estimates.

--

In addition your device may store it's software and any data that comes with that software in this space as well.  But I don't know your device so I can't say for sure.

---

### Post by mcduck on 2007-03-21
> **danmonkey said:**
> 
I've emailed COWON (who make the device), who suggested it could be the recycle bin - but I've emptied that and it's still the same.

Did you empty the recycle bin on the player itself? If you browse to the player there's a hidden directory called .Trash

---

### Post by danmonkey on 2007-03-22
Yes, I've emptied the .Trash folder on the device itself - and also removed this in case this was causing it confusion.

It's weird the way Kubuntu knows that it's only half full, but still thinks that there's no empty space on it - yet Windows works correctly.

(And yes, I do know that 3.8 Gig is not 3800 Meg!)

---

### Post by IanW on 2007-03-22
Doesn't Ubuntu reserve a chunk of each partition for expansion purposes?
Could that be what you're seeing?

I mean (on Ubuntu at least - not sure about Kubuntu) if you look at the File systems tab on System Monitor, it gives several columns:-

Device - Directory - Type - Total - Free - Available - Used.

Where "free" differs from "available" due to some drive space being "reserved".

---

### Post by mcduck on 2007-03-22
> **IanW said:**
> Doesn't Ubuntu reserve a chunk of each partition for expansion purposes?
Could that be what you're seeing?


Only on Linux file systems, and I don't think any MP3 player uses Ext3 ;)

---

### Post by Bakerconspiracy on 2007-03-28
I've had this problem on a variety of devices which inculdes flash drives, mp3 players and also my 500 gb ATA harddrive. I also have yet to find a solution to this problem (I have searched extensively for an answer)

---

### Post by danmonkey on 2007-04-05
I've found the solution.  Basically, what was happening was when I deleted a file it was going into the .Trash folder - from here I was just removing these from the device.  Except somehow, somewhere along the way (I'm not very techy!), ubuntu wasn't clearing this space from it's knowledge of what the device had on it.  So - solution was to fill the device up to the brim in Windows, then in Ubuntu, get rid of all the rubbish (so it goes in the device's .trash folder) and empty the deleted items bin on the desktop.  This will also empty the device's .trash and clear the empty space so it can be reused.  I hope this explains it!

---

### Post by cisforcojo on 2007-04-06
I had the same problem with my iPod.  

An alternative solution is:
Format the device in Windows THEN,

Make sure if you delete anything from it while in Ubuntu, clear the .Trash folder and be sure to 'Eject' the device (right click the icon on the desktop and click 'Eject').

Sidenote: if using an iPod, don't manage the files manually. You have to use a program such as gtkPod. There's a difference in file transfer protocols that sometimes causes problems (did for me anyway).

---

### Post by virtual_reality on 2007-04-07
I have the same problem and I didn't solved it yet :( help:( I cleared all bins

---

### Post by matja on 2007-06-16
I solved this problem by running dosfsck (fsck.vfat) on my iPod. While running this check it always reported that the free cluster summary was wrong, but I had trouble making it repair the error. The way I got it to work was to  unmount the player and run dosfsck with the "-rV" option twice, the second time it just reported no errors. I have no idea if it's necessary to unmount it or using the V option, but I ran the check several times with different options without any luck before the above setup finally worked.

Hope this helps, it should be a bit less work than the above suggestions!

---

### Post by eklektik on 2007-06-19
i confirm matja's method!

massive respect, matja! your howto did the trick for my fat32 usb disk drive... 

thnx a lot :D

---

### Post by ricardisimo on 2007-06-20
I've got an iPod Nano with the same problems... about a Gig's worth of missing space. I have no idea what matja said. Could someone either go line-by-line, or else tell me if any of the players (Amarok, Rhythmbox, etc.) can just do this job unaided? Thanks.

P.S. - I did look around the iPod via Nautilus, and found audio files from many months ago that I'd never even loaded - "Democracy Now!" programs and the like - just stuff that you don't put on a Nano ever. Bizarre. Anyway, deleting them made no difference whatsoever in the iPod's free space. Something's up.

---

### Post by ricardisimo on 2007-06-21
OK, I think I just understood what danmonkey was talking about... if you have 3Gs filled on a 4G Nano when Ubuntu gets a hold of it, it is then effectively a 3G Nano, unless you can reconfigure it somehow. I no longer run Windows, so dan's solution doesn't really help. I'm still waiting for a more detailed translation of what matja was saying.

It doesn't bode well for gtkpod that every other player (Rhythmbox, Amarok, Banshee, Exaile, etc., etc.) mounts my iPod immediately and without any help from me, but not gtkpod. No big, I suppose, but like I say, it doesn't exactly inspire confidence. Thanks in advance for any help.

---

### Post by eklektik on 2007-06-22
Hola, ricardisimo!

Here is the detailed howto to repair incorrect available file space reporting.

1.	you plug in your device
2.	u go to system monitor (system-administration-system monitor), hit the file systems tab and remember the device path (eg. /dev/sdc1 &#8211; we'll use this one in the next step as an example)
3.	u unmount your usb drive (places-computer; then move your mouse to 'places' side pane, to your usb device; right click and 'unmount')
4.	u hit terminal (applications-accessories-terminal) and type this command:
dosfsck -rV /dev/sdb1 &#8211;rV
5.	you'll get prompted with something related to backing up... &#8211; i have no idea what that is, so press 'next, or do nothing, or something similar'. I think thats number 3
6.	system will warn you that you have more clusters available &#8211; press number related to repair, or correct...
7.	repairing will take 20sec, sit back and relax cos u did a lot of work
8.	mount your drive (same way as unmounting)
9.	hit the properties... u now have 1gb space more :)! u did it, u rock :)


if u get something different or have problems, pm me.

bye

---

### Post by ricardisimo on 2007-06-24
It's a no-go. I'm getting syntax errors aplenty, (the second "-rV" in "dosfsck -rV /dev/sdb1 –rV" is not right, from what I can tell) and also nothing at all seems to happen while the iPod is not mounted, and only slightly more while mounted. Still, I think you've pointed me in the right direction, and I'm going to read any manpages I can find on dosfsck. Thanks.

P.S. - Please feel free to send any additions or corrections that will shorten my journey.

---

### Post by eklektik on 2007-06-26
hm, strange... i used this howto on my usb mass storage disk drive, not the ipod, but basically its all the same... the 'dosfsck -rV /dev/sdb1 &#8211;rV' syntax has to be right and second '-rV' must be used. try to google dosfsck or copy terminal/konsole content when ur doing this and paste it here in order for me to try to help u...

---

### Post by DapperDrakeNewbieDR on 2007-09-22
Folks,

I just found out that you should not use -rV after  "/dev/sdb1" and that the drive should be mounted in order to work.

I ran:

```
sudo dosfsck -rV /dev/sdb1
```

Then I got the following: (Note: I answered "1" for the first question and "y" for the second one)

```
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
Starting check/repair pass.
Free cluster summary wrong (13407 vs. really 196415)
1) Correct
2) Don't correct
? 1
Starting verification pass.
Perform changes ? (y/n) y
/dev/sdb1: 124 files, 795942/992357 clusters
```

Umounted the volume, mounted it back, and it worked.

Thanks

---

### Post by alienseer23 on 2007-09-22
hello!
there are several things that could be happening if you are experienceing a problem like this.
soltuion 1) reformat your device. Using a simple program like gparted will often do the trick. You can back up the info, then reformat, easy. I don't use the .trash file, instead I tell nautilus to simply delete them instead of sending them to the trash, no more problem

solution 2) you have a hacked device, or currupt partition table. Use fdisk to write a new, blank paretition table to your device, reboot it, then I use gparted to write a new partition. Works like a charm for my (from China) ipod nano clone.

here is a link for detailed instruction on how to do this, 

[http://www.mympxplayer.org/viewtopic.php?p=37713#37713](http://www.mympxplayer.org/viewtopic.php?p=37713#37713)

there should be a tuutorial here, on these forums, soon
--> here's the link   [http://ubuntuforums.org/showthread.php?t=556899](http://ubuntuforums.org/showthread.php?t=556899)

---

### Post by bl1rt on 2007-11-06
All of you who have/had that problem: did you delete files using the delete method of your player? Because this is what I suspect to be the source of the problem. For you see, deleting files on a Linux system usually overwrites the existing data completely (with zeros, I suppose), while the common practice on less secure operating systems is to just flag the data as eraseable, so that it gets overwritten when the space is needed (and only then). I suspect that the latter way is the one done by most players and that this is the reason why ubuntu doesn't recognize some empty space: because it is not empty from a Linux point of view. It would explain why that windows gets it right as you were saying. 

I would really appreciate it if you could drop a line whether you did erase data like that and if this sounds reasonable. Then this bug could be posted on Launchpad so that the error gets fixed - unless there is a better workaround. I seriously don't want to completely format my little player, because it's quite some work and - even more important - I read on another post that this might lead to having the firmware deleted and thus destroying your player if you can't get it back on.

But one more question: those of you who did the dosfsck or gparted, was the problem solved for you permanentely after one go or do you have to repeat the procedure every now and then?

---

### Post by DapperDrakeNewbieDR on 2007-11-14
> **bl1rt said:**
> All of you who have/had that problem: did you delete files using the delete method of your player? Because this is what I suspect to be the source of the problem. For you see, deleting files on a Linux system usually overwrites the existing data completely (with zeros, I suppose), while the common practice on less secure operating systems is to just flag the data as eraseable, so that it gets overwritten when the space is needed (and only then). I suspect that the latter way is the one done by most players and that this is the reason why ubuntu doesn't recognize some empty space: because it is not empty from a Linux point of view. It would explain why that windows gets it right as you were saying. 

I would really appreciate it if you could drop a line whether you did erase data like that and if this sounds reasonable. Then this bug could be posted on Launchpad so that the error gets fixed - unless there is a better workaround. I seriously don't want to completely format my little player, because it's quite some work and - even more important - I read on another post that this might lead to having the firmware deleted and thus destroying your player if you can't get it back on.

But one more question: those of you who did the dosfsck or gparted, was the problem solved for you permanentely after one go or do you have to repeat the procedure every now and then?

I didn't have to format the drive, and yes, for me it was solved permanently.

---

### Post by alienseer23 on 2007-11-14
EDIT: the solution for reformatting works primarily on devices that have been tampered with, deliberately, to show a larger amount of space than is actually there. Reformatting did not destroy the firmware. 

On my flash drives, reformatting works when there is mystery unavailable space, but there is no firmware to think of. 

On my creative nano zen, it is reluctant to partition table editing and nothing works. dosfsck does not seem to work, and worse yet, there is a different data shown in fdisk, cfdisk, qtparted, and gparted in regards to disk size, if the space is free or not, what type of file system is on the disk, and so on. The firmware is still there, but is unable to read the disk. I made the careless mistake of deleting the file with nautilus. Now I am paying for it. As soon as I did this, there were troubles.

---

### Post by smiley1962 on 2007-11-22
I see this is an old post, but there is a solution, these kind of devices can hold no more than 99 file names.
The solution is First empty the device then  put in exta folders and voila, you can fill those folders

---

### Post by dschaller on 2008-06-02
Is the original starter of this thread still around? I have the same problem with my IAUDIO U3. Ubuntu says the disk is full, but the player reports 1.1GB free on the device. Oddly, when I right-click on the disk icon to get the properties, Ubuntu correctly reports that there are 179 files totaling 879 MB, but then in the pie graph it shows all 1.9GB are full. (There are no hidden or trash folders lurking either.)

---

### Post by dschaller on 2008-06-06
After a couple reboots, it now reports the correct amount of space. I have no idea what happened.

---

