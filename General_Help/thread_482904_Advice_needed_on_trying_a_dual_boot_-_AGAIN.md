---
title: "Advice needed on trying a dual boot - AGAIN"
date: 2007-06-24
forum: General Help
---

### Post by Cloudedbrains on 2007-06-24
Ok Ive had a dual boot (via Wubi) with Ubuntu and XP before but then went daft and went Ubuntu alone but due to my diabetes meter not being able to be used in Ubuntu I went back to XP and decided to order the Ubuntu and Kubuntu discs so I had them if I braved it again !!

Well I am looking to dual-boot again but wanted some advice first if thats ok !!

My HDD is 250gigs - partioned at present as:
100gigs for windows and proggies
and the rest (shows as 135gig) is my documents

Could I leave my windows partion alone and just format the other partion for Ubuntu/Kubuntu but making an area that can be used by both ubuntu and XP for "My Documents" etc that they both can write or read !!
If I can just  partition this one drive what sizes and format would be best !!

Or would a total reinstall and format of both XP and Ubuntu/Kubuntu be the only way !!
I want to use the disc this time and not Wubi so any advice gratefully received !!

Id rather not have to reinstall the windows side again so is it possible just to do it via the partion I have currently set as "My Documents" !!

---

### Post by mattg89 on 2007-06-24
If you defragment your my documents partition, then you can create a new partition to install ubuntu to. Depending on what you want it for, minimum is probably 20Gb. You can now read from NTFS with no problems (writing is a bit difficult). If you want to read/write the safest route is to reformat to FAT32, though I'm not fully updated on ubuntu's ability to write to NTFS.

---

### Post by Cloudedbrains on 2007-06-24
I know when I tried the Wubi dual boot I could only read the NTFS so I defo need it to read and write so if I wiped the whole My Documents partition (have everything backed up anyway) and formatted it to "Fat" would Ubuntu or Kubuntu install easy enough from the disc ??

---

### Post by eggdeng on 2007-06-24
> Could I leave my windows partion alone and just format the other partion for Ubuntu/Kubuntu but making an area that can be used by both ubuntu and XP for "My Documents" etc that they both can write or read !!
If I can just partition this one drive what sizes and format would be best !!
I would create two partitions on the 135gig. Probably a good idea to download the gparted live CD and resize the 135gig down to whatever space you think you are going to need for your files before you start installing. Leave the rest as free space and when you install, tell the installer to create the default / and swap partitions on that space. If your documents partition is formatted as FAT, you should have no problems reading and / or writing. If it were NTFS you would have to install a utility so that ubuntu would be able to write to it. Make sure to back up everything first just in case.

---

### Post by Cloudedbrains on 2007-06-24
Ive backed my documents up as it was NTFS and have the feeling I need to format the whole of that partition - will the Kubuntu or Ubuntu CD be able to do that ??

I wanted XP and whichever version I go for to use the same partion to save documents and music to etc etc !!
Yet to have their own partitions for themelves and proggies !!

Can it be done how I am thinking or is there another way !!

---

### Post by kayvortex on 2007-06-24
Right, let me see if I have this right. You want an XP partition, which you don't want to reformat; a new K/Ubuntu partition for applications, and a last partition for documents etc. that you want read/writeable by both OSes? If that's correct, it's perfectly possible. I have set something like this up for my dad from a single NTFS partition that had XP on it. The good news is that no formatting is necessarily required.

First, defrag your "documents partition" (several times) to ensure that files aren't fragmented all over the partition.

Then, if you boot from the K/Ubuntu installation CD, and double-click the install icon that will appear when k/Ubuntu is booted (to begin the installation proper), you will eventually get to a bit asking about partitioning your disks (choose to manually partition). Here, you can choose to resize your NTFS "documents partition". In the space that this will free, you can then add your root and swap partitions.

With your resized NTFS "documents partition" you can read/write it using ntfs-3g. In Feisty, there is no installation required: see [here]("http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html").

If you choose to go through the FAT route, you will need to back-up your files in the "documents partition", format that partition as FAT32 in addition to resizing it, and then copy your files back to it. By the way, backing-up your files is a good idea whatever you do.

As for partition sizes, I keep all my music, documents etc. on a separate NTFS partition which leaves my Ubuntu partition free to hold just applications. I have a fair amount of stuff on the Ubuntu partition and it's currently at 4 Gig. However, bear in mind that some big files sometimes get written to it before being moved on to the "documents partition". I'd recommend a Ubuntu partition size of 10 Gig (at least), and leave the rest for the "documents partition".

---

### Post by eggdeng on 2007-06-24
I don't see why you should have any difficulties with this. Again I would recommend that you download the gparted liveCD from
[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828]("http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828") and use this to partion before you install. It's a versatile & powerful partitioning tool with a user-friendly interface. It's actually the same tool the installer uses but without the constraints of being in the middle of an install.
Now that everything is backed up, you might just as well eliminate the 135GB partition, create a new smaller FAT partition for your docs, say 105GB and leave the other 20GB as free space for the ubuntu install. When you start installing you will be offered the possibility of installing to the largest available free space so just go with that and the default options. Ubuntu should automatically detect and mount the available partions, and they should be visible & read/writeable from both OS's.

---

### Post by Cloudedbrains on 2007-06-24
Ive backed up my documents so can stick them back once its done.

So I use the gparted CD to wipe the partition and resize it.
Then I just stick in the Ubuntu or Kubuntu disc and let it install.

Will it pick the sizes for the home/switch  stuff or do I need to allocate them.

---

### Post by mattg89 on 2007-06-24
You can choose if you want, or it can automatically allocate them. If you're not sure, it doesn't make any changes until you click onto the next step.

---

### Post by strabes on 2007-06-24
DONT use fat32 for your data partition. Use ext3 and then install the driver from fs-driver.org in windows to read/write from it. When I was dual booting, my partitions were set up like this:

1) Windows ntfs
2) Ubuntu ext3
3) Swap
4) Data ext3

---

### Post by Cloudedbrains on 2007-06-24
THanks

---

### Post by Cloudedbrains on 2007-06-25
A friend who is a whiz with pc's has got the diabetes software I need to download my meter too, to work under wine on Ubuntu with a bit of tweaking :D

This means I have no reason not to go back to JUST Ubuntu :p

But OK I know Ive asked this before but bear with me - due to illness I cant remember what was advised :(

How on earth do I partition the 250gig drive I have for Ubuntu or Kubuntu alone :(

---

