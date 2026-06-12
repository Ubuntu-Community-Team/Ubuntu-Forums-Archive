---
title: "Write to Samba NTFS share from XP workstation"
date: 2005-07-27
forum: General Help
---

### Post by strange_brew on 2005-07-27
Asked this question in the N00B forum, but haven't gotten any responses.  I did a lot of searching and I think maybe its better asked here, so I'm cross-posting (hope that's ok).

[http://www.ubuntuforums.org/showthread.php?t=52216](http://www.ubuntuforums.org/showthread.php?t=52216)

---

### Post by majikstreet on 2005-07-27
[QUOTE=strange_brew]Asked this question in the N00B forum, but haven't gotten any responses.  I did a lot of searching and I think maybe its better asked here, so I'm cross-posting (hope that's ok).

[http://www.ubuntuforums.org/showthread.php?t=52216](http://www.ubuntuforums.org/showthread.php?t=52216)[/QUOTE]
 Maybe you want to see [http://us3.samba.org/samba/docs/using_samba/toc.html](http://us3.samba.org/samba/docs/using_samba/toc.html)

I'm not sure though.

Also, is your username inspired by the Cream song "Strange Brew"?

---

### Post by wrtrdood on 2005-07-27
You are correct in that, while it is possible, writing to NTFS partitions from Linux is a risky thing to try.  You are also correct in the belief that you should be able to do this using Samba.  I believe that you will need to allow those directories to be written to from the Windows side when you set up the share.  It might also require some user/permission changes to make it work.  The other part is whether or not you allow writing via the smb.conf.

---

### Post by crispingatiesa on 2005-07-27
I'm not so sure U can write to those using samba. Reason being that samba is just a "translation tool" to allow two different oses to communicate.

When the XP drive make a request to write in the NTFS drives in the Ubuntu box; what samba does is to translate this request in an "inteligible" order for the linux kernel, which will perform the operation if possible, so, bottom line is that you'll need NTFS writting support in your linux box.

It works the other way around because when you copy from a linux box to a windows box the kernel writting in the NTFS drive is the windows kernel

---

### Post by strange_brew on 2005-07-27
Firstly, thanks for your replies - this is my first linux experience and so far its been a good one.  Pretty straightforward stuff from what I can see so far.  Had it installed, connected via VNC and sharing Movie files with my Media Center PC in less than 5 hours, which I didn't think would happen.  So, since the experiment has been a roaring success, I will keep Ubuntu on my server box.  And given crispingatiesa's comments (which is what I was afraid of), I have decided to bite the bullet on the NTFS issue.

Here is the plan...

I have 1 200GB drive that is only 25% full - and I have backups of the movies from that drive on DVD so what I think I will do is reformat it as FAT so both OS's are happy, then copy the contents (200GB) of one of the other NTFS drives to get it empty, reformat that one as FAT, etc...  My other alternative is to pull the 2 drives and do it in XP, but I would rather not as it will tie up my workstation for a loooong time and XP will likely choke on it. 

Does anyone see any issues with trying to copy 200GB of data from an NTFS drive to a FAT drive from Ubuntu? Any recommendations on the fastest way to do this?

[QUOTE=majikstreet]
Also, is your username inspired by the Cream song "Strange Brew"?[/QUOTE]
Actually, no.  By the movie with Rick Moranis and Dave Thomas as "Bob and Doug McKenzie". Classic Canadian humour.

---

### Post by crispingatiesa on 2005-07-27
[QUOTE=strange_brew]Firstly, thanks for your replies - this is my first li
Here is the plan...

I have 1 200GB drive that is only 25% full - and I have backups of the movies from that drive on DVD so what I think I will do is reformat it as FAT so both OS's are happy, then copy the contents (200GB) of one of the other NTFS drives to get it empty, reformat that one as FAT, etc...  My other alternative is to pull the 2 drives and do it in XP, but I would rather not as it will tie up my workstation for a loooong time and XP will likely choke on it. 
[/QUOTE]

I'll advise againts using fat32, firstly because U wont gain anything from using it, you still will have to use samba to communicate your XP box with the server

Secondly because by doing so you will loss speed (fat 32 doesn't allow indexing services)

You'll be better off by using ext3fs because you'll have faster data access, better data protection (no data loss on writing accidents) and better use of the drive space (fat32 tends to take a lot of space for writing the fat table etc, etc...) 
[QUOTE=strange_brew]
Does anyone see any issues with trying to copy 200GB of data from an NTFS drive to a FAT drive from Ubuntu? Any recommendations on the fastest way to do this?

 [/QUOTE]

Dude, 200gig of data  are 200 gig of data whenever you look at it, it will take a lot of time, and from copying in Ubuntu, I don't think that it will be faster than copying from an NTFS to NTFS drive in XP. Anyways, check that you have UDMA enabled in Ubuntu with 

sudo hdparm /dev/hd?

good luck

---

### Post by strange_brew on 2005-07-27
I hear you.  But if I use Ext3, then how can my Media Center PC read the files? All this is going to be is media data storage so I don't want to use a converter for the XP boxes to read the files.  Media Center 2005 is picky enough as it is...

udma is on.

---

### Post by crispingatiesa on 2005-07-27
Based on your post, today  U are using Samba to read the NTFS drives in the Ubuntu server from your media pc. Is that correct?

If yes, then, U will still be doing the same, from the point of view of the XP box the underliying fs in the Ubuntu box is irrelevant (simply it doesnt see it.

For instance is similar to when using a protocol like ftp to transfer files between computers, the underlying fs is irrelevant

---

### Post by strange_brew on 2005-07-27
[QUOTE=crispingatiesa]Based on your post, today  U are using Samba to read the NTFS drives in the Ubuntu server from your media pc. Is that correct?

If yes, then, U will still be doing the same, from the point of view of the XP box the underliying fs in the Ubuntu box is irrelevant (simply it doesnt see it.

For instance is similar to when using a protocol like ftp to transfer files between computers, the underlying fs is irrelevant[/QUOTE]
 AHA! (Light goes on).  The posts I have read refer to a single computer using dual-boot, in which case there is no Samba to act as a translator, correct?  so if my Ubuntu box is running ext3fs, then samba will write to that but windows only sees Samba.

Got it.  Thanks!!

---

### Post by crispingatiesa on 2005-07-27
U got it mack

---

### Post by strange_brew on 2005-07-27
[QUOTE=crispingatiesa]U got it mack[/QUOTE]
 ...in process of converting to ext3fs on the one drive.  Question: is it normal to have 9 or so GB in "lost+found"?  I'm assuming this is some of the remnants of the media files that were there previously.  How do I reclaim this space? (I'm using Qtparted to partition).

***UPDATE***

Did some googling and figured it out - ended up going Reiser as it doesn't need so much space for journaling and this is a media drive so every GB counts!

Thanks again for your help...I'm now in the process of copying everything over <sigh>

---

