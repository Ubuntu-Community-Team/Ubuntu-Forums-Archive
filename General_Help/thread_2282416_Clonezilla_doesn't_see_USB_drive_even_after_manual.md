---
title: "Clonezilla doesn't see USB drive even after manually displaying, mounting manually"
date: 2015-06-14
forum: General Help
---

### Post by dora5 on 2015-06-14
I'm trying to create an image of my  Kubuntu installation, using Clonezilla on a flash drive, and a Seagate  expansion drive.   I can't get Clonezilla to see the expansion drive.  Or, rather, Clonezilla clearly DOES see the expansion drive, and I am  able to manually mount the correct partition as /home/partimag, but then  when I run clonezilla and get to the part where it rounds up the drive  and makes you choose, as if you didn't already have it mounted, the  correct partition to mount as /home/partimag, it STILL doesn't find it. 


 The drive contains a partition formatted as NTFS with a Windows 7  image created with the same Clonezilla USB drive on it.   It DID contain  a second partition formatted on my Windows 7 comptuer as exfat.  I  tried formatting it as fat32 and as ext4 (shows as Linux when I run  fdisk -l), and it made no difference.  I used Gparted in Kubuntu to set  up and format the partitions. 


 When I get to the part where you choose the drive to mount as  /home/partimag, connect the USB drive and wait, no longer how long I  wait (I tried half making my bed and coming back), when I do the next  step and it rounds up the available drives and partitions, it does not  find the USB drive nor any partition on the USB drive.


 I tried booting into terminal mode, running fdisk -l to identify the  device name of the correct partition, and mounting it manually, using:   mount -t auto /dev/sdd2 /home/partimag  

It appears to mount, though I don't know of a way to confirm that in  Clonezilla Live.   Then I ran clonezilla by typing clonezilla, and it  ran as before, gathered the drives again, and failed to find the  external hard drive nor any of the partitions on it.  It finds only the  partitions I want to back up.   I tried this twice.  

Actually on trying yet again says it umounts the existing /home/partimag and preparing the mount point /home/partimag. .... !!!!!!???? what the ..... !!!!!!!!!!!


 Mind, in Clonezilla live, at the terminal screen, it correctly shows  all five partitions on that expansion drive with their correct size, eg  205.1 G, and "Linux" for the type.   In Kubuntu I am able to mount the  partitions and then look at them. 


 I've never had a SINGLE problem using Clonezilla before.  I WAS singing its praises. 


 What do I have to do to fix this?

Don't even THINK about telling me, aw, honey, you don't have to back up your Ubuntu installation.   (Someone actually said that on the Ubuntu chat.)


 Thank you!


 Yours,
Dora Smith

---

### Post by sudodus on 2015-06-14
You know Clonezilla - it has worked for you before. It should work now, unless you have updated it to a new version, which has problems for some reason (that we don't know yet). If you recently upgraded to a new version of Clonezilla, please try the old version again.

Or maybe the installed system in the flash drive is damaged - you could try to flash it again from the iso file, or use another pendrive.

Or maybe you are not using exactly the old well-known sequence of steps in Clonezilla. I have used it for years, and I still prefer the beginner mode, because it is easier that way to avoid mistakes. Remember that Clonezilla will first select the target, and then select the source of the cloning/imaging process. So the target should not be available, when you select the source (what to clone).

Good luck trying again :-)

---

### Post by VMC on 2015-06-14
What's the output of this: ```
sudo fdisk -l
```

---

### Post by dora5 on 2015-06-14
I have some additions to above.  

I have done extensive troubleshooting. 

I already created a backup of my Windows system on the same usb drive.   

I reformatted partitions as ext4 and fat32, and originally the two partitions were ntfs and exfat, and Clonezilla still doesn't auto reload it.

I removed all of the partitions and formatted as ext4 and created a new partition table, and Clonezilla still doesn't auto reload it.

Since I was able to create a backup image in Windows the drive is not defective.

I tried with an IDE enclosure USB drive that is too small for hte backup, on the same Ubuntu system, and Clonezilla DID auto load the partition; it was available to choose to mount as /home/partimag.   Therefore, NOTHING ails the install or the flash drive it is on.   In fact, I have successfully used this Clonezilla install on this flash drive to successfully backup Ubuntu systems and to backup and reinstall a Windows system.   

I don't know which part the asker above missed, but I stated above that when I run fdisk -l it sees all existing partitions on the USB drive, and THEN, it allows me to successfully mount the partition I want to store the backup on, as /home/partimag .    Then, when I run Clonezilla, it UMOUNTS the /home/partimag, and then it fails to find and mount the partition.  Consistently.  I have now tried ten times ten different ways.  

Only thing I have not discovered is how to format a drive as exfat on a ubuntu system.   This seems to be the preferred format.   But when it WAS exfat it still didn't work.

I also tried renaming every volume and the drive itself as Seagate or Seagate followed by a number, but then I realised that Seagate Expansion+ is the model name, not an illegal Windows volume name.

I am using all defaults, so it is "beginner mode", except that I chose backup individual partitions rather than the whole drive.   I followed the same procedure I have always followed before, including when I successfully backed up the Windows system on this drive.

---

### Post by dora5 on 2015-06-14
I used the version of Clonezilla that was current when I installed it, more than six months ago.  what is the last known version that works, and how do I specifically find it?

---

### Post by dora5 on 2015-06-14
It has occurred to me that there is evidently a way to run Clonezilla completely manually, atleast from around teh point where it is failing to remount the usb drive.  The specific problem that I am running into is that Clonezilla can find the partition I want to mount as /home/partimag just fine, and mounts it, but then I run clonezilla, and it runs, and it umounts the /home/partimag partition and then fails to find the image it has no trouble finding outside of the utility.   Doing the whole thing manually could reasonably be expected to get around this.

Does anyone here have the skill level to tell me the exact commands to use to do it manually?  It's not something I'd necessarily expect of anyone who doesn't work at Sourceforge.   

I am able to identify the device names Clonezilla is assigning each drive, using fdisk -l.   I want to specifically back up three partitions on one drive, to a partition on my usb drive, specifically using what are normally the default options, except that I want to back up individual partitions and not the drive as a whole, and then I want to check the partitions to make sure they can be restored (which is probably the default).

---

### Post by sudodus on 2015-06-14
I would try another (maybe older) version of Clonezilla. Since I don't connect to the internet, I do not worry using old versions, as long as they work. But maybe your target drive is too new for something in Clonezilla to manage it properly, and that would indicate, that you should use a newer (maybe the newest possible) version. Try and see what happens :-)

Actually I'm still using the stable version 2.0.1-15-i686-pae (built on debian). You find the stable versions to download at

[http://sourceforge.net/projects/clonezilla/files/clonezilla_live_stable/](http://sourceforge.net/projects/clonezilla/files/clonezilla_live_stable/)

and you find the alternative versions (built on Ubuntu) at

[http://sourceforge.net/projects/clonezilla/files/clonezilla_live_alternative/](http://sourceforge.net/projects/clonezilla/files/clonezilla_live_alternative/)

---

### Post by dora5 on 2015-06-14
Sudodus' suggestion occurred to me.   The external USB hard drive has only a USB3 connector.   Should be backwards compatible with USB 2, and work with its technolgoy - but who knows.

Another thing that occurs to me is that my partition editors as well as Disks are telling me that the name of the external drive is Seagate Expansion+.   Right there may be the reason why Clonezilla isn't seeing it properly; that does work in Windows but it isn't a legal linux name.   At one point I got the idea that that was just the model name, but KDE Partition manager is telling me it's the disk's name.  But I am unable to learn how to rename it.   I can mostly find instructions how to rename the individual devices, and while I did change the names that didn't fix the issue.   How do I change the name of the drive?   

I have been to both the places you pointed me to, and can only find the current version which is something like 2.10.   How do I specifically find older editions - not that that is specifically going to fix either an illegal disk name or new technology.   

Also, Clonezilla isn't having any trouble finding any of my internal drives or partitions.  Do I correctly get the idea that I can both back up to, and restore from, an internal hard drive?    Because I'm in the process of trying but wouldn't know if it is going to work until I would try it.

Alternative seems to be to go out and spend about $70 on an enclosure and hard drive, which I've proven Clonezilla can see, or wait until I see what SourceForge has to say.  I posted there, but of course when I have time to work on my computer they aren't open.   Ubuntu is too destructible to not have it easy to restore.

---

### Post by sudodus on 2015-06-14
> **dora5 said:**
> Sudodus' suggestion occurred to me.   The external USB hard drive has only a USB3 connector.   Should be backwards compatible with USB 2, and work with its technolgoy - but who knows.

Yes who knows - some USB 3 drive are not following the specifications of the USB standard. There are problems with some drives. Actually I have seen several cases, where linux has problems to recognize and connect to USB drives. Probably some manufacturers are satisfied when the drive works with Windows and Mac - they don't bother to check if the drive conforms to the standard specifications, (and don't bother to check with linux). Other manufacturers make drives that work well with linux.
> 
Another thing that occurs to me is that my partition editors as well as Disks are telling me that the name of the external drive is Seagate Expansion+.   Right there may be the reason why Clonezilla isn't seeing it properly; that does work in Windows but it isn't a legal linux name.   At one point I got the idea that that was just the model name, but KDE Partition manager is telling me it's the disk's name.  But I am unable to learn how to rename it.   I can mostly find instructions how to rename the individual devices, and while I did change the names that didn't fix the issue.   How do I change the name of the drive?   

I don't know how to do that, but I don't think that is the problem.
> 
I have been to both the places you pointed me to, and can only find the current version which is something like 2.10.   How do I specifically find older editions - not that that is specifically going to fix either an illegal disk name or new technology.   

I found easily 8 stable versions, and in a subdirectory (click on Oldfiles) I found several more versions, for example 'my' old version.
> 
Also, Clonezilla isn't having any trouble finding any of my internal drives or partitions.  Do I correctly get the idea that I can both back up to, and restore from, an internal hard drive?    Because I'm in the process of trying but wouldn't know if it is going to work until I would try it.

Alternative seems to be to go out and spend about $70 on [COLOR=#0000cd]an enclosure and hard drive[/COLOR], which I've proven Clonezilla can see, or wait until I see what SourceForge has to say.  I posted there, but of course when I have time to work on my computer they aren't open.   Ubuntu is too destructible to not have it easy to restore.

A USB3 and eSATA enclosure and a 'naked' HDD is a very good alternative. That is what I use - I connect to some computers with USB (2 or 3) and to some computers with eSATA.

-o-

By the way, please refrain from negative comments - we are volunteers, and negative comments make us reluctant to help.

---

### Post by dora5 on 2015-06-14
I solved the problem.   It looks like i tmay after all have been the nonconforming disk name.

[COLOR=#000000][FONT=Tahoma]I plugged the usb drive back into my Windows computer.  Then I was able to find how to rename the disk.  [/FONT][/COLOR]

[COLOR=#000000][FONT=Tahoma]That procedure is here.  [http://www.computerhope.com/issues/ch000532.htm](http://www.computerhope.com/issues/ch000532.htm)[/FONT][/COLOR]

[COLOR=#000000][FONT=Tahoma]I also reformatted the disk, to a single partition with exfat.   [/FONT][/COLOR]

[COLOR=#000000][FONT=Tahoma]Now, this could conceivably be complex.  I booted up Clonezilla, put in the drive.[/FONT][/COLOR]

[COLOR=#000000][FONT=Tahoma]I realiezd that I misunderstood at which point one is supposed to manually mount the drive.  The only instructions I found online make it look like you do that at the beginning, but when it asks you how to specify where to save the image to you're supposed ot pick do it manually at that point.  Then you do fdisk -l, identify the correct device, and mount it to /home/partimag .    Then you enter clonezilla, and go through the steps again, but when it gets to where it asks you how you want to pick where to save the image to, to mount to /home/partimag, you choose, skip, use what is currently mounted at /home/partimag.   Not the most intuitive thing in the world to figure out.   [/FONT][/COLOR]

[COLOR=#000000][FONT=Tahoma]So I did all of that, and THEN realized that I'd specified to work with whole drives instead of partitions, by mistake, so I restarted it.   But this time I told it to just look in local drives and tell me what is there - and it found the usb drive.[/FONT][/COLOR]

[COLOR=#000000][FONT=Tahoma]It isn't clear what I actually changed the name to; I changed it to Seagate, and Clonezilla is telling me it's name is Extended+, but perhaps the most important thing is that the space between the words is gone.   [/FONT][/COLOR]

[COLOR=#000000][FONT=Tahoma]So now it's running.   [/FONT][/COLOR]

[COLOR=#000000][FONT=Tahoma]You might want to put clearer instructions on how to manually mount cloneilla image home.  It was in some thread on this web site that I found what I have been trying to use. [/FONT][/COLOR]

[COLOR=#000000][FONT=Tahoma]If there is a procedure to change the volume/ disk name in Ubuntu it would be real helpful to put that as well, because, hey, you really don't know what antic some manufacturer in China, or even Texas, is going to do.   
[/FONT][/COLOR]

---

### Post by VMC on 2015-06-14
> **dora5 said:**
> It has occurred to me that there is evidently a way to run Clonezilla completely manually, atleast from around teh point where it is failing to remount the usb drive.  The specific problem that I am running into is that Clonezilla can find the partition I want to mount as /home/partimag just fine, and mounts it, but then I run clonezilla, and it runs, and it umounts the /home/partimag partition and then fails to find the image it has no trouble finding outside of the utility.   Doing the whole thing manually could reasonably be expected to get around this.

Does anyone here have the skill level to tell me the exact commands to use to do it manually?  It's not something I'd necessarily expect of anyone who doesn't work at Sourceforge.   

I am able to identify the device names Clonezilla is assigning each drive, using fdisk -l.   I want to specifically back up three partitions on one drive, to a partition on my usb drive, specifically using what are normally the default options, except that I want to back up individual partitions and not the drive as a whole, and then I want to check the partitions to make sure they can be restored (which is probably the default).

The output of "**sudo fdisk -l**" would give us a picture of what we're dealing with. Don't just tell us everything is fine, let us have a peek.

Also, what do you mean by 'manually'; mount the partitions, or run the clone?

If your referring to partclone, here is what CZ uses:
CLONE
```
sudo partclone.ext4 -z 10485760 -N -c -s /dev/sda6 -o - |pigz -c --fast -b 1024 -p 16 > /[some local partition]/ubuntu.gz ; cat /[some local partition]/ubuntu.gz|pigz -d -c|sudo partclone.chkimg -N -s -
``` (The above assumes SDA partition #6, and compresses to file named ubuntu. also 'some local partition' is where you want your image to be stored)

RESTORE
```
zcat /media/vmc/EXT4/ubuntu.gz|sudo partclone.ext4 -N -r -o /dev/sda6
```

As far as old, new. I have never had issue with any Clonezilla. Using both on usb flash drives and/or loop-back method. Right now I'm using the latest:
**clonezilla-live-20150608-vivid-amd64.iso**

---

### Post by sudodus on 2015-06-15
Congratulations, you found a solution :KS

And thanks for sharing it. Finally, please click on **Thread Tools** at the top of the page and mark this thread as SOLVED!

---

