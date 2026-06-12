---
title: "Image or back-up"
date: 2007-12-08
forum: General Help
---

### Post by Elena678 on 2007-12-08
Hello, I just installed my computer (for the fifth time in one year, most of the times my computer crashes why i try to install the visual effects) and now my computer is running well, so, i would like to make an immage, that i can burn on a DVD, and that i can use to reinstall my pc like it is now when it crashes again.

If that not is possible, can somebody tell me then how i need to make a good back-up that i can use when i have problems

Thanks a lot

Greetings 

Elena

---

### Post by drs305 on 2007-12-08
partimage is an excellent way to make an image of your disks.

Here is a link to a howto or just do a search with the words 'partimage', 'backup' and maybe 'livecd':
[http://ubuntuforums.org/showthread.php?t=287522](http://ubuntuforums.org/showthread.php?t=287522)

---

### Post by viking777 on 2007-12-08
Elena, disk imaging is vastly superior to ordinary backups, though unfortunately Linux does not excel in this respect. There is partimage which is  a horrible program and there is dd (a command line program) which is even worse. 

I won't make any friends by saying this but at the moment if you want a sensible imaging program you have to go for the commercial ones like Acronis True Image or Symantec Ghost. The problem there is twofold. Firstly they cost money (how much is your data worth?) and secondly they do not produce Linux versions. This is not quite such  a problem as it seems because both of these programs will run from CD so once you have the CD it doesn't matter what operating system you use because you just stick the CD in and boot from that. They are both capable of imaging and restoring Linux partitions so that is not a problem either.

So how do you get the CD? Well unfortunately you have to have access to a Windows machine on which you have to install the program that you have purchased and from that you burn a 'recovery disk' or whatever they might call it and after that your involvement with the windows world is over, you just boot from your CD and image/restore away to your hearts content.

I really wish that the Linux world would get its act together and produce something that matches these programs, but at the moment they do not seem capable of doing so.

PS I am going to get so flamed for this post!! C'est la vie.

---

### Post by drs305 on 2007-12-08
I'm not flaming, but why do you think partimage is horrible? I've used it without problems on countless occasions. Granted it takes some learning but the link provides guidance. The OP can do a lot worse than partimage and I would hate to see her discouraged from using this tool.

---

### Post by Elena678 on 2007-12-08
hej hej, i think i need to try partimage, so we will see if it is so bad, i can't use the other, because i have no windows computer, i got my ubuntu cd from a friend, and bought my laptop without windows, it was a bit cheaper :) (and i think with ubuntu it is maybe better than with windows, but that is just my opinion :) )

one question about partimage, can you save the image on the same partition, becouse i have only one partition on my computer.

Greetings...

---

### Post by niteshifter on 2007-12-08
I'm also a fan of partimage. No fancy GUI, just a console-mode (ncurses actually) interface, but it's not hard to learn how to use.

To answer your question about using on a single partition system: No. The partition has to be unmounted, which would mean that you have no system to use. However all is not lost, have a look at:

[http://www.sysresccd.org/Main_Page]("http://www.sysresccd.org/Main_Page")

Includes partimage, can run totally in memory freeing your CD/DVD recorder to burn the images made. Highly recommended.

---

### Post by drs305 on 2007-12-08
Elena,

Yes, you do need a separate place to save the image. Otherwise the image would be trying to copy itself. The partition can be on another hard drive, another partition on the same drive, or as niteshifter mentioned, onto a cd/dvd.  But this is not necessarily a bad thing. Saving a copy to the same hard drive wouldn't help if the hard drive itself failed.

So here are some options and some links.

Create one or more additional partitions on you current drive. Many users maintain a separate partition for their home drive. It makes some backups easier and allows you to have mulitple systems on your computer (say Fiesty and Gutsy) while maintaining personal configurations. Since your computer only has linux on it, there is probably ample space for an extra partition or two. You could also make a partition on which to create and store backup images (and use partimage ;-)  ).
Here is a link for making/moving a separate home directory:
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

You can also create the image on a separate hard drive (external or internal). 

In any case, once you have created an image you can copy it to a cd/dvd and restore it from there as well.

For instructions on using partimage, here are some links:
[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)
[http://www.partimage.org/Main_Page](http://www.partimage.org/Main_Page)
The  psychocat's site is very extensive and has lots of great tips for a variety of tasks. Just look in the left menu panel. The partimage website images are a bit easier to see as they are larger.

If the thought of making a new partition or adding an external or internal drive is more than you want to try, here is a link to a current thread for saving your setup without needing another partition:
[http://ubuntuforums.org/showthread.php?t=564836](http://ubuntuforums.org/showthread.php?t=564836)

If you use gparted for creating a new partition or partimage for backing up your system, there is lots of information on this forum. And if searches fail, there are plenty  of people on this forum who will be willing to help you get started.

---

### Post by viking777 on 2007-12-09
Somebody asked me back there why I don't like Partimage, and it is not the first time I have been asked that.
 
I can only assume that people that ask that question have never used a good imaging system (or they wouldn't have to ask!). Since you did ask though, I will try to explain. I use Acronis True Image. I use it because I used to be a Windows user and I bought it whilst I still was and therefore have it around. Because it runs from CD I don't have to run Windows to use it. 

Can I make clear here and now that I have no connection with the Acronis organisation and never have had in the past so this is not some kind of advertising scam it is just my genuine thoughts.

1) Interface. We are in the 21st century right? and Partimage produce an interface that requires you to use Tab keys and Space Bars to move around in it? Have they never heard of the Mouse? The interface alone is enough reason not to use it.

2)Speed. I conducted tests for myself on the speed of imaging of Acronis, Partimage and dd. I imaged the same partition using all three (default compression setting) and saved the image to the same drive on the same computer. Partimage took almost exactly twice as long as Acronis. (incidentally dd took twice as long as Acronis before it failed with the image not even completed!)

3) Image size. In the above test the Acronis image was significantly smaller than the partimage one (default compression remember).

4)Image splitting. I know there are image splitting tools on partimage (although I have never used them) but they do not work as seemlessly as those in Acronis. It just automtically splits image files according to the size of the backup media. For example I usually backup to an external hard drive (which is formatted FAT32). Many of you probably know that FAT32 file systems have an individual file size limit of 4Gb. If any of my images exceed 4Gb it automatically carries on imaging in a second file - no configuration is necessary to make this happen.

5) If you run Acronis from windows (which I admit I don't any more) it is capable of 'live imaging' in other words it will image the disk that it is running on - faultlessly. Their advertising even suggest that you can carry on working in windows whilst the image is being created. Try that with Partimage!

6) Acronis images allow the recovery of individual files and folders as well as the whole thing. Can you do that with partimage? I don't know.

7) Acronis can back up to almost any media known to man. Can Partimage? Again I don't know.

8 ) Acronis can restore to a partition of a different size with ease, so if you want to expand the size of your Linux partition you can easily. Can Partimage do this? I don't know.

9) Reliability. I have used Acronis for a long time and it has never let me down. Perhaps Partimage is equally as reliable but I go with what I trust.

Is that enough reasons for you? It is certainly enough for me. Don't get me wrong, I seriously wish there was a Linux equivalent to Acronis but there just isn't, end of story.

---

### Post by ntu on 2007-12-09
I use Clonemaxx to clone one hdd to another. It is free. You can download it from here:
[http://www.pcinspector.de/Sites/clon...htm?Language=1](http://www.pcinspector.de/Sites/clon...htm?Language=1)

---

### Post by viking777 on 2007-12-10
> **ntu said:**
> I use Clonemaxx to clone one hdd to another. It is free. You can download it from here:
[http://www.pcinspector.de/Sites/clon...htm?Language=1](http://www.pcinspector.de/Sites/clon...htm?Language=1)

"Die Seite wurde nicht gefunden"

And I didn't know you kiwis spoke German!

---

### Post by viking777 on 2007-12-10
Ah here is the site you want to try this:

[http://www.pcinspector.de/Sites/clone_maxx/download.htm?language=1#](http://www.pcinspector.de/Sites/clone_maxx/download.htm?language=1#)

Just click the download link. It comes as an iso file so you don't need windows to install it, just burn to cd and apparently it is free so not a problem there either.

Don't know how good it is though. If somebody wants to try it out let us know how you get on.

EDIT Just found the catch by looking in the faq - it only images full hard drives not individual partitions.

---

### Post by psusi on 2007-12-10
I have used Norton Ghost for mass deployment of prepared images to desktop windows machines before, it and was quite handy, but for backup purposes, I think the only reason people find disk imaging suitable is because the windows backup took sucks so much.  It can't backup files that are in use, and to restore the backup you must first reinstall windows anyhow.  

Linux doesn't have these problems, so a simple old fashioned tar backup works fine.  With imagers you have to take the system offline to backup, but tar has no problem backing up the system while it is running.  Tar can also put the backup file on the same partition it is backing up.  Restoring the system is as simple as booting from a livecd, formatting the disk, extracting the archive, and installing grub.  

I have a cron job set up on my server to do a nightly incremental backup with a weekly full backup.  It takes place automatically and sends me an email to confirm.  After it makes the backup, it even automatically copies the archive over the network to another system for safekeeping.

---

### Post by Elena678 on 2007-12-14
okej, thanks for all the info, i just downloaded the cd, i will try tomorrow to make an image on en external drive, can it be an USB drive?

greetings

---

### Post by Joshua on 2007-12-14
You could see if remastersys suits your needs.

[http://www.howtoforge.com/ubuntu-linux-mint-livecd-with-remastersys]("http://www.howtoforge.com/ubuntu-linux-mint-livecd-with-remastersys")

[http://linuxmint.com/wiki/index.php/Remastersys]("http://linuxmint.com/wiki/index.php/Remastersys")

---

