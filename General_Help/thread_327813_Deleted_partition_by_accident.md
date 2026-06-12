---
title: "Deleted partition by accident"
date: 2006-12-29
forum: General Help
---

### Post by Flavian on 2006-12-29
Hi guys
I set up edgy on my Dads Laptop today (he said he would try it if it really was that much better than windows ;) )
Anyways, I set it all up and after installing all the packets he needs plus downloading LOADS of data from the inet I wanted to just delete his old NTFS partition and reformat it with FAT32 to share thunderbird mails between the 2 OS.
I went into windows and there I deleted the NTFS partition, which was shown with a green boarder around it. The green boarder "connected" another partition to the NTFS one, which fileformat windows didn't know. 
I didn't think, so I simply deleted the partition (I didn't format it yet) which magically merged the other one into it as well... :( 
I knew that I broke Ubuntu at that point :(

I rebooted and GRUB wasn't there anymore.
Trying to reinstall it doesn't work, I can access the root system via the "alternate CD" it's at /dev/hda2 BUT reinstalling GRUB gives me error code 20!
What can I do so that I not loose all the data and the install again.
Plus get a wonderful FAT32 drive that I can USE afterwards?

Thanks in advance
Flo

---

### Post by Flavian on 2006-12-29
Okay!
Wow, here's an update ;)
*lol* sweet, see that's one thing why I LOVE Linux so much more than freaking windows...
If you brake something, you a) got a LARGE and friendly supportive community behind you and b) are not limited to any system restrictions... the command line just WORKS :)

So I fixed it.
The way I solved it was, to put the CD in again and instead of using "rescue a broken system" I used "install" again... there I could set the root file system in the partitioning manager again. But GRUB wouldnt install in the master boot record so I just installed it on (hd0,1) which is the root partition.
BUT I was anxcious to delete or overwrite any data, so when the partitioning program said: "There isn't any SWAP partition..." I just continued without one.
Question is now: Can I create one now, even if it's all fixed?

My guess is that the partitions who merged where a) the NTFS part. and b) the SWAP Part.
That would make sense...
So the question is now: How do I get my desired FAT32 part. plus a working SWAP Part. without killling any other existing partitions again ?

Thanks in advance!
Flo

---

### Post by bernied on 2006-12-29
Can you show the output to 
```
sudo fdisk -l
```this is a list of your partitions

If you do create/destroy/merge partitions do it while they are not mounted - ie you can't do this from your installed system, you must do it from live-cd.
EDIT: you can do the fdisk -l - it doesn't change anything, just lists - it's editing that you can't do on mounted partitions

---

### Post by bernied on 2006-12-29
Also, it might be useful to see your /boot/grub/menu.lst file
```
cat /boot/grub/menu.lst
```

---

### Post by EZ-man on 2006-12-29
Have you looked into the Disks Manager Display Box:

System/Administration/Disks.

must be root

EZ  :D

---

### Post by Flavian on 2006-12-29
Thanks buddies!
Works all fine now :)

---

