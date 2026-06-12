---
title: "Space missing on hard drive, can't be found in xubuntu or windows installer"
date: 2013-10-15
forum: General Help
---

### Post by bachtobach on 2013-10-15
I had Windows 7 on my hard drive and I created a partition with the UbuntuStudio installer to install and try that. 
Then I think I tried to delete the partition in Windows through the Disk Management but something seems to have gone wrong. 

Since then I wiped the drive and installed xubuntu. I chose to format the disk when installing this so I thought everything would be back to a default state, a full empty drive. This isn't the case though, I am missing the 30gb that I partitioned before. 

Gparted isn't recognising the full size of the disk and doesn't see the missing partition. 
The File System section in xubuntu does seem to recognise the proper size of the disk but I it doesn't allow me to put any more data on it than the 'false' size so it seems this extra 30gb is hidden but is actually some form of data.

I ran ```
sudo fdisk -l
``` and this is what I get, I'm not really able to interpret this properly. 

[IMG]http://i.imgur.com/4lCn3o1.png[/IMG]

I tried to reinstall Windows because I thought maybe the partition was a dynamic volume but the Windows installer isn't allowing me to install, it says it needs a disk formatted in NFTS. It also does not recognise the full size of the disk. 

I don't know what else to do, I can completely wipe the drive, I have everything backed up but I don't know where to start.

---

### Post by michaelcranie on 2013-10-15
is the 30 gig not just because the hard disc manufacturer used 1000Mb to a gig instead of 1024 also you have three partitions that uses some space i think.

---

### Post by bachtobach on 2013-10-15
No, I don't think that's the issue. When I hover over the File System icon in the File Manager it says that it is 487gb which is what I would expect.

---

### Post by oldfred on 2013-10-15
Your 465 looks correct.
       1 Gigabyte (GB) = 1,000,000,000 bytes.
1 Gibibyte (GiB) = 1024x1024x1024 = 1,073,741,824 bytes
500/1.073 = 465

Different tools report space different ways, so it can be very confusing.
You also have ext4 reserving space for journal and 5% for superuser (so you may have a chance to boot when drive is full).

 MB vs MiB
[http://en.wikipedia.org/wiki/Binary_prefix](http://en.wikipedia.org/wiki/Binary_prefix)
[http://www.osforge.com/news/001337.html](http://www.osforge.com/news/001337.html)
Then when you format it, the ext4 is journalized so it reserves space for the journal. This improves performance and allows error correction for the cost of a small amount of space. Also reserves space.
[http://blog.flexion.org/index.php/2010/01/07/recovering-reserved-space-ext4/](http://blog.flexion.org/index.php/2010/01/07/recovering-reserved-space-ext4/)
Hard Drive size
[http://en.wikipedia.org/wiki/Gigabyte#Consumer_confusion](http://en.wikipedia.org/wiki/Gigabyte#Consumer_confusion)

Windows does not see Linux partitions. Best to only use Windows tools for Windows and Linux tools for Linux. If installing Windows you have to have a primary partition formatted NTFS with the boot flag or unallocated space with available primary partition(s). Windows 7 will install to one partition if created in advance but default install is with a 100MB (hidden) boot/repair partition and the main install. Main reason for separate Boot is so you can encrypt the main install.

---

### Post by bachtobach on 2013-10-15
Thanks for the reply [**[COLOR=#C61919][B]oldfred**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=852711"), really appreciate any help with this. 
The maths may look correct but I know something is wrong here. My backup folder totals 458gb, this is just data files like music, pictures, videos. I had this on my Windows installation, along with the Windows folder (18gb I think it was) and installed programs (another few gbs). I was running out of space, and only had about 10gb free but it fit on there.  

Now, I installed xubuntu, not really added much more than what comes with it and I can't even fit my backup files on the disk. 

If it really does only have a 465gb capacity then why would the File Manager report it as a 487gb volume?

EDIT: I also have a second drive that I use as a backup. This is also a 500gb drive. This is showing all of my files with 21gb free space (and includes the program files/data from the windows installation). This is showing as 488gb total capacity.

---

### Post by oldfred on 2013-10-15
I do not have Xubuntu, and its file manager. Desktops do their own thing.
What does this show after you mount all partitions.
df -h

I also like gparted's graphical view, so I install it in my working install even though I cannot use it on the mounted partition.

---

### Post by bachtobach on 2013-10-15
That command gives:

[IMG]http://i.imgur.com/6Ky09DN.png[/IMG]

---

### Post by oldfred on 2013-10-15
I do not know LVM, so partition is occupied by the LVM but will not show what is in it. And gparted does not currently work with LVM either. The very newest gparted not yet in Ubuntu may show more, but you need LVM command which I do not know.

---

