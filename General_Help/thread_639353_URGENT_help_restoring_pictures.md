---
title: "URGENT help restoring pictures"
date: 2007-12-13
forum: General Help
---

### Post by kenan6346 on 2007-12-13
I've screwed up big time here. I've accidently installed ubuntu over my windows instead of on another hard drive, and now windows is gone along with all my stuff. I only care about the pictures though, is there any way to get them back?

My set up was weird. I had a 40 gig HDD plus an 80 gig hard drive that was 'split' in half; when I went into My Computer, it had 3 40 gig hard drives showing instead of 1 80 gig HDD and 1 40 gig HDD. My pictures were on one of the 40 gig drives that made up the 80 gig hard drive, specifically the drive that didn't have windows installed on it. 

In the ubuntu installation, I said 'use entire drive'.

PLEASE help me, I will be forever in debt.

Just tell me if i need to post any more specs.

Ed: problem solved

---

### Post by mozetti on 2007-12-13
If I read your post correctly, you installed Ubuntu onto the 80GB hard drive that had your pictures on it? So, there was a 40GB NTFS or FAT32 partition with your pictures on the 80GB hard drive, and another 40GB partition on the 80GB drive that you were going to use for installing Ubuntu? But, when you installed Ubuntu, you told it to use the whole 80GB hard drive, and not the 2nd 40GB partition that you had planned to use?

If all of the above is correct, then the installer would have formatted the whole 80GB drive as ext3 (by default) and installed Ubuntu onto that 80GB drive. In this case, I think your chances of recovering the pictures is very slim. You can try some recovery tools to see if it can reconstruct the files after a format, but I'm not too sure it will be possible.

---

### Post by kenan6346 on 2007-12-13
I found a program called PhotoRec, I don't know how to run it though; its make for linux, its an executable file (not a .exe but something) and when I double click it it doesn't run. I found the article about it [here](http://www.linux.com/feature/56588) and the link to the site is there.

---

### Post by strabes on 2007-12-13
Just a piece of practical advice, since it's unlikely that you'll be able to get all your data back: Get an external (or internal I guess) hard drive and make daily/weekly backups of all of your data. Problems like these would be eliminated.

---

### Post by tombott on 2007-12-13
I have never done data recovery in Linux before but have used a number of Windows apps that have worked very well.
One thing to remember though is the more you write data to the drive that contained your lost data the less chance you have of recovering that data.
If you have access to a Windows PC i can suggest software that you can try to use for recovery purposes.

Tom.

---

### Post by digitalbenji on 2007-12-13
The big issue I see is that you are trying to recover data across filesystem types.  Typical file recovery software recovers NTFS to NTFS or FAT to FAT.  File recovery in linux is a little different.  However, what you are talking about is extremely advanced file recovery, because you will need to be looking for NTFS or FAT structures in what is now ext3 space.  Frankly, I don't think this is something most linux experts could do.  I supposed you would begin by dd'ing off an image of the entire drive onto an external device, and then slicing that up into components, and wokring with each one independanty.  Even then, you would still have to have a way of identifying the image signatures.  I just don't think this is going to happen.  Plus, you would need at least another 100gigs, so that you can copy the 80 gig image with dd and then have some space to work.

Sorry.  My roommate did something similar using an FAT external USB drive, and then filled the drive with data.  All  I could recover were the filenames, the content was long gone and overwritten.

---

### Post by daengbo on 2007-12-13
Immediately remove the drive, take it to a data recovery specialist, and explain what happened. Do NOT boot into that drive or use it for anything.

Good luck.

---

### Post by digitalbenji on 2007-12-13
Do you really think a data recovery specialist will be able to handle that?  I'm not trying to be sarcastic or negatve, just serious.  This is a doosy of an issue.  I don't think you are going to find the knowhow and skills necessary to do this in the public sector, to say the least.  My experience with people who claim to do "data recovery" is that they run a GUI tool on NTFS and FAT drives only.  Most of them don't even know how to move the platters from one case to another.

Perhaps you could try doing an NTFS quick format on the drive, as I don't think this really removes much data, and then use a FAT/NTFS tool.  Of course, that's a dangerous move, since you would be formatting it again.  If you do this, I recommend dd'ing an image of the entire drive now as is.

---

### Post by kenan6346 on 2007-12-13
Thanks for all your help people, it means a lot.

@strabes: good idea, will do ASAP.

@tombott: I've actually got 2 real HDD's in the computer, one with linux one without. If I install windows 98 or ME (I've got no more XP installs left) on the one without linux, will I be able to do data recovery from the linux drive?

@digitalbenji: if I try the above senario will it work? I ask because it will be trying to recover NTFS/FAT from an HDD that has been written over by ext3.


@digitalbenji &daengbo: is it worth taking it to a computer repair shop or something of the like? Most of them only really deal with windows I believe. And that DD'ing the drive.....I don't know what that is or how to do it. Can you explain.

Finally, does anyone know how to open the file I explain in my previous post.

Cheers.

---

### Post by daengbo on 2007-12-14
Regarding dd,
Boot into a live CD. unmount the hard disks.
You'll need an external drive large enough to hold 40GBs, and to figure out where the partitions are mounted. Open 
System -> Preferences -> Hardware information
and find your drive and the partition you want want to save. It's probably under an IDE or SATA controller. Click on the Advanced tab and look next to "block.device" to see the device it's mapped to. For the purposes of this discussion, I'll pretend it's /dev/sda3. It probably isn't, though, so DON'T COPY AND PASTE from here.
Next, find the external drive and mount location of the partition you want to make the backup to. You can do this through Nautilus. We'll assume this is /media/USBDISK. Again, it probably isn't, so DON'T COPY AND PASTE the command below.

Next, open a terminal and type the following:
sudo dd if=/dev/sda3 of=/media/USBDISK/partition.img
## if means the input file. You are using the device as the input file. This works because in Unix, everything is a file.
## of means the output file. This will be a normal image file (similar to an .iso) on the external drive's partition.
You'll probably need the sudo for direct access to the /dev location, but that may have changed in the last few years. Input your password when requested to.

This command will make a bit-for-bit copy of your disk, but I understand there is additional data that can be recovered from the original drive because of "ghost" bits which were overwritten but still weren't fully magnetized. I'm not a professional and know little about this. You're better off having the original disk examined, but having a bit-for-bit copy can't be a bad thing.

Best of luck

---

### Post by kenan6346 on 2007-12-14
Thanks for the above post, I'll keep it in mind if this doesn't work

I found a program called "Recover My Files", I installed the trial and it is the real deal; I reinstalled windows on another HDD and it found files that I deleted ages ago on the HDD that I had since reformatted to install linux and then formatted again to install windows. I may just have a chance to get most of the files back...

---

### Post by kenan6346 on 2007-12-14
Yep, I think it's working, I'm finding a heap of photos and excel files; however a lot of the photos are considerably smaller and some excel files are just bits and pieces of what they were.

Moving on to a slightly different topic, this is showing me how difficult it really is to permanently delete files. I mean, if I had reformatted a flash drive to get rid of files I didn't want anyone to see, could someone still recover files off it?

---

### Post by mozetti on 2007-12-14
The best method of formatting to eliminate file artifacts goes beyond the simple formats available in any OS. However, there are various free Linux Live-CDs made specifically for this purpose, and they generally format the storage (whether HDD or flash) and then write all 1s or all 0s to it multiple times.

I work for a government organization and before we can dispose of hard drives we use one of these methods.

---

### Post by kenan6346 on 2007-12-15
Ah I see. I'll keep that in mind, thanks.

Recover My Files is still scanning, says its got about 30 million files to scan still....although thats probably all the files that I've ever deleted or were in my temp folders when the system was wiped

---

